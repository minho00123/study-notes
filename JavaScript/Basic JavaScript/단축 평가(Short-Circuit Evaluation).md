---
Created: 2023-09-28 15:36
Modified: 2023-09-28 15:35
---
# 단축 평가(Short-Circuit Evaluation)
---
## Summary
> [[표현식(Expression)]]을 평가하는 도중에 평가 결과가 확정된 경우 나머지 평가 과정을 생략하는 것을 말한다.
## Description
### 논리 연산자를 사용한 단축 평가
- 논리곱(`&&`) 연산자와 논리합(`||`) 연산자는 논리 연산의 결과를 결정하는 피연산자를 타입 변환하지 않고 그대로 반환한다. 이를 단축 평가라 한다.
- 단축 평가는 다음 규칙을 따른다:
<table>
	<thead>
		<th>단축 평가 표현식</th>
		<th>평가 결과</th>
	</thead>
	<tbody>
		<tr>
			<td>true || anything</td>
			<td>true</td>
		</tr>
		<tr>
			<td>false || anything</td>
			<td>anything</td>
		</tr>
		<tr>
			<td>true && anything</td>
			<td>anything</td>
		</tr>
		<tr>
			<td>false && anything</td>
			<td>false</td>
		</tr>
	</tbody>
</table>

```js
// 논리합(||) 연산자
'Cat' || 'Dog' // "Cat"
false || 'Dog' // "Dog"
'Cat' || false // "Cat"

// 논리곱(&&) 연산자
'Cat' && 'Dog' // "Dog"
false && 'Dog' // false
'Cat' && false // false
```
- 단축 평가를 사용하면 `if` 문을 대체할 수 있다.
	- 어떤 조건이 Truthy 값일 때 무언가를 해야 한다면 논리곱(`&&`) 연산자 표현식으로 `if` 문을 대체할 수 있다.
```js
let done = true;
let message = '';

// 주어진 조건이 true일 때
if (done) message = '완료';

// if 문은 단축 평가로 대체 가능하다.
// done이 true라면 message에 '완료'를 할당
message = done && '완료';
console.log(message); // 완료
```

- 조건이 Falsy 값일 때 무언가를 해야 한다면 논리합(`||`) 연산자 표현식으로 `if` 문을 대체할 수 있다.
```js
let done = false;
let message = '';

// 주어진 조건이 false일 때
if (!done) message = '미완료';

// if 문은 단축 평가로 대체 가능하다.
// done이 false라면 message에 '미완료'를 할당
message = done || '미완료';
console.log(message); // 미완료
```

#### 객체를 가리키는 변수가 `null` 또는 `undefined`가 아닌지 확인하고 프로퍼티를 참조할 때
- 객체를 가리키는 변수의 값이 객체가 아닌 `null` 또는 `undefined`인 경우 타입 에러(TypeError)가 발생한다. 에러가 발생하면 프로그램은 강제 종료된다.
	- 이때 단축 평가를 사용하면 에러를 발생시키지 않는다.
```js
let elem = null;
let value = elem.value; // TypeError: Cannot read property 'value' of null

// 단축 평가 사용
let value = elem && elem.value; // null

```
#### 함수 매개변수에 기본값을 설정할 때
- 함수를 호출할 때 인수를 전달하지 않으면 매개변수에는 `undefined`가 할당된다.
	- 이때 단축 평가를 사용해 매개변수의 기본값을 설정하면 `undefined로` 인해 발생할 수 있는 에러를 방지할 수 있다.
```js
// 단축 평가를 사용한 매개변수의 기본값 설정
function getStringLength(str) {
	str = str || '';
	return str.length;
}

getStringLength(); // 0
getStringLength('hi'); // 2

// ES6의 매개변수의 기본값 설정
function getStringLength(str = '') {
	return str.length;
}

getStringLength(); // 0
getStringLength('hi'); // 2
```

### 옵셔널 체이닝(Optional Chaining) 연산자 `?.`
- ES11(ECMAScript2020)에서 도입된 옵셔널 체이닝 연산자는 좌항의 피연산자가 `null` 또는 `undefined`인 경우 `undefined`를 반환하고, 그렇지 않으면 우항의 프로퍼티 참조를 이어간다.
```js
let elem = null;

let value = elem?.value;
console.log(value); // undefined
```
- 옵셔널 체이닝 연산자는 객체를 가리키는 변수가 `null` 또는 `undefined`가 아닌지 확인하고 프로퍼티를 참조할 때 유용하다.
- 옵셔널 체이닝 연산자가 도입되기 이전에는 논리 연산자 `&&`를 사용한 단축 평가를 통해 변수가 `null` 또는 `undefined`인지 확인했다.
	- 논리 연산자 `&&`는 좌항 피연산자가 Falsy 값이면 좌항 피연산자를 그대로 반환한다. 하지만 `0`이나 `''`은 객체로 평가될 때도 있다.
```js
let str = '';

// 문자열의 길이(length)를 참조한다.
let length = str && str.length;

// 문자열의 길이(length)를 참조하지 못한다.
console.log(length); // ''
```
- 하지만 옵셔널 체이닝 연산자는 좌항 피연산자가 Falsy 값이라도 `null` 또는 `undefined`가 아니면 우항의 프로퍼티 참조를 이어간다.
```js
let str = '';

let length = str?.length;
console.log(length); // 0
```

### null 병합(nullish coalescing) 연산자 `??`
- ES11에서 도입된 null 병합 연산자는 좌항의 피연산자가 `null` 또는 `undefined`인 경우 우항의 피연산자를 반환하고, 그렇지 않으면 좌항의 피연산자를 반환한다. 
- null 병합 연산자는 변수에 기본값을 설정할 때 유용하다.
```js
let foo = null ?? 'default string';
console.log(foo); // "default string"
```
- null 병합 연산자가 도입되기 이전에는 논리 연산자 `||` 를 이용한 단축 평가를 통해 변수에 기본값을 설정했다.
	- 논리 연산자 `||`를 사용한 단축 평가의 경우 좌항의 피연산자가 Falsy 값이면 우항의 피연산자를 반환한다. 만약 Falsy 값인 0이나 ''도 기본값으로서 유효하다면 예기치 않은 동작이 발생할 수 있다.
```js
let foo = '' || 'default string';
console.log(foo); // "default string"
```
- 하지만 null 병합 연산자는 좌항의 피연산자가 Falsy 값이라도 `null` 또는 `undefined`가 아니면 좌항의 피연산자를 그대로 반환한다.
```js
let foo = '' ?? 'default string';
console.log(foo); // ""
```
## Reference
- "모던 자바스크립트 Deep Dive" by 이웅모, p.118-123