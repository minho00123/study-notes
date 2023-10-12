
# Object.isExtensible()
## 📌 Summary
> 객체의 확장 가능 여부를 확인한다.
## 📌 Syntax
```js
Object.isExtensible(obj)
```
### ◉ Parameter
#### ▪︎ obj
- 확인할 객체
### ◉ Return Value
- `Boolean`
	- 확장 가능하면 `true`, 아니면 `false`를 반환한다.
## 📌 Examples
```js
// New objects are extensible.
const empty = {};
Object.isExtensible(empty); // true

// They can be made un-extensible
Object.preventExtensions(empty);
Object.isExtensible(empty); // false

// Sealed objects are by definition non-extensible.
const sealed = Object.seal({});
Object.isExtensible(sealed); // false

// Frozen objects are also by definition non-extensible.
const frozen = Object.freeze({});
Object.isExtensible(frozen); // false
```
## 📌 Reference
- https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/Object/isExtensible