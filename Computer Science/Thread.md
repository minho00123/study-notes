# Thread
---
## 📌 Summary
> 코드를 실행할 수 있는 각각의 단위를 thread라고 한다.
## 📌 Description
- Process 내에서 작업을 실행하는 경로를 말한다.
- Process의 일부 속성을 가지기 때문에 lightweight process라고도 한다.
- 각 Process는 서로 다른 메모리 주소를 가지지만, thread는 같은 메모리를 공유한다.
	-  따라서 여러 개의 thread가 하나의 프로그램에서 협업하고 효율적으로 작업할 수 있다.
- Thread는 운영 체제가 생성 및 관리한다.
- Multi-threading을 지원하는 운영 체제는 여러 개의 thread로 구성될 수 있다. 이를 multi-thread라고 한다.
- 브라우저에서는 Main Thread를 이용하여 웹 페이지 또는 앱을 구성하는 대부분의 코드를 실행한다.
## 📌 Reference
- https://developer.chrome.com/blog/inside-browser-part1/
- https://www.geeksforgeeks.org/thread-in-operating-system/