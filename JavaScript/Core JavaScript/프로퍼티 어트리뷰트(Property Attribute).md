# 프로퍼티 어트리뷰트(Property Attribute)
---
## 📌 Summary
> 자바스크립트 엔진이 관리하는 내부 상태 값(meta-property)
## 📌 Description
### ◉ 내부 슬롯(Internal Slot)과 내부 메서드(Internal Method)
- ECMAScript 사양에서 자바스크립트 엔진의 구현 알고리즘을 설명하기 위해 사용하는 의사 프로퍼티(pseudo property)와 의사 메서드(pseudo method)다.
	- ECMAScript 사양에서 이중 대괄호 (`[[ ... ]]`)로 감싼 이름들이 내부 슬롯과 내부 메서드다.
- 자바스크립트 엔진의 내부 로직이기 때문에 직접적으로 접근하거나 호출할 수 없다.
- 모든 객체는 `[[Prototype]]` 내부 슬롯을 가진다.
	- 직접적으로는 접근이 불가능하지만 `__proto__`를 통해 간접적으로 접근할 수 있다.
```js
const obj = {};

obj.[[Prototype]] // Uncaught SyntaxError: Unexpected token '['
obj.__proto__     // Object.prototype
```
### ◉ 프로퍼티 어트리뷰트(Property Attribute)
- 자바스크립트 엔진이 관리하는 내부 상태 값(meta-property)을 일컫는다.
	- 내부 상태 값에는 `[[Value]]`, `[[Writable]]`, `[[Enumerable]]`, `[[Configurable]]`가 있다.
- 프로퍼티를 생성할 때 프로퍼티 어트리뷰트를 기본값으로 자동 정의한다.
- 내부 슬롯이기 때문에 직접 접근할 수 없지만 `Object.getOwnPropertyDescriptor` 메서드를 사용하여 간접적으로 확인할 수는 있다.
### ◉ 데이터 프로퍼티(Data Property) vs. 접근자 프로퍼티(Accesor Property)
#### ▪︎ 데이터 프로퍼티
- 키와 값으로 구성된 일반적인 프로퍼티
- 다음과 같은 프로퍼티 어트리뷰트를 갖는다:

| 프로퍼티 어트리뷰트 | 프로퍼티 디스크립터 객체의 프로퍼티 | 설명                                                                                                                                                                                                                                                                                     |
| ------------------- | ----------------------------------- |:---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| `[[Value]]`         | value                               | • 프로퍼티 키를 통해 프로퍼티 값에 접근하면 반환되는 값이다. <br> • 프로퍼티 키를 통해 프로퍼티 값을 변경하면 `[[Value]]`에 값을 재할당한다. 이때 프로퍼티가 없으면 프로퍼티를 동적 생성하고 생성된 프로퍼티의 `[[Value]]`에 값을 저장한다.                                              |
| `[[Writable]]`      | writable                            | • 프로퍼티 값의 **변경 가능 여부**를 나타내며 불리언 값을 갖는다. <br> • 값이 `false`인 경우 해당 프로퍼티의 `[[Value]]`의 값을 변경할 수 없는 읽기 전용 프로퍼티가 된다.                                                                                                   |
| `[[Enumerable]]`    | enumerable                          | • 프로퍼티의 **열거 가능 여부**를 나타내며 불리언 값을 갖는다. <br> • 값이 `false`인 경우 해당 프로퍼티는 `for...in` 문이나 `Object.keys` 메서드 등으로 열거할 수 없다.                                                                                                   |
| `[[Configurable]]`  | configurable                        | • 프로퍼티의 **재정의 가능 여부**를 나타내며 불리언 값을 갖는다. <br>  • 값이 `false`인 경우 해당 프로퍼티의 삭제, 프로퍼티 어트리뷰트 값의 변경이 금지된다. 단, `true`인 경우 `[[Value]]`의 변경과 `[[Writable]]`을 `false`로 변경하는 것은 허용된다. |

- `[[Value]]`의 값은 프로퍼티 값으로 초기화되고, `[[Writable]]`, `[[Enumerable]]`, `[[Configurable]]`의 값은 `true`로 초기화된다.
	- 프로퍼티를 동적으로 추가해도 이와 같이 초기화된다.
```js
const user = {
    name: 'Mino',
};

user.greet = function () {
    return `Hi! I'm ${this.name}!`;
}

