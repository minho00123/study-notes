---
Created: 2023-09-23 15:49
Modified: 2023-09-23 15:49
---
---
# position 프로퍼티
## Summary
> 요소의 위치를 정의할 때 사용하는 [[CSS(Cascading Style Sheet)]] 프로퍼티
## Syntax
```css
position: static;
position: relative;
position: absolute;
position: fixed;
position: sticky;

/* Global values */
position: inherit;
position: initial;
position: revert;
position: revert-layer;
position: unset;
```
## Description
- `top`, `right`, `bottom`, `left` 프로퍼티와 함께 사용하여 위치를 지정한다
### static
- `position` 프로퍼티의 기본값으로, 기본적인 요소의 배치 순서에 따라 배치된다.
- `top`, `right`, `bottom`, `left` 값을 사용할 수 없다.
- 부모 요소 내에 자식 요소로서 존재할 때는 **부모 요소의 위치를 기준으로 배치**된다.
### relative
- 기본 위치를 기준으로 `top`, `right`, `bottom`, `left` 값을 사용하여 위치를 이동시킨다.
- `top`, `right`, `bottom`, `left` 값을 사용할 수 있다는 점을 제외하면 `static`과 동일하게 동작한다.
### absolute
- 부모 요소 또는 가장 가까운 조상 요소(`static` 제외)를 기준으로 `top`, `right`, `bottom`, `left` 값만큼 이동한다.
- 부모/조상 요소가 `static`인 경우, HTML Document body 기준으로 `top`, `right`, `bottom`, `left` 값만큼 이동한다.
	- 부모 요소 기준으로 배치하려면 부모 요소에 `relative`를 정의하면 된다.
- Block-level 요소의 `width`는 콘텐츠에 맞게 변화되기 때문에 적절한 `width` 값을 지정해야 한다.
#### `relative` vs. `absolute`
- `relative`는 기본 위치를 기준으로 `top`, `right`, `bottom`, `left` 값만큼 이동하기 때문에 **무조건 부모 요소를 기준으로 위치**하게 된다.
- `absolute`는 부모 요소가 `static` 이외의 값이 지정되어 있을 경우에만 부모를 기준으로 위치하게 된다.
	- 부모/조상 요소가 모두 `static`인 경우, Document Body를 기준으로 위치한다.
- 따라서 `absolute`는 부모 요소의 영역을 벗어나 어디든지 위치할 수 있다.
### fixed
- 부모 요소와 관계없이 브라우저의 [[Viewport]]를 기준으로 `top`, `right`, `bottom`, `left` 값만큼 이동한다.
- 스크롤 되더라도 화면에서 사라지지 않고 항상 같은 곳에 위치한다.
- Block-level 요소의 `width`는 콘텐츠에 맞게 변화되기 때문에 적절한 `width` 값을 지정해야 한다.
## Reference
- https://poiemaweb.com/css3-position