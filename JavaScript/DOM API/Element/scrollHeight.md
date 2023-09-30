---
Created: 2023-09-22 08:55
Modified: 2023-09-22 08:54
---
# scrollHeight
---
## Summary
> Overflow로 인해 화면에 나타나지 않는 content를 포함하여 element content의 높이를 측정하는 읽기 전용 property다.
## Description
- `scrollHeight` 값은 세로 스크롤바를 사용하지 않고 뷰포트의 모든 content에 맞추기 위해 element에 필요한 최소 높이와 같다.
- 값에 padding, psuedo-element(ex.`::before`) 은 포함하지만 border, margin, 또는 가로 스크롤바는 포함되지 않는다.
- [[scrollTop]]은 값이 반올림되지 않지만, `scrollHeight`는 반올림되기 때문에 스크롤 영역이 아래쪽으로 스크롤되었는지 확인하는 유일한 방법은 스크롤 양이 특정 임계값에 충분히 근접했는지 확인하는 것 뿐이다.
```jsx
Math.abs(element.scrollHeight - element.clientHeight - element.scrollTop) < 1;
```
## Examples
```html
<form name="registration">
  <p>
    <textarea id="rules">
Lorem ipsum dolor sit amet, consectetur adipiscing elit. Vestibulum at laoreet magna.
Aliquam erat volutpat. Praesent molestie, dolor ut eleifend aliquam, mi ligula ultrices sapien, quis cursus
neque dui nec risus. Duis tincidunt lobortis purus eu aliquet. Quisque in dignissim magna. Aenean ac lorem at
velit ultrices consequat. Nulla luctus nisi ut libero cursus ultrices. Pellentesque nec dignissim enim. Phasellus
ut quam lacus, sed ultricies diam. Vestibulum convallis rutrum dolor, sit amet egestas velit scelerisque id.
Proin non dignissim nisl. Sed mi odio, ullamcorper eget mattis id, malesuada vitae libero. Integer dolor lorem,
mattis sed dapibus a, faucibus id metus. Duis iaculis dictum pulvinar. In nisi nibh, dapibus ac blandit at, porta
at arcu. Pellentesque habitant morbi tristique senectus et netus et malesuada fames ac turpis egestas. Praesent
dictum ipsum aliquet erat eleifend sit amet sollicitudin felis tempus. Aliquam congue cursus venenatis. Maecenas
luctus pellentesque placerat. Mauris nisl odio, condimentum sed fringilla a, consectetur id ligula. Praesent sem
sem, aliquet non faucibus vitae, iaculis nec elit. Nullam volutpat, lectus et blandit bibendum, nulla lorem congue
turpis, ac pretium tortor sem ut nibh. Donec vel mi in ligula hendrerit sagittis. Donec faucibus viverra fermentum.
Fusce in arcu. Nullam at dignissim massa. Cras nibh est, pretium sit amet faucibus eget, sollicitudin in
ligula. Vivamus vitae urna mauris, eget euismod nunc. Aenean semper gravida enim non feugiat. In hac habitasse
platea dictumst. Cras eleifend nisl volutpat ante condimentum convallis. Donec varius dolor malesuada erat
consequat congue. Donec eu lacus ut sapien venenatis tincidunt. Quisque sit amet tellus et enim bibendum varius et
a orci. Donec aliquet volutpat scelerisque. Proin et tortor dolor. Ut aliquet, dolor a mattis sodales, odio diam
pulvinar sem, egestas pretium magna eros vitae felis. Nam vitae magna lectus, et ornare elit. Morbi feugiat, ipsum
ac mattis congue, quam neque mollis tortor, nec mollis nisl dolor a tortor. Maecenas varius est sit amet elit
interdum quis placerat metus posuere. Duis malesuada justo a diam vestibulum vel aliquam nisi ornare. Integer
laoreet nisi a odio ornare non congue turpis eleifend. Cum sociis natoque penatibus et magnis dis parturient montes,
nascetur ridiculus mus. Cras vulputate libero sed arcu iaculis nec lobortis orci fermentum.
    </textarea>
  </p>
  <p>
    <input type="checkbox" id="agree" name="accept" />
    <label for="agree">I agree</label>
    <input type="submit" id="nextstep" value="Next" />
  </p>
</form>
```

```css
#notice {
  display: inline-block;
  margin-bottom: 12px;
  border-radius: 5px;
  width: 600px;
  padding: 5px;
  border: 2px #7fdf55 solid;
}

#rules {
  width: 600px;
  height: 130px;
  padding: 5px;
  border: #2a9f00 solid 2px;
  border-radius: 5px;
}
```

```jsx
function checkReading() {
  if (checkReading.read) {
    return;
  }
  checkReading.read =
    this.scrollHeight - Math.round(this.scrollTop) === this.clientHeight;
  document.registration.accept.disabled = document.getElementById(
    "nextstep",
  ).disabled = !checkReading.read;
  checkReading.noticeBox.textContent = checkReading.read
    ? "Thank you."
    : "Please, scroll and read the following text.";
}

onload = () => {
  const oToBeRead = document.getElementById("rules");
  checkReading.noticeBox = document.createElement("span");
  document.registration.accept.checked = false;
  checkReading.noticeBox.id = "notice";
  oToBeRead.parentNode.insertBefore(checkReading.noticeBox, oToBeRead);
  oToBeRead.parentNode.insertBefore(document.createElement("br"), oToBeRead);
  oToBeRead.onscroll = checkReading;
  checkReading.call(oToBeRead);
};
```
## Reference
- https://developer.mozilla.org/en-US/docs/Web/API/Element/scrollHeight