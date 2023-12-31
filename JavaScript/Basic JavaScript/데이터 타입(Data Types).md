# 데이터 타입(Data Types)
---
## 📌 Summary
> 값(Value)의 종류를 나타낸다.
## 📌 Description
### ◉ Types
<table class="tg">
<thead>
  <tr>
    <th class="tg-b411">Type</th>
    <th class="tg-b411">Date Type</th>
    <th class="tg-b411">Description</th>
  </tr>
</thead>
<tbody>
  <tr>
    <td class="tg-baqh" rowspan="7">원시 타입<br>(Primitive Type)</td>
    <td class="tg-baqh">Number</td>
    <td class="tg-0lax">숫자. 정수와 실수 구분 없이 하나의 숫자 타입만 존재</td>
  </tr>
  <tr>
    <td class="tg-baqh">String<br></td>
    <td class="tg-0lax">문자열</td>
  </tr>
  <tr>
    <td class="tg-baqh">Boolean</td>
    <td class="tg-0lax">논리적 참(true)과 거짓(false)</td>
  </tr>
  <tr>
    <td class="tg-baqh">undefined</td>
    <td class="tg-0lax">var 키워드로 선언된 변수에 암묵적으로 할당되는 값</td>
  </tr>
  <tr>
    <td class="tg-baqh">null</td>
    <td class="tg-0lax"><span style="font-weight:400;font-style:normal">값이 없다는 것을 의도적으로 명시할 때 사용하는 값</span></td>
  </tr>
  <tr>
    <td class="tg-baqh">Symbol</td>
    <td class="tg-0lax">ES6에서 추가된 7번째 타입</td>
  </tr>
  <tr>
    <td class="tg-baqh">BigInt</td>
    <td class="tg-0lax">Number보다 더 큰 정수를 표현할 수 있는 숫자</td>
  </tr>
  <tr>
    <td class="tg-baqh" colspan="2">객체 타입<br>(Object Type)</td>
    <td class="tg-0lax">객체, 배열, 함수 등</td>
  </tr>
</tbody>
</table>

#### ▪︎ Primitive Type(기본형, 원시형)
##### 1. Number
- 8byte 크기를 가진 실수(floating-point)로 처리된다.
	- ‘double-precision 64-bit binary format [IEEE754]’ 형식을 따른다.
