# 일급 객체(First-class Object)
---
## 📌 Summary
> 일반적인 객체가 사용할 수 있는 모든 기능을 가진 객체를 말한다.
## 📌 Description
### ◉ 일급 객체 만족 조건
- 다음 조건을 만족하는 객체를 일급 객체라 한다:
#### 1. 변수나 자료구조(객체, 배열 등)에 저장할 수 있다.
```js
const hello = function() {
	console.log("Hello, World!")
}
```
#### 2. 함수의 매개변수(Parameter)로 전달할 수 있다.
```js
const hello = function() {
	console.log("Hello, World!");
}

function print(func) {
	func();
}

print(hello);
```
#### 3. 함수의 반환값으로 사용할 수 있다.
```js
const hello = function() {
	console.log("Hello, World!");
	return function() {
		console.log("Hello, World2!");
	}
}

const hello2 = hello();
hello2();
```
### ◉ 자바스크립트 함수
- 자바스크립트의 함수는 일급 객체의 조건을 모두 만족하기 때문에 일급 객체다.
- 객체는 값이므로 함수는 값과 동일하게 취급할 수 있다.
	- 함수는 값을 사용할 수 있는 곳(변수 할당문, 객체의 프로퍼티, 배열의 요소, 함수 호출의 인수, 함수 반환문)이라면 어디서든지 리터럴로 정의할 수 있으며 런타임에 함수 객체로 평가된다.
- 일급 객체로서 함수가 가지는 가장 큰 특징은 일반 객체와 같이 함수의 매개변수에 전달할 수 있으며, 함수의 반환값으로 사용할 수도 있다는 것이다. 
	- 이는 함수형 프로그래밍을 가능케 하는 자바스크립트의 장점 중 하나다.
### ◉ 함수 객체의 프로퍼티
- 함수는 객체다. 따라서 함수도 프로퍼티를 가질 수 있다.
- `arguments`, `caller`, `length`, `name`, `prototype` 프로퍼티는 함수 객체만 가지는 고유한 프로퍼티다.
```js
function square(number) {
	return number * number;
}

console.log(Object.getOwnPropertyDescriptors(square));
/*
{
	length: {value: 1, writable: false, enumerable: false, configurable: true},
	name: {value: "square", writable: false, enumerable: false, configurable: true},
	arguments: {value: null, writable: false, enumerable: false, configurable: false},
	caller: {value: null, writable: false, enumerable: false, configurable: false},
	prototype: {value: {...}, writable: true, enumerable: false, configurable: false},
}
*/

// __proto__는 square 함수의 프로퍼티가 아니다.
console.log(Object.getOwnPropertyDescriptor(square, '__proto__')); // undefined

// __proto__는 Object.prototype 객체의 접근자 프로퍼티다.
// square 함수는 Object.prototype 객체로부터 __proto__ 접근자 프로퍼티를 상속받는다.
console.log(Object.getOwnPropertyDescriptor(Object.prototype, '__proto__'));
// {get: ƒ, set: ƒ, enumerable: false, configurable: true}
```
#### ▪︎ arguments 프로퍼티
- 함수 호출시 전달된 인수(argument)들의 정보를 담고있는 유사 배열 객체다.
	- `arguments` 객체는 프로퍼티 키에는 인수의 순서를, 프로퍼티 값은 인수를 가진다.
- 함수 내부에서 지역 변수처럼 사용되지만, 함수 외부에서는 참조할 수 없다.
- 함수 객체의 `Function.arguments` 프로퍼티는 ES3부터 표준에서 폐지되었다. 따라서 사용을 권장하지 않는다.
	- 함수 내부에서 지역 변수처럼 사용할 수 있는 `arguments` 객체를 사용하는 것이 좋다.
- `arguments` 객체의 `callee` 프로퍼티는 호출되어 `arguments` 객체를 생성한 함수, 즉 자신을 가리키고 `arguments` 객체의 `length` 프로퍼티는 인수의 개수를 가리킨다.
- `arguments` 객체는 매개변수 개수를 확정할 수 없는 가변 인자 함수를 구현할 때 유용하다.
```js
function sum() {
	let res = 0;

	for (let i = 0; i < arguments.length; i++) {
		res += arguments[i];
	}

	return res;
}

console.log(sum());        // 0
console.log(sum(1, 2));    // 3
console.log(sum(1, 2, 3)); // 6
```
#### ▪︎ caller 프로퍼티
- `caller` 프로퍼티는 ECMAScipt 사양에 포함되지 않은 비표준 프로퍼티다.
	- 이후 표준화될 예정도 없는 프로퍼티이므로 사용하지 말고 참고로만 알아두자.
