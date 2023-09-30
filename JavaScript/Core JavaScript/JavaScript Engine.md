---
Created: 2023-09-25 09:31
Modified: 2023-09-25 09:31
---

# JavaScript Engine
---
## Summary
> [[자바스크립트(JavaScript)]] 코드를 해석하는 컴퓨터 프로그램
## Description
- JavaScript 코드를 실행하고, 이를 컴퓨터가 이해할 수 있는 언어로 변환하는 컴퓨터 프로그램
- 브라우저마다 다른 자바스크립트 엔진을 가진다:
	- Google Chrome - V8 engine
	- Firefox - SpiderMonkey
	- Safari - JavaScriptCore
	- IE - Chakra
- 모든 자바스크립트 엔진에는 일반적으로 Call Stack과 Heap이 포함된다.
	- Call Stack은 코드가 실행되는 장소이다.
	- Heap은 애플리케이션에 필요한 모든 객체를 저장한다.
- 자바스크립트 코드가 엔진에 전달되면 [[Parsing]] -> AST -> Machine Code 순으로 진행된다.
- 실행은 [[실행 컨텍스트(Execution Context)]]를 사용하여 엔진의 Call Stack에서 발생한다.
### JavaScript Runtime
* 런타임 환경의 예시로 Browser Runtime과 Node.js가 있다.
* Brower Runtime 환경은 웹 브라우저가 실행되면 작동한다.
	* DOM에 대한 접근을 제공한다.
- Node.js는 브라우저 외부에서 JavaScript를 실행하기 위한 Server-side 런타임 환경을 제공한다.
	- 브라우저 외부에서 JS를 실행하기 때문에 Web API에 접근할 수 없다.
	- 대신 Node.js 런타임 환경은 이를 C++ 바인딩 및 thread pool이라는 것으로 대체한다.
- 자바스크립트를 실행하는 데 필요한 모든 구성 요소를 가진다: JavaScript Engine, Web API, Caback Queue
#### Web API
- 자바스크립트 엔진에 제공되지만, 자바스크립트 언어와는 다르다.
- 브라우저를 통해 자바스크립트 엔진에 접근할 수 있고, 데이터에 접근하거나 브라우저 기능을 향상시키는데 도움이 된다.
	Ex. DOM, Fetch API
#### Callback Queue
- 실행할 준비가 된 콜백 함수가 있다.
	- 콜 스택이 비어있을 때 전달된다.
## Reference
- https://www.freecodecamp.org/news/how-javascript-works-behind-the-scenes/