---
Created: 2023-09-24 09:59
Modified: 2023-09-24 09:59
---

# 주석(Comments)
---
## Description
- 코드에 대한 메모를 추가하는 데 사용된다.
	- 개발자는 이를 통해 코드를 더 쉽게 읽고 이해할 수 있다.
	- 코드를 비활성화시키기 때문에 디버깅 도구로도 사용할 수 있다.
### Line Comments(//)
- 한 줄을 주석할 때 사용한다.
```jsx
function comment() {
  // This is a one line JavaScript comment
  console.log("Hello world!");
}
comment();
```
### Block Comments(/\*\*\/)
- 여러 줄을 주석할 때 사용한다.
```jsx
function comment() {
  /* This comment spans multiple lines. Notice
     that we don't need to end the comment until we're done. */
  console.log("Hello world!");
}
comment();
```
### Hashbang Comments(#!)
- Line Comment와 비슷하지만 스크립트 또는 모듈 맨 앞에 위치해야 한다.
- `#!` 전에 White Space가 올 수 없다.
- 스크립트를 실행하는 데 사용할 특정 자바스크립트 인터프리터의 경로를 제공하는데 주로 사용된다.
- 자바스크립트 인터프리터를 지정하는 게 아니라면 Line Comment를 사용해야 한다.
## Reference
- https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Lexical_grammar#line_terminators
[[Lexical Grammar|]]