# Object.getPrototypeOf()
## 📌 Summary
> 주어진 객체의 프로토타입(`[[Prototype]]` 프로퍼티 값)을 반환한다.
## 📌 Syntax
```js
Object.getPrototypeOf(obj)
```
### ◉ Parameter
#### obj
- 프로토타입을 반환할 객체
### ◉ Return Value
- 주어진 객체의 프로토타입
## 📌 Examples
```js
const proto = {};
const obj = Object.create(proto);
Object.getPrototypeOf(obj) === proto; // true
```
## 📌 Reference
- https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/Object/getPrototypeOf