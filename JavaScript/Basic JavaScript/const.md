# const
---
## 📌 Summary
>  단 한번만 할당할 수 있는 변수
## 📌 Description
- `const`는 상수를 뜻하는 'constant'에 의미를 가진다.
- `let` 키워드와 대부분 동일하다.
	- 블록 레벨 스코프를 가지고, 변수 호이스팅이 발생하지 않는 것처럼 동작한다.
### ◉ 특징
#### 1. 선언과 초기화가 반드시 동시에 이루어져야 한다.
- 동시에 이뤄지지 않으면 문법 에러가 발생한다.
```js
const foo = 1;

const foo; // SyntaxError: Missing initializer in const declaration
```
#### 2. 재할당 금지
```js
const foo = 1;
foo = 2; // TypeError: Assignment to constant variable
```
#### 3. 상수
- `const` 키워드로 선언한 변수에 원시 값을 할당하면 변수 값을 변경할 수 없기 때문에, 이러한 특징을 이용하여 상수를 표현하는 데 사용한다.
- 상수는 **재할당이 금지된 변수** 를 말한다.
	- 상수도 값을 저장하기 위한 메모리 공간이 필요하기 때문에 변수라고 할 수 있다.
```js
const TAX_RATE = 0.1;

let preTaxPrice = 100;

let afterTaxPrice = preTaxPrice + (preTaxPrice * TAX_RATE);

console.log(afterTaxPrice); // 110
```
#### 4. 객체를 할당한 경우에는 값을 변경할 수 있다.
- 객체는 변경 가능한 값이기 때문에 재할당 없이도 값을 변경할 수 있다.
```js
const person = {
	name: 'Lee'
};

person.name = 'Kim';

console.log(person); // {name: "Kim"}
```
## 📌 Reference
- "모던 자바스크립트 Deep Dive" by 이웅모, p.215-217