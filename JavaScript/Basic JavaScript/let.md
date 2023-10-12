# let
---
## 📌 Summary
> 변수를 선언하는 키워드 중 하나
## 📌 Description
- `let`은 영어 단어에 뜻인 '허용/허락하다'를 의미한다.
	- 따라서 `let`에 선언한 변수 이름을 할당한 값으로 허용/허락한다는 의미를 가진다.
- "선언 단계"와 "초기화 단계"가 분리되어 진행된다.
### ◉ 특징
#### 1. 변수 중복 선언이 불가능하다.
- 이름이 같은 변수를 중복 선언하면 문법 에러(SyntaxError)가 발생한다.
```js
let foo = 1;

let foo = 2;  // SyntaxError
```
#### 2. 블록 레벨 스코프
- 모든 코드 블록을 지역 스코프로 인정한다.
```js
let foo = 1;

{ 
	let foo = 2;
	let bar = 3;
}

console.log(foo); // 1
console.log(bar); // ReferenceError: bar is not defined
```
#### 3. 변수 호이스팅이 발생하지 않는 것처럼 동작한다.
- `let` 키워드로 선언한 변수를 변수 선언문 이전에 참조하면 참조 에러(ReferenceError)가 발생한다.
- 런타임 이전에 자바스크립트 엔진에 의해 암묵적으로 선언 단계가 먼저 실행되지만 초기화 단계는 변수 선언문이 도달했을 때 실행된다.
- 스코프의 시작 지점부터 초기화 단계 시작 지점(변수 선언문)까지 변수를 참조할 수 없다.
	- 이 구간은 **일시적 사작지대(Temporal Dead Zone; TDZ)** 라고 부른다.
```js
console.log(foo) // ReferenceError: foo is not defined
let foo;
```
#### 4. 전역 객체의 프로퍼티가 아니다.
- `window.foo`와 같이 접근할 수 없다.
```js
let foo = 1;

console.log(window.foo); // undefined
console.log(foo);        // 1
```
## 📌 Reference
- "모던 자바스크립트 Deep Dive" by 이웅모, p.210-215