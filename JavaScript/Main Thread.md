---
Created: 2023-09-22 14:36
Modified: 2023-09-22 14:36
---
# Main Thread
---
## Summary
> 브라우저가 사용자 이벤트와 paint를 처리하는 single thread
## Description
- 하나의 thread를 사용하여 모든 JavaScript를 실행하고, 레이아웃, reflow, 그리고 garbage collection을 수행한다.
	- JavaScript 함수가 오래 지속될 경우, thread를 차단하여 페이지가 응답하지 않을 수 있다.
- 모던 자바스크립트는 [[Web Worker]]를 사용하여 추가적인 thread를 생성할 수 있다.
	- 생성된 thread는 독립적으로 실행되고 서로 통신한다.
## Reference
- https://developer.mozilla.org/en-US/docs/Glossary/Main_thread