console.log(Object.getOwnPropertyDescriptors(user));
/*
{
	name: {value: 'Mino',  writable: true, enumerable: true, configurable: true},
	greet: {value: ƒ,  writable: true, enumerable: true, configurable: true}
}
*/
```
#### ▪︎ 접근자 프로퍼티
- 접근자 함수(accessor function)로 구성된 프로퍼티
	- 접근자 함수는 `getter`/`setter` 함수라고도 부른다.
- 자체적으로 값(`[[Value]]`)을 갖지 않고, 데이터 프로퍼티의 값을 읽거나 저장할 때 관여한다.
- 다음과 같은 프로퍼티 어트리뷰트를 갖는다:

| 프로퍼티 어트리뷰트 | 프로퍼티 디스크립터 객체의 프로퍼티 | 설명                                                                                                                                                                                                                                |
| ------------------- | ----------------------------------- |:----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| `[[Get]]`           | get                                 | • 접근자 프로퍼티를 통해 데이터 프로퍼티의 값을 읽을 때 호출되는 접근자 함수다. <br> • 접근자 프로퍼티 키로 프로퍼티 값에 접근하면 프로퍼티 어트리뷰트 `[[Get]]`의 값인 `getter` 함수가 호출되고 그 결과가 프로퍼티 값으로 반환된다. |
| `[[Set]]`           | set                                 | • 접근자 프로퍼티를 통해 데이터 프로퍼티의 값을 저장할 때 호출되는 접근자 함수다. <br> • 접근자 프로퍼티 키로 프로퍼티 값을 저장하면 프로퍼티 어트피뷰트 `[[Set]]`의 값인 `setter` 함수가 호출되고 그 결과가 프로퍼티 값으로 저장된다. |
| `[[Enumerable]]`    | enumerable                          | • 데이터 프로퍼티의 `[[Enumerable]]`과 같다.                                                                                                                                                                                        |
| `[[Configurable]]`  | configurable                        | • 데이터 프로퍼티의 `[[Configurable]]`과 같다.                                                                                                                                                                                      | 

```js
const user = {
	firstName: 'Mino',
    lastName: 'Jang',

    get fullName() {
        return `${this.firstName} ${this.lastName}`;
    },

    set fullName(name) {
        [this.firstName, this.lastName] = name.split(' ');
    }
};

console.log(user.fullName); // Mino Jang
user.fullName = 'YJ Jang';
console.log(user.fullName); // YJ Jang

Object.getOwnPropertyDescriptors(user);
/*
{
	firstName: {value: 'YJ',  writable: true, enumerable: true, configurable: true},
	lastName: {value: 'Jang',  writable: true, enumerable: true, configurable: true}
	},
	fullName: {get: ƒ, set: ƒ, enumerable: true, configurable: true}
*/

```
- 메서드 앞에 `get`, `set`이 붙은 메서드는 `getter`와 `setter` 함수이고, `getter`/`setter` 함수의 이름 `fullName`이 접근자 프로퍼티다.

- 접근자 프로퍼티와 데이터 프로퍼티를 구별하는 방법은 다음과 같다.
```js
// 일반 객체의 __proto__는 접근자 프로퍼티다.
Object.getOwnPropertyDescriptor(Object.prototype, '__proto__');
// {get: ƒ, set: ƒ, enumerable: false, configurable: true}

// 함수 객체의 prototype은 데이터 프로퍼티다.
Object.getOwnPropertyDescriptor(function() {}, 'prototype');
// {vale: {...}, writable: true, enumerable: false, configurable: false}
```
### ◉ 프로퍼티 정의
- 새로운 프로퍼티를 추가하여 프로퍼티 어트리뷰트를 명시적으로 정의하거나, 기존 프로퍼티의 프로퍼티 어트리뷰트를 재정의하는 것을 말한다.
	- 이를 통해 객체의 프로퍼티가 어떻게 동작해야 하는지를 명확히 정의할 수 있다.
- `Object.defineProperty` 메서드를 사용하여 프로퍼티의 어트리뷰트를 정의한다.
### ◉ 객체 변경 방지
- 객체는 변경 가능한 값이므로 재할당 없이 프로퍼티를 추가/삭제할 수 있고, 프로퍼티 값을 갱신할 수 있으며, `Object.defineProperty` / `Object.defineProperties` 메서드를 사용하여 프로퍼티 어트리뷰트를 재정의할 수도 있다.
- 자바스크립트는 객체의 변경을 방지하는 다양한 메서드를 제공한다. 객체 변경 방지 메서드들은 객체의 변경을 금지하는 강도가 다르다.

| 구분           | 메서드                     | 프로퍼티 추가 | 프로퍼티 삭제 | 프로퍼티 값 읽기 | 프로퍼티 값 쓰기 | 프로퍼티 어트리뷰트 재정의 |
| -------------- | -------------------------- | ------------- | ------------- | ---------------- | ---------------- | -------------------------- |
| 객체 확장 금지 | `Object.preventExtensions` | X             | O             | O                | O                | O                          |
| 객체 밀봉      | `Object.seal`              | X             | X             | O                | O                | X                          |
| 객체 동결      | `Object.freeze`            | X             | X             | O                | X                | X                          | 
#### 불변 객체
- 객체 변경 방지 메서드들은 중첩 객체까지는 영향을 주지 못한다. 즉, 얕은 변경 방지(shallow only)만 진행한다.
```js
const user = {
    id: 1,
    name: 'Mino',
    address: { city: 'Seoul' }
}

Object.freeze(user);
console.log(Object.isFrozen(user.address)); // false

user.address.city = 'New York';
console.log(user.address); // {city: 'New York'}
```
- 객체의 중첩 객체까지 동결하려면 객체를 값으로 갖는 모든 프로퍼티에 대해 재귀적으로 `Object.freeze` 메서드를 호출해야 한다.
```js
function deepFreeze(target) {
	// 객체가 아니거나 동결된 객체는 무시하고 객체이고 동결되지 않은 객체만 동결한다.
	if (target && typeof target === 'object' && !Object.isFrozen(target)) {
		Object.freeze(target);
		Object.keys(target).forEach(key => deepFreeze(target[key]));
	}
	return target;
}

const user = {
    id: 1,
    name: 'Mino',
    address: { city: 'Seoul' }
}

deepFreeze(user);
console.log(Object.isFrozen(user.address)); // true

user.address.city = 'New York';
console.log(user.address); // {city: 'Seoul'}
```
## 📌 Reference
- "모던 자바스크립트 Deep Dive" by 이웅모, p.219-233