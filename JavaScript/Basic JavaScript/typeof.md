---
Created: 2023-09-25 18:13
Modified: 2023-09-25 18:13
---
---
# typeof
## Summary
> 주어진 값의 자료형을 나타내는 문자열을 반환한다.
## Syntax
``` js
typeof operand;
typeof (operand);
```
### Parameter
- `operand`: 자료형을 가져올 객체 또는 원시값을 나타내는 표현식
### Return Value
|      Type      |   Result    |
|:--------------:|:-----------:|
|   Undefined    | `undefined` |
|      Null      |  `object`   |
|    Boolean     |  `boolean`  |
|     Number     |  `number`   |
|     BigInt     |  `bigint`   |
|     String     |  `string`   |
|     Symbol     |  `symbol`   |
|    Function    | `function`  |
| 다른 모든 객체 |  `object`   |
## Examples
``` js
// Numbers
typeof 37 === "number";
typeof 3.14 === "number";
typeof Math.LN2 === "number";
typeof Infinity === "number";
typeof NaN === "number"; // Despite being "Not-A-Number"
typeof Number(1) === "number"; // but never use this form!

typeof 42n === "bigint";

// Strings
typeof "" === "string";
typeof "bla" === "string";
typeof typeof 1 === "string"; // typeof always returns a string
typeof String("abc") === "string"; // but never use this form!

// Booleans
typeof true === "boolean";
typeof false === "boolean";
typeof Boolean(true) === "boolean"; // but never use this form!

// Symbols
typeof Symbol() === "symbol";
typeof Symbol("foo") === "symbol";
typeof Symbol.iterator === "symbol";

// Undefined
typeof undefined === "undefined";
typeof declaredButUndefinedVariable === "undefined";
typeof undeclaredVariable === "undefined";

// Objects
typeof { a: 1 } === "object";

// use Array.isArray or Object.prototype.toString.call
// to differentiate regular objects from arrays
typeof [1, 2, 4] === "object";

typeof new Date() === "object";

// The following is confusing. Don't use!
typeof new Boolean(true) === "object";
typeof new Number(1) === "object";
typeof new String("abc") === "object";

// Functions
typeof function () {} === "function";
typeof class C {} === "function";
typeof Math.sin === "function";
```
## Reference
- https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Operators/typeof
[[예약어(Reserved Word)|]]