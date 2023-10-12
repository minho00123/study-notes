# 생성자 함수(Constructor)
---
## 📌 Summary
> `new` 연산자와 함께 호출하여 객체(인스턴스)를 생성하는 함수
> 	- 인스턴스(instance): 생성자 함수에 의해 생성된 객체
## 📌 Description
### ◉ 생성자 함수의 역할
#### 1. 템플릿(클래스)처럼 사용하여 프로퍼티 구조가 동일한 여러 개의 인스턴스를 생성한다.
- 일반 함수와 동일한 방식으로 생성자 함수를 정의하고, `new` 연산자와 함께 호출하여 생성자 함수를 생성한다.
	- `new`  연산자 없이 호출하면 일반 함수로 동작한다.
	- 자바스크립트는 `Object`, `String`, `Number`, `Boolean`, `Function`, `Array`, `Date`, `RegExp`, `Promise` 등의 빌트인(built-in) 생성자 함수를 제공한다.
```js
function User(userId) {
    this.id = userId;
    this.name = 'Mino';
    this.greet = function () {
        return `Hi! I'm ${this.name}!`;
    }
}

const user1 = new User(1);

console.log(user1.greet()); // Hi! I'm Mino!

const user2 = User(2);

// 일반 함수로 호출된 User는 반환문이 없어 암묵적으로 undefined를 반환한다.
console.log(user2); // undefined

// user2가 일반 함수로 호출되었기 때문에 User 내의 this는 전역 객체를 가리킨다.
console.log(name); // Mino
```
#### 2. 인스턴스를 초기화한다.
- 인스턴스 초기화는 인스턴스에 프로퍼티를 추가하거나 초기값을 할당하는 것을 말한다.
- 생성자 함수가 인스턴스를 생성하는 것은 필수이지만, 생성된 인스턴스를 초기화하는 것은 선택이다.
```js
function User(userId) {
	// 인스턴스 초기화
    this.id = userId;
    this.name = 'Mino';
    this.greet = function () {
        return `Hi! I'm ${this.name}!`;
    }
}

// 인스턴스 생성
const user1 = new User(1);

```
### ◉ Object 생성자 함수 vs. 객체 리터럴
- `new` 연산자와 함께 `Object` 생성자 함수를 호출하면 빈 객체를 생성하여 반환한다
	- 이후에 프로퍼티 또는 메서드를 추가하여 객체를 완성할 수 있다.
```js
const user = new Object();

user.id = 1;
user.name = 'Mino';
user.greet = function () {
	console.log(`Hi! I'm ${this.name}!`);
};

console.log(user); // {userId: 1, name: 'Mino', greet: ƒ}
user.greet(); // Hi! I'm Mino!
```
- 이와 반대로 객체 리터럴을 생성 방식은 직관적이고 간편하다.
	- 하지만 객체 리터럴은 단 하나의 객체만을 생성하기 때문에 같은 프로퍼티를 가진 객체를 여러 개 생성해야 하는 경우 비효율적이다.
```js
const user1 = {
    id: 1,
    name: 'Mino',
    greet() {
        return `Hi! I'm ${this.name}!`;
    }
};

console.log(user1.greet()); // Hi! I'm Mino!

const user2 = {
    id: 2,
    name: 'YJ',
    greet() {
        return `Hi! I'm ${this.name}!`;
    }
};

console.log(user2.greet()); // Hi! I'm YJ!
```
### ◉ 생성자 함수의 인스턴스 생성 과정
- `new` 연산자와 함께 생성자 함수를 호출하면 자바스크립트 엔진은 암묵적으로 인스턴스를 생성하고 반환한다.
- 인스턴스 생성 과정은 다음과 같다:
#### 1. 인스턴스 생성과 this 바인딩
- 런타임 이전에 암묵적으로 인스턴스가 생성되고 `this`에 바인딩된다.
	- 따라서 생성자 함수 내부의 `this`는 생성할 인스턴스를 가리키게 된다.
> 💡 **바인딩(name binding)**
> • 식별자와 값을 연결하는 과정을 의미한다.
		Ex. 변수 선언: 변수 이름(식별자)과 확보된 메모리 공간의 주소를 바인딩하는 것
			  `this` 바인딩: `this`와 `this`가 가리킬 객체를 바인딩하는 것
#### 2. 인스턴스 초기화
- 인스턴스에 프로퍼티 또는 메서드를 추가하고, 생성자 함수가 인수로 전달받은 초기값을 인스턴스 프로퍼티에 할당하여 초기화하거나 고정값을 할당한다. → 이는 개발자가 기술한다.
#### 3. 인스턴스 반환
- 완성된 인스턴스가 바인딩된 `this`를 암묵적으로 반환된다.
	- `this`가 아닌 다른 객체를 `return` 문에 명시적으로 반환하면 그 객체가 반환된다.
		- `this`가 아닌 다른 값을 반환하는 것은 생성자 함수의 기본 동작을 훼손하는 것이기 때문에 생성자 함수 내부에서 `return` 문은 반드시 생략해야 한다.
	- 명시적으로 원시 값을 반환하면 암묵적으로 `this`가 반환된다.
```js
function User(userId) {
	// 1. 암묵적으로 인스턴스가 생성되고 this에 바인딩된다.
    console.log(this); // User {}

	// 2. this에 바인딩되어 있는 인스턴스를 초기화한다.
    this.id = userId;
    this.greet = function () {
        return `Hi! I'm ${this.name}!`;
    }

	// 3. 완성된 인스턴스가 바인딩된 this가 암묵적으로 반환된다.
	// 3-1. 명시적으로 객체를 반환하면 암묵적인 this 반환이 무시된다.
	// return {};
	// 3-2. 명시적으로 원시 값을 반환하면 원시 값 반환은 무시되고 암묵적으로 this가 반환된다.
	// return 100;
}

