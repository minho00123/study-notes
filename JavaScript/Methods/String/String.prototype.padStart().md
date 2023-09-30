---
Created: 2023-09-27 16:34
Modified: 2023-09-27 16:34
---
---
# String.prototype.padStart()
## Summary
> 문자열이 지정된 길이가 될 때까지 다른 문자열 처음부터 채운다.
## Syntax
```js
padStart(targetLength[, padString])
```
### Parameter
- `targetLength`: 결과 문자열의 길이. 값이 `str.length`보다 작거나 같으면 `str`을 그대로 반환한다.
- `padString`: 채울 문자열을 지정한다.  `padString`응응 `targetLength`보다 길면 끝부터 잘린다. 기본값은 "space"다.
### Return Value
- `padString`이 처음부터 적용된 `targetLength`의 문자열
## Examples
### Basic example
```js
"abc".padStart(10); // "       abc"
"abc".padStart(10, "foo"); // "foofoofabc"
"abc".padStart(6, "123465"); // "123abc"
"abc".padStart(8, "0"); // "00000abc"
"abc".padStart(1); // "abc"
```
### Fixed width string number conversion
```js
// JavaScript version of: (unsigned)
// printf "%0*d" width num
function leftFillNum(num, targetLength) {
  return num.toString().padStart(targetLength, "0");
}

const num = 123;
console.log(leftFillNum(num, 5)); // "00123"
```
## Reference
- https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/String/padStart