- 함수 객체의 `caller` 프로퍼티는 함수 자신을 호출한 함수를 가리킨다.
```js
function foo(func) {
	return func();
}

function bar() {
	return 'caller : ' + bar.caller;
}

console.log(foo(bar)); // caller : function foo(func) {...}
console.log(bar());    // caller : null
```
- 함수 호출 `foo(bar)`의 경우 `bar` 함수를 `foo` 함수 내에서 호출했다. 이때 `bar` 함수의 `caller` 프로퍼티는 `bar` 함수를 호출한 `foo` 함수를 가리킨다.
- 함수 호출 `bar()`의 경우 `bar` 함수를 호출한 함수는 없다. 따라서 `caller` 프로퍼티는 `null`을 가리킨다.
- 위 결과는 브라우저에서 실행한 결과다. 만약 Node.js 환경에서 위 예제를 실행하면 다른 결과가 나온다. 이는 모듈과 관계가 있다.
#### ▪︎ length 프로퍼티
- 함수 객체의 `length` 프로퍼티는 함수를 정의할 때 선언한 매개변수의 개수를 가리킨다.
```js
function foo() {}
console.log(foo.length); // 0

function bar(x) {
	return x;
}
console.log(bar.length); // 1

function baz(x, y) {
	return x + y;
}
console.log(baz.length); // 2
```
- `arguments` 객체의 `length` 프로퍼티와 함수 객체의 `length` 프로퍼티의 값은 다를 수 있으므로 주의해야 한다.
	- `arguments` 객체의 `length` 프로퍼티는 인자(argument)의 개수를 가리키고, 함수 객체의 `length` 프로퍼티는 매개변수(parameter)의 개수를 가리킨다.
#### ▪︎ name 프로퍼티
- 함수 객체의 `name` 프로퍼티는 함수 이름을 나타낸다.
- `name` 프로퍼티는 ES6 이전까지는 비표준이었다가 ES6에서 정식 표준이 되었다.
- 익명 함수 표현식의 경우 ES6에서는 함수 객체를 가리키는 식별자를 값으로 갖는다.
	- ES5에서는 빈 문자열을 값으로 갖는다.
```js
// 기명 함수 표현식
var namedFunc = function foo() {};
console.log(namedFunc.name); // foo

// 익명 함수 표현식
var anonymousFunc = function () {};
// ES5: 빈 문자열을 값으로 갖는다.
// ES6: 함수 객체를 가리키는 변수 이름을 값으로 갖는다.
console.log(anonymousFunc.name); // anonymousFunc

// 함수 선언문(Function declaration)
function bar() {}
console.log(bar.name); // bar
```
- 함수를 호출할 때 함수 이름이 아닌 함수 객체를 가리키는 식별자로 호출한다.
#### ▪︎ \_\_proto\_\_ 접근자 프로퍼티
- `__proto__` 프로퍼티는 `[[Prototype]]` 내부 슬롯이 가리키는 프로토타입 객체에 접근하기 위해 사용하는 접근자 프로퍼티다.
- `[[Prototype]]` 내부 슬롯에는 직접 접근할 수 없으며 `__proto__` 접근자 프로퍼티를 통해 간접적으로 프로토타입 객체에 접근할 수 있다.
```js
const obj = { a: 1 };

// 객체 리터럴 방식으로 생성한 객체의 프로토타입 객체는 Object.prototype이다.
console.log(obj.__proto__ === Object.prototype); // true

// 객체 리터럴 방식으로 생성한 객체는 프로토타입 객체인 Object.prototype의 프로퍼티를 상속받는다.
// hasOwnProperty 메서드는 Object.prototype의 메서드다.
console.log(obj.hasOwnProperty('a'));         // true
console.log(obj.hasOwnProperty('__proto__')); // false
```
#### ▪︎ prototype 프로퍼티
- `prototype` 프로퍼티는 생성자 함수로 호출할 수 있는 함수 객체, 즉 constructor만이 소유하는 프로퍼티다.
- 일반 객체와 생성자 함수로 호출할 수 없는 non-constructor에는 `prototype` 프로퍼티가 없다.
```js
// 함수 객체는 prototype 프로퍼티를 소유한다.
(function () {}).hasOwnProperty('prototype'); // true

// 일반 객체는 prototype 프로퍼티를 소유하지 않는다.
({}).hasOwnProperty('prototype'); // false
```
- `prototype` 프로퍼티는 함수가 객체를 생성하는 생성자 함수로 호출될 때 생성자 함수가 생성할 인스턴스의 프로토타입 객체를 가리킨다.
## 📌 Reference
- "모던 자바스크립트 Deep Dive" by 이웅모, p.249-258