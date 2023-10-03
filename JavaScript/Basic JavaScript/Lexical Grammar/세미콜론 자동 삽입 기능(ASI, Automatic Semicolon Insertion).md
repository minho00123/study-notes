# 세미콜론 자동 삽입 기능(ASI, Automatic Semicolon Insertion)
---
## 📌 Description
- 자바스크립트에서는 다음과 같은 문(Statement)의 정의 끝에 세미콜론(;)을 붙인다:
	- var, let, const
	- 표현식(Expression Statement)
	- do...while
	- continue, break, return, throw
	- debugger
	- Class field declaration (`public` or `private`)
	- `import`, `export`
- 하지만  자바스크립트 엔진이 소스코드를 해석할 때, 문의 끝이라고 예측되는 지점에 세미콜론을 자동으로 붙여준다.
## 📌 Reference
- "모던 자바스크립트 Deep Dive" by 이웅모, p.55
- https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Lexical_grammar