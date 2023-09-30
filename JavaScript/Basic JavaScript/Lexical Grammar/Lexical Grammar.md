---
Created: 2023-09-24 09:07
Modified: 2023-09-24 09:07
---

# Lexical Grammar
---
## Description
- [[자바스크립트(JavaScript)]]의 Source Text는 일련의 문자로 이루어져 있다.
	- 인터프리터는 Source Text를 이해하기 위해 [[Parsing]]을 진행한다.
 - Parsing의 초기 단계를 Lexical Analysis라고 한다.
	 - Source Text를 왼쪽에서 오른쪽으로 스캔하고, [[토큰(Token)]], [[Line Terminator]], [[주석(Comments)]] 또는 [[공백(White Space)]]과 같은 일련의 Input Element로 변환된다.
	 - 이 단계 이후에 인터프리터는 중요하지 않은 공백과 주석을 제거한다.
## Reference
- https://tc39.es/ecma262/multipage/ecmascript-language-lexical-grammar.html
- https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Lexical_grammar#line_terminators