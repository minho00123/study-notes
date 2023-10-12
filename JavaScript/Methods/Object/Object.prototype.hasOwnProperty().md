# Object.prototype.hasOwnProperty()
## 📌 Summary
> 객체가 주어진 프로퍼티를 자체적으로 가지고 있는지 여부를 나타낸다.
## 📌 Syntax
```js
hasOwnProperty(prop)
```
### ◉ Parameter
#### ▪︎ prop
- 테스트할 프로퍼티의 문자열 또는 Symbol
### ◉ Return Value
- `Boolean`
## 📌 Description
- 인수로 전달받은 프로퍼티 키가 객체 고유의 프로퍼티 키인 경우에만 `true`를 반환하고 상속받은 프로토타입의 프로퍼티 키인 경우 `false`를 반환한다.
## 📌 Examples
``` js
const example = {};
example.hasOwnProperty("prop"); // false

example.prop = "exists";
example.hasOwnProperty("prop"); // true - 'prop' has been defined

example.prop = null;
example.hasOwnProperty("prop"); // true - own property exists with value of null

example.prop = undefined;
example.hasOwnProperty("prop"); // true - own property exists with value of undefined
```
## 📌 Reference
- https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/Object/hasOwnProperty