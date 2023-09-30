---
Created: 2023-09-25 18:29
Modified: 2023-09-25 18:29
---
n
# 조건문(Conditional Statement)
---
## Description
- 주어진 조건식(Conditional Expression)의 평가 결과에 따라 실행할 코드 블록([[블록문(Block Statement)|블록문]])을 결정한다.
	- 조건식은 Boolean 값으로 평가될 수 있는 표현식이다.
### Types
#### if...else 문
- 논리적 참 또는 거짓에 따라 실행할 코드 블록을 결정한다.
```js
if (조건식1) {
	// 조건식1이 truthy면 이 코드 블록이 실행된다.
} else if (조건식2) {
	// 조건식2가 truthy면 이 코드 블록이 실행된다.
} else {
	// 조건식1과 조건식2가 모두 falsy면 이 코드 블록이 실행된다.
}
```
#### switch 문
- 주어진 표현식을 평가하여 그 값과 일치하는 표현식을 갖는 `case` 문으로 실행 흐름을 옮긴다.
	- `case` 문은 상황을 의미하는 표현식을 지정하고 콜론(:)으로 마친다. 그리고 그 뒤에 실행할 문들을 위치시킨다.
- `switch` 문의 표현식과 일치하는 `case` 문이 없다면 실행 순서는 `default` 문으로 이동한다.
	- `default` 문은 선택사항으로, 사용할 수도 있고 사용하지 않을 수도 있다.
	- `default` 문에는 `break` 문을 생략하는 것이 일반적이다.
```js
switch (표현식) {
	case 표현식1:
		switch 문의 표현식과 표현식1이 일치하면 실행될 문;
		break;
	case 표현식2:
		switch 문의 표현식과 표현식2가 일치하면 실행될 문;
		break;
	default:
		switch 문의 표현식과 일치하는 case 문이 없을 때 실행될 문;
}
```

- `if...else` 문의 조건식은 불리언 값으로 평가되어야 하지만 `switch` 문의 표현식은 불리언 값보다는 문자열이나 숫자 값인 경우가 많다.
- `switch` 문은 논리적 참, 거짓보다는 다양한 상황(`case`)에 따라 실행할 코드 블록을 결정할 때 사용한다.
## Examples
### if...else 문
```js
if (x > 50) {
  /* do something */
} else if (x > 5) {
  /* do something */
} else {
  /* do something */
}
```
### switch 문
```js
switch (expr) {
  case "Oranges":
    console.log("Oranges are $0.59 a pound.");
    break;
  case "Apples":
    console.log("Apples are $0.32 a pound.");
    break;
  case "Bananas":
    console.log("Bananas are $0.48 a pound.");
    break;
  case "Cherries":
    console.log("Cherries are $3.00 a pound.");
    break;
  case "Mangoes":
  case "Papayas":
    console.log("Mangoes and papayas are $2.79 a pound.");
    break;
  default:
    console.log(`Sorry, we are out of ${expr}.`);
}

console.log("Is there anything else you'd like?");
```
## Reference
- "모던 자바스크립트 Deep Dive" by 이웅모, p.94-100