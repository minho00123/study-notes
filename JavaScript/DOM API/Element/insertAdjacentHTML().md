---
Created: 2023-09-22 08:14
Modified: 2023-09-22 08:14
---
---
# insertAdjacentHTML()
## Summary
> 문자열로 작성된 HTML 또는 XML을 parsing하고, 지정된 위치에 DOM 트리를 삽입한다.
## Syntax
```jsx
insertAdjacentHTML(position, text)
```
### Parameter
- `position`: 요소를 기준으로 위치를 나타내는 문자열. 다음 4가지 중 하나를 입력해야 한다:
	1. `"beforebegin"`: 요소 앞. 요소가 DOM 트리에 있고, 부모 요소가 있는 경우에만 유효하다.
	2. `"afterbegin"`: 첫 번째 자식 요소 앞에 위치한다.
	3. `"beforeend"`: 마지막 자식 요소 뒤에 위치한다.
	4. `"afterend"`: 요소 뒤. 요소가 DOM 트리에 있고, 부모 요소가 있는 경우에만 유효하다.
```html
<!-- beforebegin -->
<p>
  <!-- afterbegin -->
  foo
  <!-- beforeend -->
</p>
<!-- afterend -->
```
- `text`:  HTML 또는 XML을 [[Parsing]]하여 DOM tree에 삽입할 문자열

### Return Value
- None(`undefined`)
## Description
- 호출된 요소를 다시 parsing하지 않기 때문에 기존 요소를 손상시키지 않는다.
	- 따라서 직렬화의 추가 단계를 피하므로 `innerHTML`보다 훨씬 빠르다.
- HTML을 삽입할 때, 이스케이프 문자열을 사용하면 안된다.
- 일반 텍스트를 삽입할 때는 `Node.textContent` 또는 `Element.insertAdjacentText()`를 사용해야 한다.
	-  `insertAdjacentHTML`은 일반 텍스트를 HTML로 해석하지 않고 원시 텍스트로 인식한다.
## Examples
```jsx
const insert = document.querySelector("#insert");
insert.addEventListener("click", () => {
  const subject = document.querySelector("#subject");
  const positionSelect = document.querySelector("#position");
  subject.insertAdjacentHTML(
    positionSelect.value,
    "<strong>inserted text</strong>",
  );
});
const reset = document.querySelector("#reset");
reset.addEventListener("click", () => {
  document.location.reload();
});
```
## Reference
- https://developer.mozilla.org/ko/docs/Web/API/Element/insertAdjacentHTML