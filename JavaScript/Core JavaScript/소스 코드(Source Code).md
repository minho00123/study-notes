---
Created: 2023-09-25 13:13
Modified: 2023-09-25 13:13
---
# 소스 코드(Source Code)
---
## Summary
- 프로그래머가 만든 컴퓨터 프로그램의 기본 요소
## Description
- JavaScript에는 4가지 타입의 소스 코드가 있다.
	- 소스 코드를 구분하는 이유는 타입에 따라 실행 컨텍스트를 생성하는 과정과 관리하는 내용이 다르기 때문이다.
- [[JavaScript Engine]]은 소스 코드를 "평가"와 "실행" 과정으로 나누어 처리한다.
	- 평가 과정에서는 실행 컨텍스트를 생성하고  변수, 함수 등의 선언문만 먼저 실행하여 스코프(Environment Record)에 등록한다.
	- 평가 과정이 끝나면 선언문을 제외한 소스 코드가 순차적으로 실행되어 런타임이 시작된다.
		- 소스 코드를 실행하기 위해 필요한 변수나 함수를 실행 컨텍스트가 관리하는 스코프에서 검색하여 가져온다.
		- 만약 값의 변화가 일어나면 소스코드의 실행 결과를 다시 실행 컨텍스트가 관리하는 스코프에 등록한다.
### Types of Source Code
#### 전역 코드(Global Code)
- 전역에 존재하는 소스 코드; Global Execution Context를 생성한다.
- 전역 변수를 관리하기 위해 Global Scope를 생성한다.
- [[var]] 키워드로 선언된 전역 변수와 함수 선언문으로 정의된 전역 함수를 [[전역 객체]]의 프로퍼티와 메서드로 바인딩한다.
#### 함수 코드(Function Code)
- 함수 내부에 존재하는 소스 코드
- Local Scope를 생성하고 지역 변수, 매개변수, arguments 객체를 관리한다.
- 생성한 Local Scope를 Global Scope에서 시작하는 스코프 체인의 일원으로 연결한다.
#### eval 코드(eval Code)
- [[eval]] 함수에 인수로 전달되어 실행되는 소스코드
- strict mode에서 자신만의 독자적인 Scope를 생성한다.
#### 모듈 코드(Module Code)
- 모듈 내부에 존재하는 소스코드
- 모듈별로 독립적인 Module Scope를 생성한다.
## Reference
- https://262.ecma-international.org/14.0/
- "모던 자바스크립트 Deep Dive" by 이웅모, p.359-360