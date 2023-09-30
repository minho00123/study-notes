---
Created: 2023-09-23 21:28
Modified: 2023-09-23 21:28
---

# 예약어(Reserved Word)
---
## Summary
> 식별자로 사용할 수 없는 [[키워드(Keyword)]]
## Description
- 프로그래밍 언어에서 사용되고 있거나 사용될 예정인 단어를 말한다.
- `async`는 어디에서나 식별자로 사용할 수 있다.
	- `await`은 `async` 본문 내에서만 예약어로 사용된다.
- `let`은 strict mode 또는 `const`, `let` 선언에서만 식별자로 사용할 수 없다.
### Types
| | | | | | | |
|---|---|---|---|---|---|---|
|as|async|await|break|case|catch|class|
|var, let, const|continue|debugger|default|delete|do|else|
|export|extends|false|finally|for|from|function|
|get|if|import|in|instanceof|new|null|
|of|return|set|static|super|switch|target|
|this|throw|true|try|typeof|void|while|
|with|yield||||||

## Reference
- "모던 자바스크립트 Deep Dive" by 이웅모, p.47
[[Lexical Grammar|]]