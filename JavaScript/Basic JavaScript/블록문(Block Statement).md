---
Created: 2023-09-25 18:24
Modified: 2023-09-25 18:24
---

# 블록문(Block Statement)
---
## Description
- 0개 이상의 [[문(Statement)]]을 중괄호({})로 묶은 것으로, 코드 블록 또는 블록이라고 부르기도 한다.
- 자바스크립트는 블록문을 하나의 실행 단위로 취급한다.
- 문의 끝에는 세미콜론(;)을 붙이는게 일반적이지만, 블록문은 언제나 문의 종료를 의미하는 자체 종결성을 갖기 때문에 세미콜론을 붙이지 않는다.
## Examples
```jsx
// 블록문
{
	let foo = 10;
}

// 제어문
let x = 1;
if (x < 10) {
	x++;
}

// 함수 선언문
function sum(a, b) {
	return a + b;
}
```
## Reference
- "모던 자바스크립트 Deep Dive" by 이웅모, p.93-94