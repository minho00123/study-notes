# continue 문
---
## 📌 Summary
> 반복문의 코드 블록 실행을 현 지점에서 중단한다.
## 📌 Syntax
```js
continue [label];
```

- `label`: 레이블에 연결한 식별자
### ◉ Error
- 반복문 안에 있는 함수에서는 사용할 수 없다.
```js
for (let i = 0; i < 10; i++) {
  (() => {
    continue; // SyntaxError: Illegal continue statement: no surrounding iteration statement
  })();
}
```
- 레이블을 사용할 때, `continue`문은 `label`문 안에 있어야 한다.
```js
label: for (let i = 0; i < 10; i++) {
  console.log(i);
}

for (let i = 0; i < 10; i++) {
  continue label; // SyntaxError: Undefined label 'label'
}
```
- `label`문은 반복문이어야 한다.
```js
label: {
  for (let i = 0; i < 10; i++) {
    continue label; // SyntaxError: Illegal continue statement: 'label' does not denote an iteration statement
  }
}
```
## 📌 Description
- `break`문과는 다르게 반복문을 탈출하지는 않는다.
    - `while`, `do...while`문에서는 조건식으로 넘어간다.
    - `for` 문에서는 update expression(증감식)으로 넘어간다.
    - `for...in`, `for...of`,`for await...of`문에서는 다음 반복문으로 넘어간다.
- `label`문에서 `continue`문을 사용할 때는 `label`문 안에 있어야 한다.
- 어떠한 경우라도 스크립트 최상단에서는 사용할 수 없다.
## 📌 Examples
- `while`문에서의 활용
```js
let i = 0;
let n = 0;

while (i < 5) {
  i++;

  if (i === 3) {
    continue;
  }

  n += i;
}

// n takes 1, 3, 7, and 12.
```
- `label`문에서의 활용
```js
let i = 0;
let j = 8;

checkIAndJ: while (i < 4) {
  console.log(`i: ${i}`);
  i += 1;

  checkJ: while (j > 4) {
    console.log(`j: ${j}`);
    j -= 1;

    if (j % 2 === 0) continue checkJ;
    console.log(`${j} is odd.`);
  }
  console.log(`i = ${i}`);
  console.log(`j = ${j}`);
}

/*
-------Output-------
	i: 0

	// start checkj
	j: 8
	7 is odd.
	j: 7
	j: 6
	5 is odd.
	j: 5
	// end checkj
	
	i = 1
	j = 4
	
	i: 1
	i = 2
	j = 4
	
	i: 2
	i = 3
	j = 4
	
	i: 3
	i = 4
	j = 4
*/
```
## 📌 Reference
- https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Statements/continue
- "모던 자바스크립트 Deep Dive" by 이웅모, p.106-107