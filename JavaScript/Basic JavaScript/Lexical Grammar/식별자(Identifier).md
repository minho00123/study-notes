# 식별자(Identifier)
---
## 📌 Summary
> 어떤 값을 구별하여 식별할 수 있는 고유한 이름
## 📌 Description
- 값은 메모리 공간에 있기 때문에 식별자는 특정 값이 저장된 메모리 주소를 저장한다.
	- 따라서 메모리 상에 존재하는 특정 값을 식별할 수 있는 이름을 식별자라 할 수 있다.
- 문자열과 식별자는 다르다.
	- 문자열은 데이터이고, 식별자는 코드의 일부다.
	- 식별자를 문자열로 변환할 수 없지만, 문자열은 식별자로 Parsing할 수 있다.
- 선언하지 않은 식별자에 접근하면 `ReferenceError`(참조 에러)가 발생한다.
- 모든 식별자는 실행 컨텍스트(Execution Context)에 등록된다.
### ◉ 식별자 네이밍 규칙
1. 대소문자를 구분한다.
2. 유니코드 문자, $, \_, 숫자(0-9)를 포함할 수 있지만 숫자로 시작할 수는 없다.
3. 예약어(Reserved Word)|예약어는 식별자로 사용할 수 없다.
## 📌 Reference
- "모던 자바스크립트 Deep Dive" by 이웅모, p. 38-39, 47-49
- https://developer.mozilla.org/en-US/docs/Web/Javahttps://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Lexical_grammarScript/Reference/Lexical_grammar