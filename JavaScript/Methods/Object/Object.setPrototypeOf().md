# Object.setPrototypeOf()
## 📌 Summary
> 주어진 객체의 프로토타입(`[[Prototype]]` 프로퍼티)을 다른 객체 또는 `null`로 설정한다.
## 📌 Syntax
```js
Object.setPrototypeOf(obj, prototype)
```
### ◉ Parameter
#### obj
- 프로토타입을 설정할 객체
#### prototype
- 객체의 새로운 프로토타입
### ◉ Return Value
- 지정한 객체
### ◉ Exceptions
#### TypeError
- `obj`가 `undefined`이거나 `null`인 경우
- `obj`가 non-extensible하거나, `Object.prototype` 또는 `window`인 경우
	- 단, `obj`와 `prototype`이 같은 경우 에러는 발생하지 않는다.
- `prototype`이 객체가 아니거나 `null`인 경우
## 📌 Examples
```js
function Human(name, level) {
  this.name = name;
  this.level = level;
}

function SuperHero(name, level) {
  Human.call(this, name, level);
}

Object.setPrototypeOf(SuperHero.prototype, Human.prototype);

// Set the `[[Prototype]]` of `SuperHero.prototype`
// to `Human.prototype`
// To set the prototypal inheritance chain

Human.prototype.speak = function () {
  return `${this.name} says hello.`;
};

SuperHero.prototype.fly = function () {
  return `${this.name} is flying.`;
};

const superMan = new SuperHero("Clark Kent", 1);

console.log(superMan.fly());
console.log(superMan.speak());
```
## 📌 Reference
- https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/Object/setPrototypeOf