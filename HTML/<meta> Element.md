---
Created: 2023-09-23 14:48
Modified: 2023-09-23 14:48
---
---
# \<meta\> Element
## Summary
> [[HTML(HyperText Markup Language) | HTML]] 문서의 생성자, 내용, 키워드와 같은 여러 정보르 검색엔진이나 브라우저에게 제공한다.
## Description
```html
<meta name="viewport" content="width=device-width, initial-scale=1.0" />
```
### Attributes
- `name`과 `content`를 함께 사용하여 name-value 쌍으로 [[Metadata]]를 제공할 수 있다.
	- `name`은 이름을, `content`는 값을 지정한다.
- `viewport`는 [[Viewport]]의 시작 크기에 대한 정보를 제공한다.
- `width`는 웹사이트를 렌더링할 viewport의 픽셀 너비를 정의한다.
	- 양의 정수 또는 `device-width` 값을 가질 수 있다.
- `initial-scale`: Device 너비와 viewport 크기 사이의 비율을 정의한다.
	- `0.0` ~ `10.0` 사이의 양의 정수를 값으로 가진다.
## Reference
- https://www.w3schools.com/html/html_head.asp
- https://developer.mozilla.org/en-US/docs/Web/HTML/Element/meta/name