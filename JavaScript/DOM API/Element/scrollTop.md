# scrollTop
---
## 📌 Summary
> Element 상단에서부터 가장 위에 표시되는 content까지의 거리 값을 가져오거나 설정한다.
## 📌 Description
- `scollTop` 값은 임의의 정수 값으로 설정할 수 있다.
	※ 주의사항
		- Element의 content가 세로 스크롤바를 생성하지 않으면 값은 0이다.
		- Element를 스크롤할 수 없으면 값은 0이다.
		- 음수 값을 할당하면 0으로 값이 설정된다.
		- Element의 최대값보다 큰 값을 설정하면 최대값으로 설정된다.
- 루트 요소(`<html>`)에 scrollTop이 사용되면 window의 scrollY가 반환된다.
![[Pasted image 20230922091259.png]]
## 📌 Examples
```html
<div id="container">
  <div id="scroller">
    <p>
      Far out in the uncharted backwaters of the unfashionable end of the
      western spiral arm of the Galaxy lies a small unregarded yellow sun.
      Orbiting this at a distance of roughly ninety-two million miles is an
      utterly insignificant little blue green planet whose ape-descended life
      forms are so amazingly primitive that they still think digital watches are
      a pretty neat idea.
    </p>
  </div>
</div>

<div id="output">scrollTop: 0</div>
```

```css
#scroller {
  overflow: scroll;
  height: 150px;
  width: 150px;
  border: 5px dashed orange;
}

#output {
  padding: 1rem 0;
}
```

```js
const scroller = document.querySelector("#scroller");
const output = document.querySelector("#output");

scroller.addEventListener("scroll", (event) => {
  output.textContent = `scrollTop: ${scroller.scrollTop}`;
});
```
## 📌 Reference
- https://developer.mozilla.org/en-US/docs/Web/API/Element/scrollTop