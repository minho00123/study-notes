# Object.seal()
## 📌 Summary
> 객체를 밀봉(seal)한다.
## 📌 Syntax
```js
Object.seal(obj)
```
### ◉ Parameter
#### ▪︎ obj
- 밀봉할 객체
### ◉ Return Value
- 밀봉된 객체
## 📌 Description
- 프로퍼티 추가 및 삭제와 프로퍼티 어트리뷰트 재정의를 금지한다.
- 밀봉된 객체는 읽기와 쓰기만 가능하다.
- 밀봉된 객체인지 여부는 `Object.isSealed` 메서드로 확인할 수 있다.
## 📌 Examples
```js
const person = { name: 'Lee' };

// person 객체는 밀봉(seal)된 객체가 아니다.
console.log(Object.isSealed(person)); // false

// person 객체를 밀봉하여 프로퍼티 추가, 삭제, 재정의를 금지한다.
Object.seal(person);

// person 객체는 밀봉된 객체다.
console.log(Object.isSealed(person)); // true

// 밀봉된 객체는 configurable이 false다.
console.log(Object.getOwnPropertyDescriptors(person));
/*
{
	name: {value: "Lee", writable: true, enumerable: true, configurable: false},
}
*/

// 프로퍼티 추가가 금지된다.
person.age = 20; // 무시. strict mode에서는 에러
console.log(person); // {name: "Lee"}

// 프로퍼티 삭제가 금지된다.
delete person.name; // 무시. strict mode에서는 에러
console.log(person); // {name: "Lee"}

// 프로퍼티 값 갱신은 가능하다.
person.name = 'Kim';
console.log(person); // {name: "Kim"}

// 프로퍼티 어트리뷰트 재정의가 금지된다.
Object.defineProperty(person, 'name', { configurable: true });
// TypeError: Cannot redefine property: name
```
## 📌 Reference
- https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/Object/seal
- "모던 자바스크립트 Deep Dive" by 이웅모, p.230-231