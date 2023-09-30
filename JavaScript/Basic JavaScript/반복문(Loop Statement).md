---
Created: 2023-09-25 19:49
Modified: 2023-09-25 19:48
---

# 반복문(Loop Statement)
---
## Description
- 조건식의 평가 결과가 참이 경우 코드 블록을 실행한다. 그 후 조건식을 다시 평가하여 여전히 참인 경우 코드 블록을 다시 실행한다. 이는 조건식이 거짓일 때까지 반복된다.
### for 문
- 조건식이 거짓으로 평가될 때까지 코드 블록을 반복 실행한다.
```js
for ([initialization]; [condition]; [afterthought])
   statement
```
- `initialization`: 표현식 또는 변수 선언이 반복이 진행되기 전에 한 번만 평가된다. 일반적으로 counter 변수를 선언할 때 사용한다.
- `condition`: 매 반복마다 평가할 식. 평가가 `true`면 `statement`를 실행한다. `false`면 반복을 종료하고 다음 식으로 넘어간다.
- `afterthought`: 반복이 끝나고 평가되는 표현식. 다음 조건식을 평가하기 전에 실행된다. 일반적으로 counter 변수를 증가시킬 때 사용한다. (증감식)
- `statement`: 조건의 평가가 `true`일 때 실행하는 문
### while 문
- 조건문이 `true`면 코드 블록을 계속해서 실행한다.
```js
while (condition) {
  statement
}
```
- `condition`: 반복이 시작되기 전 `true`/`false`를 판단한다. `false`면 반복문이 종료된다.
- `statement`: `condition`이 `true`일 때만 실행된다.
### do...while 문
- 코드 블록을 먼저 실행하고 조건식을 평가한다. 따라서 코드 블록은 무조건 한 번 이상 실행된다.
```js
do {
  statement;
} while (condition);
```

- `statement`: 무조건 한 번은 실행되고, 조건식이 `true`면 다시 실행된다.
- `condition`: 반복문이 실행될 때마다 평가되는 식

※ `for`문은 반복 횟수가 명확할 때 주로 사용하고 `while`문은 반복 횟수가 불명확할 때 주로 사용한다.
## Examples
### for 문
```js
for (let i = 0; i < 9; i++) {
  console.log(i);
  // more statements
}
```
### while 문
```js
let n = 0;
let x = 0;

while (n < 3) {
  n++;
  x += n;
}
```
### do...while 문
```js
let result = "";
let i = 0;
do {
  i += 1;
  result += `${i} `;
} while (i > 0 && i < 5);
// Despite i === 0 this will still loop as it starts off without the test

console.log(result);
```
## Reference
- "모던 자바스크립트 Deep Dive" by 이웅모, p.100-103