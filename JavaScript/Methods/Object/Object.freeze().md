# Object.freeze()
## 📌 Summary
> 객체를 동결(freeze)한다.
## 📌 Syntax
```js
Object.freeze(obj)
```
### ◉ Parameter
#### ▪︎ obj
- 동결할 객체
### ◉ Return Value
- 동결된 객체
## 📌 Description
- 프로퍼티 추가 및 삭제와 프로퍼티 어트리뷰트 재정의 금지, 프로퍼티 값 갱신을 금지한다.
- 동결된 객체는 읽기만 가능하다.
- 동결된 객체인지 여부는 `Object.isFrozen` 메서드로 확인할 수 있다.
## 📌 Examples
```js
const person = { name: 'Lee' };

// person 객체는 동결(freeze)된 객체가 아니다.
console.log(Object.isFrozen(person)); // false

// person 객체를 동결하여 프로퍼티 추가, 삭제, 재정의, 쓰기를 금지한다.
Object.freeze(person);

// person 객체는 동결된 객체다.
console.log(Object.isFrozen(person)); // true

// 동결된 객체는 writable과 configurable이 false다.
console.log(Object.getOwnPropertyDescriptors(person));
/*
{
	name: {value: "Lee", writable: false, enumerable: true, configurable: false},
}
*/

// 프로퍼티 추가가 금지된다.
person.age = 20; // 무시. strict mode에서는 에러
console.log(person); // {name: "Lee"}

// 프로퍼티 삭제가 금지된다.
delete person.name; // 무시. strict mode에서는 에러
console.log(person); // {name: "Lee"}

// 프로퍼티 값 갱신이 금지된다.
person.name = 'Kim'; // 무시. strict mode에서는 에러
console.log(person); // {name: "Lee"}

// 프로퍼티 어트리뷰트 재정의가 금지된다.
Object.defineProperty(person, 'name', { configurable: true });
// TypeError: Cannot redefine property: name
```
## 📌 Reference
- https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/Object/freeze
- "모던 자바스크립트 Deep Dive" by 이웅모, p.231-232