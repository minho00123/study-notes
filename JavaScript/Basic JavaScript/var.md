# var
---
## 📌 Summary
> 변수를 선언할 때 사용하는 키워드 중 하나
## 📌 Description
- 변수를 뜻하는 "variable"의 약어이다.
- `var` 키워드를 사용한 변수 선언은 선언 단계와 초기화 단계가 동시에 진행된다.
- ES5까지 변수를 선언할 수 있는 유일한 방법이었다.
### ◉ 특징
#### 1. 변수 중복 선언 허용
- 초기화 있는 문은 자바스크립트 엔진에 의해 `var` 키워드가 없는 것처럼 동작하고 초기화문이 없는 변수 선언문이 무시된다. 이때 에러는 발생하지 않는다.
```js
var foo = 1;
var bar = 1;

var foo = 3;
var bar;

console.log(foo); // 3;
console.log(bar); // 1;
```
#### 2. 함수 레벨 스코프
- 함수의 코드 블록만을 지역 스코프로 인정한다.
```js
var foo = 1;

if (true) {
	var foo = 2;
}

console.log(foo); // 2
```
- 함수 이외의 코드 블록(반복문, 조건문 등)에서는 전역 변수가 된다.
```js
var i = 1;

for (var i = 0; i < 5; i++) {
	console.log(i); // 0 1 2 3 4
}

console.log(i); // 5
```
#### 3. 변수 호이스팅
- 변수 선언문이 코드의 최상위에 끌어 올려진 것처럼 동작하는 특징
	- 선언문 이전에 변수를 참조해도 에러가 나지 않는다.
	- 할당문 이전에 변수를 참조하면 언제나 `undefined`를 반환한다.
```js
console.log(foo); // undefined

foo = 1;

console.log(foo); // 1

var foo;
```
#### 4. 전역변수를 선언할 때 전역 객체의 프로퍼티가 된다.
```js
var foo = 1;

console.log(foo === window.foo) // true
```
## 📌 Reference
- "모던 자바스크립트 Deep Dive" by 이웅모, p.208-210