- 최대 값은 `2^1024 - 1`까지 나타낼 수 있으며, 정수의 범위는 `-2^53 - 1 ~ 2^53 - 1`까지 나타낼 수 있다.
- `Infinity`, `-Infinity`, `NaN`과 같은 특수한 값이 있다.
##### 2. String
- UTF-16으로 인코딩되는 텍스트를 나타낸다.
- 작은따옴표(''), 큰따옴표(""), 또는 백틱(\`\`)으로 택스트를 감싼다.
- 변경 불가능(immutable)한 값을 가지기 때문에 생성은 가능하지만, 수정은 불가능하다.
- 문자 길이에 따라 메모리 공간의 크기가 달라진다.
	- 문자 1개당 2byte를 차지한다.
- 유사 배열 객체(Array-like Objects)다.
##### 3. Boolean
- 논리적 참, 거짓을 나타내는 `true`와 `false`를 가진다.
##### 4. Null
- `null` 값만 가진다.
##### 5. Undefined
- `undefined` 값만 가진다.
##### 6. Symbol
- ES6에서 새롭게 추가된 데이터 타입으로, 다른 값과 중복되지 않는 유일무이한 값이다.
- 일반적으로 이름이 충돌할 위험이 있는 객체의 유일한 프로퍼티 키를 만들기 위해 사용한다.
##### 7. BigInt
- ES11에서 추가되었으며, 기존의 나타낼 수 있는 정수의 최대값보다 더 큰 숫자를 표현할 수 있다.
- 정수 리터럴 뒤에 n을 붙이거나 BigInt 함수를 호출해 생성한다. Ex. `10n`, `BigInt(10)`
#### ▪︎ Objective/Reference Type (객체형, 참조형)
##### 8. Object
- 원시형을 제외한 `object`, `array` 등은 모두 객체다.
### ◉ 데이터 타입이 필요한 이유
- 값을 지정/참조할 때 필요한 메모리 공간의 크기를 결정한다.
- 메모리에서 읽어 들인 2진수를 어떻게 해석할지 결정한다.
### ◉ 원시 값 vs. 객체 값
> 💡 **주요 차이점**
> 1. 원시 값은 변경 불가능한 값(immutable value)이고, 객체 값은 변경 가능한 값(mutable value)이다.
> 2. 원시 값에 변수를 할당하면 실제 값이 저장되지만, 객체는 참조 값이 저장된다.
> 3. 원시 값은 값에 의한 전달(pass by value)이지만, 객체 값은 참조에 의한 전달(pass by reference)이다.
#### ▪︎ 원시 값
- 원시 타입의 값은 변경 불가능한 값이다.
	- 변경 불가능하다는 것은 변수가 아닌 **값**에 대한 진술이다.
- 원시 값을 가진 변수를 재할당하면 새로운 메모리 공간을 확보하고 재할당 값을 저장한다. 그리고 변수가 참조하던 메모리 공간의 주소를 변경한다. → 이를 불변성(immutability)이라 한다.
```js
let score = 80;
let copy = score;

console.log(score); // 80
console.log(copy);  // 80

score = 100;

console.log(score); // 100
console.log(copy);  // 80
```
- 위 예제처럼, 변수에 원시 값을 갖는 변수를 할당하면 할당받는 변수(`copy`)에는 할당되는 변수(`score`)의 원시 값이 복사되어 전달된다. → 이를 "*값에 의한 전달*"이라 한다.
- 두 변수(`score` & `copy`)의 원시 값은 서로 다른 메모리 공간에 저장되어 있기 때문에 어느 한쪽을 재할당하여 값을 변경하더라도 서로 간섭할 수 없다.
- `score` 변수와 `copy` 변수의 값 80은 다른 메모리 공간에 저장된 별개의 값이다.
#### ▪︎ 객체
- 객체의 크기는 동적이고, 프로퍼티의 값으로 객체가 올 수 있기 때문에 깊은 복사를 통해 생성하기에는 메모리의 효율성과 성능이 나쁘다.
	- 객체 값을 가진 변수는 재할당 없이 프로퍼티를 동적으로 추가/갱신/삭제할 수 있다.
- 따라서 메모리 효율성과 성능을 향상시키기 위해 객체는 변경 가능한 값으로 설계되었다.
	- 여러 개의 식별자가 하나의 객체를 공유할 수 있다는 구조적 단점이 있다.
- 객체를 할당한 변수가 기억하는 메모리 주소를 통해 메모리 공간에 접근하면 참조 값(reference value)에 접근할 수 있다.
	- 참조 값은 생성된 객체가 저장된 메모리 공간의 주소, 그 자체다.
```js
const person = {
	name: 'Lee',
};

// 얕은 복사
let copy = person;
```
- 객체 값을 가지는 변수(`person`)를 다른 변수(`copy`)에 할당하면 원본의 **참조 값**이 복사되어 전달된다. → 이를 "참조에 의한 전달"이라 한다.
- `person`과 `copy`는 동일한 객체를 가리킨다.
	- 따라서 원본 또는 사본 중 어느 한쪽에서 객체를 변경하면 서로 영향을 주고받는다.

#### ※ 얕은 복사(shallow copy) vs. 깊은 복사(deep copy)
- 객체를 프로퍼티 값으로 갖는 객체의 경우 얕은 복사는 한 단계까지만 복사하는 것을 말하고, 깊은 복사는 객체에 중첩되어 있는 객체까지 모두 복사하는 것을 말한다.
```js
const o = { x: { y: 1 } };

// 얕은 복사
const c1 = { ...o };
console.log(c1 === o);     // false
console.log(c1.x === o.x); // true

// lodash의 cloneDeep을 사용한 깊은 복사
const = require('lodash');
const c2 = _.cloneDeep(o);
console.log(c2 === o);     // false
console.log(c2.x === o.x); // false
```
- 얕은 복사와 깊은 복사로 생성된 객체는 참조 값이 다른 별개의 객체다. 
	- 하지만 얕은 복사는 중첩되어 있는 객체의 참조 값을 복사하고, 깊은 복사는 객체에 중첩되어 있는 객체까지 모두 복사해서 원시 값처럼 완전한 복사본을 만든다는 차이가 있다.
- 참고로 원시 값을 할당한 변수를 다른 변수에 할당하는 것을 깊은 복사, 객체를 할당한 변수를 다른 변수에 할당하는 것을 얕은 복사라고 부르는 경우도 있다.
## 📌 Reference
- "모던 자바스크립트 Deep Dive" by 이웅모, p.59-70, 137-153