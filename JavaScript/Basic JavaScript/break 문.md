---
Created: 2023-09-25 20:03
Modified: 2023-09-25 20:02
---

# break 문
---
## Description
- [[반복문(Loop Statement)]], [[조건문(Conditional Statement)|switch 문]], [[label 문]]의 코드 블록을 탈출한다.
- 어떠한 경우라도 스크립트 최상단에서는 사용할 수 없다.
## Syntax
```js
break [label];
```

- `label`: 레이블에 연결한 식별자. 반복문 또는 `switch`문이 아니면 필수로 작성해야 한다.
### Error
- 반복문 내에 중첩된 함수에서 `break`문을 사용하면 에러가 발생한다.
```js
function testBreak(x) {
  let i = 0;

  while (i < 6) {
    if (i === 3) {
      (() => {
        break;
      })();
    }
    i += 1;
  }

  return i * x;
}

testBreak(1); // SyntaxError: Illegal break statement
```
- `label`문에서도 중첩된 함수 안에 사용하면 에러가 발생한다.
```js
block1: {
  console.log("1");
  (() => {
    break block1; // SyntaxError: Undefined label 'block1'
  })();
```
## Examples
```js
outer_block: {
  inner_block: {
    console.log("1");
    break outer_block; // inner_block과 outer_block 둘다 빠져나옴
    console.log(":-("); // 건너뜀
  }
  console.log("2"); // 건너뜀
}
```
## Reference
- "모던 자바스크립트 Deep Dive" by 이웅모, p.104-105
- https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Statements/break
[[제어문(Control Flow Statement)|]]