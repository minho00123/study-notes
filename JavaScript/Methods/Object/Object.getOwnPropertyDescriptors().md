# Object.getOwnPropertyDescriptors()
## 📌 Summary
> 주어진 객체의 모든 프로퍼티 어트리뷰트를 반환한다.
## 📌 Syntax
```js
Object.getOwnPropertyDescriptors(obj)
```
### ◉ Parameter
#### ▪︎ obj
- 모든 프로퍼티 어트리뷰트를 가져올 객체
### ◉ Return Value
- 모든 프로퍼티 어트리뷰트 정보가 담긴 객체를 반환한다.
- 객체의 프로퍼티가 없을 경우 빈 객체를 반환한다.
## 📌 Description
- `Object.getOwnPropertyDescriptor` 참조
## 📌 Examples
```js
const person = {
	name: 'Lee',
};

person.age = 20;

console.log(Object.getOwnPropertyDescriptors(person));
/*
{
	name: {value: "Lee",  writable: true, enumerable: true, configurable: true},
	age: {value: 20,  writable: true, enumerable: true, configurable: true}
}
*/
```
## 📌 Reference
- https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/Object/getOwnPropertyDescriptors
- "모던 자바스크립트 Deep Dive" by 이웅모, p.221