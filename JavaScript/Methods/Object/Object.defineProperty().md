# Object.defineProperty()
## 📌 Summary
> 새로운 프로퍼티를 정의하거 기존 프로퍼티를 수정하여 객체를 반환한다.
## 📌 Syntax
```js
Object.defineProperty(obj, prop, descriptor)
```
### ◉ Parameter
#### ▪︎ obj
- 프로퍼티를 정의하기 위한 객체
#### ▪︎ prop
- 새롭게 정의하거나 기존의 값을 수정할 프로퍼티의 키를 지정하는 문자열 또는 Symbol
#### ▪︎ descriptor
- 프로퍼티 디스크립터 객체
### ◉ Return Value
- 새로운 프로퍼티가 추가된, 또는 수정된 객체
## 📌 Description
- 새로운 프로퍼티를 추가하여 프로퍼티 어트리뷰트를 명시적으로 정의하거나, 기존 프로퍼티의 프로퍼티 어트리뷰트를 재정의한다.
- `Object.defineProperty` 메서드로 프로퍼티를 정의할 때 프로퍼티 디스크립터 객체의 프로퍼티를 일부 생략할 수 있다. 프로퍼티 디스크립터 객체에서 생략된 어트리뷰트는 다음과 같이 기본값이 적용된다.

| 프로퍼티 디스크립터 객체의 프로퍼티 | 대응하는 프로퍼티 어트리뷰트 | 생략했을 때의 기본값 |
| ----------------------------------- | ---------------------------- | -------------------- |
| value                               | `[[Value]]`                  | `undefined`          |
| get                                 | `[[Get]]`                    | `undefined`          |
| set                                 | `[[Set]]`                    | `undefined`          |
| writable                            | `[[Writable]]`               | `false`              |
| enumerable                          | `[[Enumerable]]`             | `false`              |
| configurable                        | `[[Configurable]]`           | `false`                     |

## 📌 Examples
```js
const person = {};

// 데이터 프로퍼티 정의
Object.defineProperty(person, 'firstName', {
	value: 'Ungmo',
	writable: true,
	enumerable: true,
	configurable: true
});

Object.defineProperty(person, 'lastName', {
	value: 'Lee'
});

let descriptor = Object.getOwnPropertyDescriptor(person, 'firstName');
console.log('firstName', descriptor);
// firstName {value: "Ungmo", writable: true, enumerable: true, configurable: true}

// 디스크립터 객체의 프로퍼티를 누락시키면 undefined, false가 기본값이다.
descriptor = Object.getOwnPropertyDescriptor(person, 'lastName');
console.log('lastName', descriptor);
// lastName {value: "Lee", writable: false, enumerable: false, configurable: false}

// [[Enumerable]]의 값이 false인 경우
// 해당 프로퍼티는 for...in 문이나 Object.keys 등으로 열거할 수 없다.
console.log(Object.keys(person)); // ["firstName"]

// [[Writable]]의 값이 false인 경우 해당 프로퍼티의 [[Value]]의 값을 변경할 수 없다.
// false 값을 변경하면 에러는 발생하지 않고 무시된다.
person.lastName = 'Kim';

// [[Configurable]]의 값이 false인 경우 해당 프로퍼티를 삭제할 수 없다.
// false인 값을 삭제하면 에러는 발생하지 않고 무시된다.
delete person.lastName;

// [[Configurable]]의 값이 false인 경우 해당 프로퍼티를 재정의할 수 없다.
// Object.defineProperty(person, 'lastName', { enumerable: true });
// Uncaugth TypeError: Cannot readefine property: lastName

descriptor = Object.getOwnPropertyDescriptor(person, 'lastName');
console.log('lastName', descriptor);
// lastName {value: "Lee", writable: false, enumerable: false, configurable: false}

// 접근자 프로퍼티 정의
Object.defineProperty(person, 'fullName', {
	// getter 함수
	get() {
		return `${this.firstName} ${this.lastName}`;
	},
	// setter 함수
	set(name) {
		[this.firstName, this.lastName] = name.split(' ');
	},
	enumerable: true,
	configurable: true
});
descriptor = Object.getOwnPropertyDescriptor(person, 'fullName');
console.log('fullName', descriptor);
// fullName {get: ƒ, set: ƒ, enumerable: true, configurable: true}

person.fullName = 'Heegun Lee';
console.log(person); // {firstName: "Heegun", lastName: "Lee"}
```
## 📌 Reference
- https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/Object/defineProperty
- "모던 자바스크립트 Deep Dive" by 이웅모, p.226-228