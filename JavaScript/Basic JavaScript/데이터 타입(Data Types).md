---
Created: 2023-09-25 15:27
Modified: 2023-09-24 17:03
---

# 데이터 타입(Data Types)
---
## Summary
> [[값(Value)]]의 종류를 나타낸다.
## Description
### Types
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

#### Primitive Type(기본형, 원시형)
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
- [[유사 배열 객체(Array-like Objects)]]다.
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
#### Objective/Reference Type (객체형, 참조형)
##### 8. Object
- 원시형을 제외한 `object`, `array` 등은 모두 객체다.
### 데이터 타입이 필요한 이유
- 값을 지정/참조할 때 필요한 메모리 공간의 크기를 결정한다.
- 메모리에서 읽어 들인 2진수를 어떻게 해석할지 결정한다.
## Reference
- "모던 자바스크립트 Deep Dive" by 이웅모, p.59-70