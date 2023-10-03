# 타입 변환(Type Conversion)
---
## 📌 Summary
> 기존의 원시 값을 사용해 다른 타입의 새로운 원시 값을 생성하는 것
## 📌 Description
### ◉ 명시적 타입 변환(explicit coercion) / 타입 캐스팅(type casting)
- 개발자가 의도적으로 값의 타입을 변환하는 것
- 표준 빌트인 생성자 함수(String, Number, Boolean)를 new 연산자 없이 호출하는 방법과 빌트인 메서드를 사용하는 방법, 그리고 암묵적 타입 변환을 이용하는 방법이 있다.
#### ▪︎ 문자열 타입으로 변환
##### 1. `String` 생성자 함수를 `new` 연산자 없이 호출하는 방법
```js
// Number -> String
String(1);             // "1"
String(NaN);           // "NaN"
String(Infinity);      // "Infinity"
// 불리언 타입 => 문자열 타입
String(true);          // "true"
String(false);         // "false"
```

##### 2. `Object.prototype.toString` 메서드를 사용하는 방법
```js
// Number -> String
(1).toString();        // "1"
(NaN).toString();      // "NaN"
(Infinity).toString(); // "Infinity"

// Boolean -> String
(true).toString();     // "true"
(false).toString();    // "false"
```
##### 3. 문자열 연결 연산자를 이용하는 방법
```js
// Number -> String
1 + '';                // "1"
NaN + '';              // "NaN"
Infinity + '';         // "Infinity"

// Boolean -> String
true + '';             // "true"
false + '';            // "false"
```
#### ▪︎ 숫자 타입으로 변환
##### 1. `Number` 생성자 함수를 `new` 연산자 없이 호출하는 방법
```js
// String -> Number
Number('0');         // 0
Number('-1');        // -1
Number('10.53');     // 10.53

// Boolean -> Number
Number(true);        // 1
Number(false);       // 0
```
##### 2. `parseInt`, `parseFloat` 함수를 사용하는 방법(문자열만 숫자 타입으로 변환 가능)
```js
// String -> Number
parseInt('0');       // 0
parseInt('-1');      // -1
parseFloat('10.53'); // 10.53
```
##### 3. `+` 단항 산술 연산자를 이용하는 방법
```js
// String -> Number
+'0';                // 0
+'-1';               // -1
+'10.53';            // 10.53

// Boolean -> Number
+true;               // 1
+false               // 0
```
##### 4. `*` 산술 연산자를 이용하는 방법
```js
// String -> Number
'0' * 1;             // 0
'-1' * 1;            // -1
'10.53' * 1;         // 10.53

// Boolean -> Number 
true * 1;            // 1
false * 1;           // 0
```
#### ▪︎ 불리언 타입으로 변환
##### 1. `Boolean` 생성자 함수를 `new` 연산자 없이 호출하는 방법
```js
// String -> Boolean
Boolean('x');       // true
Boolean('');        // false
Boolean('false')    // true

// Number -> Boolean
Boolean(0);         // false
Boolean(1);         // true
Boolean(NaN);       // false
Boolean(Infinity);  // true

// null -> Boolean
Boolean(null);      // false

// undefined -> Boolean
Boolean(undefined); // false

// Object -> Boolean
Boolean({});        // true
Boolean([]);        // true
```
##### 2. `!` 부정 논리 연산자를 두 번 사용하는 방법
```js
// String -> Boolean
!!'x';              // true
!!'';               // false
!!'false'           // true

// Number -> Boolean
!!0;                //false
!!1;                // true
!!NaN;              // false
!!Infinity;         // true

// null -> Boolean
!!null;             // false

// undefined -> Boolean
!!undefined;        // false

// Object -> Boolean
!!{};               // true
!![];               // true
```
### ◉ 암묵적 타입 변환(implicit coercion) / 타입 강제 변환(type coercion)
- 개발자의 의도와는 자바스크립트 엔진에 의해 암묵적으로 타입이 자동으로 변환되는 것
- 기존 변수 값을 재할당하여 변경하는 것이 아니라, 값을 암묵적 타입 변환하여 새로운 타입의 값을 만들어 단 한 번 사용하고 버린다.
```js
// 피연산자가 모두 문자열 타입이어야 하는 문맥
'10' + 2 // '102'

// 피연산자가 모두 숫자 타입이어야 하는 문맥
5 * '10' // 50

// 피연산자 또는 표현식이 불리언 타입이어야 하는 문맥
!0 // true
```
- 자바스크립트는 가급적 에러를 발생시키지 않도록 암묵적 타입 변환을 통해 표현식을 평가한다.
- 암묵적 타입 변환이 발생하면 원시 타입 중 하나로 타입을 자동 변환한다.
#### ▪︎ 문자열 타입으로 변환
- `+` 연산자는 피연산자 중 하나 이상이 문자열이면 문자열 연결 연산자로 동작한다.
```js
// Number
0 + ''              // "0"
-0 + ''             // "0"
1 + ''              // "1"
-1 + ''             // "-1"
NaN + ''            // "NaN"
Infinity + ''       // "Infinity"
-Infinity + ''      // "-Infinity"

// Boolean
true + ''           // "true"
false + ''          // "false"

// null
null + ''           // "null"

// undefined
undefined + ''      // "undefined"

// Symbol
(Symbol()) + ''     // TypeError: Cannot convert a Symbol value to a string

// Object
({}) + ''           // "[object Object]"
Math + ''           // "[object Math]"
[] + ''             // ""
[10, 20] + ''       // "10,20"
(function(){}) + '' // "function(){}"
Array + ''          // "function Array() { [native code] }"
```
#### ▪︎ 숫자 타입으로 변환
- 산술 연산자 중, `+`를 제외한 `-`, `*`, `/` 연산자는 암묵적으로 숫자 타입으로 변환한다.
- 이때 피연산자를 숫자 타입으로 변환할 수 없는 경우는 산술 연산을 수행할 수 없으므로 표현식의 평가 결과는 `NaN`이 된다.
- 자바스크립트 엔진은 비교 연산자 표현식을 평가하기 위해 비교 연산자의 피연산자 중에서 숫자 타입이 아닌 피연산자를 숫자 타입으로 암묵적 타입 변환한다.
```js
'1' > 0 // true
```
- `+` 단항 연산자는 피연산자가 숫자 타입의 값이 아니면 숫자 타입의 값으로 암묵적 타입 변환을 수행한다.
```js
// String
+''            // 0
+'0'           // 0
+'1'           // 1
+'string'      // NaN

//  Boolean
+true          // 1
+false         // 0

// null
+null          // 0

// undefined
+undefined     // NaN

// Symbol
+Symbol() // TypeError: Cannot convert a Symbol value to a number

// Object
+{}             // NaN
+[]             // 0
+[10, 20]       // NaN
+(function(){}) // NaN
```
#### ▪︎ 불리언 타입으로 변환
- 자바스크립트 엔진은 조건식의 평가 결과를 불리언 타입으로 암묵적 타입 변환한다.
- 이때 자바스크립트 엔진은 불리언 타입이 아닌 값을 Truthy 값(참으로 평가되는 값) 또는 Falsy 값(거짓으로 평가되는 값)으로 구분한다.
- 아래는 `false`로 평가되는 Falsy 값이다:
	- `false`
	- `undefined`
	- `null`
	- `0`, `-0`
	- `NaN`
	- `''`(빈 문자열)
```js
// 전달받은 인수가 Falsy 값이면 true, Truthy 값이면 false를 반환한다.
function isFalsy(v) {
	return !v;
}

// 전달받은 인수가 Truthy 값이면 true, Falsy 값이면 false를 반환한다.
function isTruthy(v) {
	return !!v;
}

// 모두 true를 반환한다.
isFalsy(false);
isFalsy(undefined);
isFalsy(null);
isFalsy(0);
isFalsy(NaN);
isFalsy('');

// 모두 true를 반환한다.
isTruthy(true);
isTruthy('0');
isTruthy({});
isTruthy([]);
```
## 📌 Reference
- "모던 자바스크립트 Deep Dive" by 이웅모, p.108-118