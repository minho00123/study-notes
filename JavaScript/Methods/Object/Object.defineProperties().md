# Object.defineProperties()
## 📌 Summary
> 새로운 프로퍼티를 정의하거 기존 프로퍼티를 수정하여 객체를 반환한다.
## 📌 Syntax
```js
Object.defineProperties(obj, props)
```
### ◉ Parameter
#### ▪︎ obj
- 프로퍼티를 정의하거나 수정할 객체
#### ▪︎ props
- 정의하거나 수정할 프로퍼티 어트리뷰트 정보
### ◉ Return Value
- 새로운 프로퍼티가 추가된, 또는 수정된 객체
## 📌 Description
- `Object.defineProperty()` 참고
## 📌 Examples
```js
const person = {};

Object.defineProperties(person, {
	firstName: {
		value: 'Ungmo',
		writable: true,
		enumerable: true,
		configurable: true
	},
	lastName: {
		value: 'Lee',
		writable: true,
		enumerable: true,
		configurable: true
	},
	fullName: {
		get() {
		return `${this.firstName} ${this.lastName}`;
		},
		set(name) {
			[this.firstName, this.lastName] = name.split(' ');
		},
		enumerable: true,
		configurable: true
	}
});

person.fullName = 'Heegun Lee';
console.log(person); // {firstName: "Heegun", lastName: "Lee"}
```
## 📌 Reference
- https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/Object/defineProperties
- "모던 자바스크립트 Deep Dive" by 이웅모, p.228-229