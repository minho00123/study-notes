# Browser Rendering Process
---
## 📌 Summary
> 서버에서 데이터를 받아 HTML, CSS, 자바스크립트를 브라우저 화면에 나타내는 과정
## 📌 Description
- 브라우저를 Rendering하는 Main Thread는 single-threaded로, 웹 페이지 또는 앱을 구성하는 대부분의 코드를 순차적으로 실행한다.
### ◉ Navigation
- 서버로부터 데이터 요청을 하는 과정
- DNS lookup, TCP handshake, TLS negotiation 등의 과정이 이루어진다.
### ◉ Response
- 서버로부터 데이터를 가져오는 과정
### ◉ Parsing
- Bytes -> Characters -> Tokens -> Nodes -> Object Model 순으로 진행된다.
- 네트워크를 통해 전달 받은 데이터를 Tree 구조로 변환한다.
	- HTML -> Document Object Model(DOM)
	- CSS -> CSS Object Model(CSSOM)
	- JavaScript -> Abstract Syntax Tree(AST)
- JavaScript Compilation: AST를 compiler가 bytecode로 변환시키는 일련의 과정
- Non-blocking resource(ex. image)는 브라우저가 parsing을 계속하지만 blocking resource(ex. `script` tag)는 parsing을 중단시킨다.
###  ◉ Render
- Parsing 단계에서 생성된 DOM과 CSSOM 트리는 Render Tree로 결합되어 화면에 나타나는 모든 요소의 레이아웃을 계산하고, 화면에 paint된다.
#### ▪︎ Style
-  DOM과 CSSOM을 Render Tree로 결합하는 단계
- `<head>` element 또는 `display: none`을 가지는 element는 Render Tree에 포함되지 않는다.
#### ▪︎ Layout
- Render Tree에 있는 모든 노드의 크기와 위치를 결정하는 단계
- 각 노드의 크기와 위치가 **처음** 결정되는 시점을 Layout이라 하고, Layout 이후의 **재계산**하는 것을 Reflow라고 한다.
#### ▪︎ Paint
- Layout 단계에서 계산된 각 상자를 실제 픽셀로 변환하는 단계
- 텍스트, 색상, 테두리, 그림자, 버튼, 이미지와 같은 요소를 화면에 그리는 작업이다.
## 📌 Reference
- https://developer.mozilla.org/en-US/docs/Web/Performance/How_browsers_work