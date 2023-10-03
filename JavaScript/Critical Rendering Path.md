# Critical Rendering Path(CRP)
---
## 📌 Summary
> Browser Rendering Process에서 Parsing과 Render 과정을 거치는 일련의 단계를 말한다.
## 📌 Description
- CRP를 최적화하여 rendering을 향상시킬 수 있다.
	- 중요하지 않은 리소스의 다운로드를 지연 또는 비동기로 만들거나, 해당 데이터 파일의 크기를 줄여 페이지 로딩 속도를 개선할 수 있다.
	- 각 요청의 파일 크기와 필요한 요청 수를 최적화한다.
	- 다운로드의 우선순위를 지정하여 순서를 최적화하여 critical path length를 줄인다.
### ◉ Document Object Model(DOM)
- 노드의 수가 많을 수록 Rendering Path가 느려지기 때문에, 성능을 향상시키기 위해서는 노드 수를 줄이는 것이 좋다.
### ◉ CSS Object Model(CSSOM)
- CSS는 Render Blocking이다.
	- CSS 파일을 받고, parsing할 때까지 브라우저는 Rendering을 차단한다.
	- CSS는 규칙을 덮어쓸 수 있으므로 CSSOM이 완성될 때까지 콘텐츠가 rendering될 수 없기 때문에 Render Blocking이라고 한다.
	- 자식 노드가 부모의 스타일을 상속받는 것처럼, CSS는 'Cascade'되기 때문에 덮어쓸 수 있다.
- CSS가 parsing되면 CSSOM이 만들어지지만, parsing이 완전히 끝날 때까지 Render Tree를 만들 수 없다.
	- 이후에 parsing되어 덮어쓰는 CSS는 화면에 render될 수 없기 때문
- CSS Selector가 적을수록 성능이 향상된다.
	- Ex. `.foo {}` vs. `.bar .foo {}`
### ◉ Layout
- Layout은 DOM의 영향을 받는다.
	- 노드 수가 많을수록 layout 시간이 길어진다.
	- 노드 추가, 콘텐츠 변경, 박스 모델 스타일 업데이트 등 render tree가 수정될 때마다 layout이 발생한다.
- Layout의 이벤트 빈도와 지속 시간을 줄이려면 일괄적으로 업데이트하고, Box Moel 프로퍼티에 애니메이션 사용을 지양해야 한다.
### Paint
- Paint 시간은 Render Tree에 적용되는 업데이트에 따라 달라진다.
- 애니메이션 프레임에 걸리는 시간을 측정할 때는 layout과  re-paint 시간 모두를 고려해야 한다.
## 📌 Reference
- https://developer.mozilla.org/en-US/docs/Web/Performance/Critical_rendering_path