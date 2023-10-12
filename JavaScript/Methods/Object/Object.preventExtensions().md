# Object.preventExtensions()
## 📌 Summary
> 새로운 프로퍼티가 객체에 추가되는 것을 금지한다. 또한 객체의 프로토타입이 재할당 되는 것을 방지한다.
## 📌 Syntax
```js
Object.preventExtensions(obj)
```
### ◉ Parameter
#### ▪︎ obj
- 확장 금지시킬 객체
### ◉ Return Value
- 확장 금지된 객체
## 📌 Description
- 객체의 확장을 금지시킨다.
- 객체의 프로퍼티는 삭제될 수 있으나 새 프로퍼티 추가는 할 수 없다.
	- 프로퍼티 동작 추가와 `Object.defineProperty` 메서드로 추가, 둘 다 모두 금지된다.
	- strict mode에서는 `TypeError`를 발생시킨다.
- 확장이 가능한 객체인지 여부는 `Object.isExtensible` 메서드로 확인할 수 있다.
## 📌 Examples
```js
const person = { name: 'Lee' };

// person 객체는 확장이 금지된 객체가 아니다.
console.log(Object.isExtensible(person)); // true

// person 객체의 확장을 금지하여 프로퍼티 추가를 금지한다.
Object.preventExtensions(person);

// person 객체는 확장이 금지된 객체다.
console.log(Object.isExtensible(person)); // false

// 프로퍼티 추가가 금지된다.
person.age = 20; // 무시. strict mode에서는 에러
console.log(person); // {name: "Lee"}

// 프로퍼티 추가는 금지되지만 삭제는 가능하다.
delete person.name;
console.log(person); // {}

// 프로퍼티 정의에 의한 프로퍼티 추가도 금지된다.
Object.defineProperty(person, 'age', { value: 20 });
// TypeError: Cannot define property age, object is not extensible
```
## 📌 Reference
- https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/Object/preventExtensions
- "모던 자바스크립트 Deep Dive" by 이웅모, p.229-230