const user1 = new User(1);
console.log(user1); // 3. User {id: 1, greet: ƒ}
// console.log(circle); // 3-1. User {}
// console.log(circle); // 3-2. User {id: 1, greet: ƒ}
```
### ◉ constructor vs. non-constructor
- 자바스크립트 엔진은 함수 정의 방식에 따라 함수 객체를 constructor와 non-constructor로 구분한다.
- 자바스크립트에서 함수는 객체이기 때문에 일반 객체가 가지는 내부 슬롯과 내부 메서드를 모두 가지고 있다.
	- 또한, 함수 객체는 함수로서 동작하기 위해 `[[Environment]]`, `[[FormalParameters]]` 등의 내부 슬롯과 `[[Call]]`, `[[Construct]]` 같은 내부 메서드를 추가로 가지고 있다.
- 모든 함수는 호출할 수 있기 때문에 내부 메서드 `[[Call]]`(callable)을 가지고 있다.
- 내부 메서드 `[[Construct]]`를 갖는 함수 객체를 constructor, `[[Construct]]`를 갖지 않는 함수 객체를 non-constructor라고 부른다.
	- constructor는 생성자 함수로서 호출할 수 있는 함수다.; `new` 연산자와 함께 생성자 함수로서 호출될 수 있는 함수이기도 하다. Ex. 함수 선언문, 함수 표현식, 클래스
	- non-constructor는 객체를 생성자 함수로서 호출할 수 없는 함수다.
	   Ex. 메서드(ES6 메서드 축약 표현), 화살표함수
- 함수를 일반 함수로서 호출하면 함수 객체의 내부 메서드 `[[Call]]`이 호출되고 `new` 연산자와 함께 생성자 함수로서 호출하면 내부 메서드 `[[Construct]]`가 호출된다.
- 주의할 것은 생성자 함수로서 호출될 것을 기대하고 정의하지 않은 일반 함수(callable이면서 constructor)에 `new` 연산자를 붙여 호출하면 생성자 함수처럼 동작할 수 있다는 것이다.

```js
// 일반 함수 정의: 함수 선언문, 함수 표현식
function foo() {}
const bar = function () {};
// 프로퍼티 x의 값으로 할당된 것은 일반 함수로 정의된 함수다. 이는 메서드로 인정하지 않는다.
const baz = {
	x: function () {}
};

// 일반 함수로 정의된 함수만이 constructor다.
new foo(); // foo {}
new bar(); // bar {}
new baz.x(); // x {}

// 화살표 함수 정의
const arrow = () => {};

new arrow(); // TypeError: arrow is not a constructor

// 메서드 정의: ES6의 메서드 축약 표현만 메서드로 인정한다.
const obj = {
	x() {}
};

new obj.x(); // TypeError: obj.x is not a constructor
```
### ◉ new.target
- ES6에서 도입되었으며, `new` 연산자와 함께 생성자 함수로서 호출되었는지 확인할 수 있다.
	- `new` 연산자와 함께 생성자 함수에 의해 생성된 객체(인스턴스)는 프로토타입에 의해 생성자 함수와 연결된다. 이를 이용해 `new` 연산자와 함께 호출되었는지 확인할 수 있다.
	- `new` 연산자와 함께 생성자 함수로서 호출되면 함수 내부의 `new.target`은 함수 자신을 가리킨다.
	- `new` 연산자없이 일반 함수로서 호출된 함수 내부의 `new.target`은 `undefined`다.
- `new.target`은 `this`와 유사하게 constructor인 모든 함수 내부에서 암묵적인 지역 변수와 같이 사용되며 메타 프로퍼티라고 부른다.
```js
function User(userId) {
	// 이 함수가 new 연산자와 함께 호출되지 않았다면 new.target은 undefined다.
	if (!new.target) {
		// new 연산자와 함께 생성자 함수를 재귀 호출하여 생성된 인스턴스를 반환한다.
		return new User(userId);
	}

    this.id = userId;
    this.greet = function () {
        return `Hi! I'm ${this.name}!`;
    }
}

// new 연산자 없이 생성자 함수를 호출하여도 new.target을 통해 생성자 함수로서 호출된다.
const user1 = User(1);
console.log(user.greet); // undefined
```

- 대부분의 빌트인 생성자 함수는 `new` 연산자와 함께 호출되었는지를 확인한 후 적절한 값을 반환한다.
	Ex. `Object`와 `Function` 생성자 함수는 `new` 연산자 없이 호출해도 `new` 연산자와 함께 호출했을 때와 동일하게 동작한다.
```js
let obj = new Object();
console.log(obj); // {}

obj = Object();
console.log(obj); // {}

let f = new Function('x', 'return x ** x');
console.log(f); // ƒ anonymous(x) { return x ** x }

f = Function('x', 'return x ** x');
console.log(f); // ƒ anonymous(x) { return x ** x }
```
- 하지만 `String`, `Number`, `Boolean` 생성자 함수는 `new` 연산자와 함께 호출했을 때 `String`, `Number`, `Boolean` `객체를` 생성하여 반환하지만 `new` 연산자 없이 호출하면 문자열, 숫자, 불리언 값을 반환한다. 이를 통해 데이터 타입을 변환하기도 한다.
```js
const str = String(123);
console.log(str, typeof str); // 123 string

const num = Number('123');
console.log(num, typeof num); // 123 number

const bool = Boolean('true');
console.log(bool, typeof bool); // true boolean
```
## 📌 Reference
- "모던 자바스크립트 Deep Dive" by 이웅모, p.234-248