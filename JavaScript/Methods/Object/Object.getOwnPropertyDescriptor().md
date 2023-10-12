# Object.getOwnPropertyDescriptor()
## 📌 Summary
> 주어진 객체의 프로퍼티 어트리뷰트 정보를 제공한다.
## 📌 Syntax
```js
Object.getOwnPropertyDescriptor(obj, prop)
```
### ◉ Parameter
#### ▪︎ obj
- 검색할 프로퍼티를 가진 객체
#### ▪︎ prop
- 정보를 검색할 프로퍼티 키
### ◉ Return Value
- 프로퍼티 어트리뷰트 정보를 가진 하나의 프로퍼티 디스크립터(PropertyDescriptor) 객체를 반환
- 존재하지 않는 프로퍼티나 상속받은 프로퍼티를 제공하면 `undefined`를 반환
## 📌 Description
- 다음과 같은 결과 값을 가진다:
	- `value`: 프로퍼티와 연결된 값 (데이터 프로퍼티만 해당)
	- `writable`: `value`가 변경될 수 있는 경우에만 `true` (데이터 프로퍼티만 해당)
	- `get`: `getter` 역할을 하는 함수. `getter`가 없으면 `undefined` 값을 가진다. (접근자 프로퍼티만 해당)
	- `set`: `setter` 역할을 하는 함수. `setter`가 없으면 `undefined` 값을 가진다. (접근자 프로퍼티만 해당)
	- `configurable`: 프로퍼티의 유형이 변경될 수 있고 삭제될 수 있는 경우에만 `true`
	- `enumerable`: 프로퍼티를 열거할 수 있는 경우에만 `true`
## 📌 Examples
```js
const person = {
	name: 'Lee',
};

console.log(Object.getOwnPropertyDescriptor(person, 'name'));
// {value: "Lee", writable: true, enumerable: true, configurable: true}
```

```js
let o, d;

o = {
  get foo() {
    return 17;
  },
};
d = Object.getOwnPropertyDescriptor(o, "foo");
console.log(d);
// {
//   configurable: true,
//   enumerable: true,
//   get: [Function: get foo],
//   set: undefined
// }

o = { bar: 42 };
d = Object.getOwnPropertyDescriptor(o, "bar");
console.log(d);
// {
//   configurable: true,
//   enumerable: true,
//   value: 42,
//   writable: true
// }

o = { [Symbol.for("baz")]: 73 };
d = Object.getOwnPropertyDescriptor(o, Symbol.for("baz"));
console.log(d);
// {
//   configurable: true,
//   enumerable: true,
//   value: 73,
//   writable: true
// }

o = {};
Object.defineProperty(o, "qux", {
  value: 8675309,
  writable: false,
  enumerable: false,
});
d = Object.getOwnPropertyDescriptor(o, "qux");
console.log(d);
// {
//   value: 8675309,
//   writable: false,
//   enumerable: false,
//   configurable: false
// }
```


## 📌 Reference
- https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/Object/getOwnPropertyDescriptor
- "모던 자바스크립트 Deep Dive" by 이웅모, p.220-221