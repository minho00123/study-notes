# label 문
---
## 📌 Description
- break 문이나 continue 문을 사용해 특정 위치의 반복문(Loop Statement)에서 작업을 멈추고, 다시 수행할지 알려 준다.
- 원하는 식별자로 구문 앞에 레이블을 추가한다.
- 중첩된 `for`문 외부로 탈출할 때 유용하지만 그 밖의 경우에는 일반적으로 권장하지 않는다.
	- 프로그램의 흐름이 복잡해져서 가독성이 떨어지고, 오류를 발생시킬 가능성이 높다.
## 📌 Syntax
```js
label:
  statement;
```
## 📌 Examples
```js
var itemsPassed = 0;
var i, j;

top: for (i = 0; i < items.length; i++) {
  for (j = 0; j < tests.length; j++) {
    if (!tests[j].pass(items[i])) {
      continue top;
    }
  }

  itemsPassed++;
}
```

```js
var allPass = true;
var i, j;

top: for (i = 0; items.length; i++)
  for (j = 0; j < tests.length; i++)
    if (!tests[j].pass(items[i])) {
      allPass = false;
      break top;
    }
```
## 📌 Reference
- https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Statements/label