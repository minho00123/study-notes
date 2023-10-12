# strict mode
---
## 📌 Summary
> 자바스크립트 언어의 문법을 더 엄격히 적용하여 오류를 발생시킬 가능성이 높거나 자바스크립트 엔진의 최적화 작업에 문제를 일으킬 수 있는 코드에 대해 명시적인 에러를 발생시킨다.
## 📌 Description
- 암묵적 전역(implicit global): 전역 객체의 프로퍼티를 마치 전역 변수처럼 사용하는 것
- ESLint 같은 린트 도구를 사용해도 strict mode와 유사한 효과를 얻을 수 있다.
> 💡 **린트 도구**
> 정적 분석(static analysis) 기능을 통해 소스코드를 실행하기 전에 소스코드를 스캔하여 문법적 오류만이 아니라 잠재적 오류까지 찾아내고 오류의 원인을 리포팅해주는 도구
### ◉ strict mode의 적용
- 전역의 선두 또는 함수 몸체의 선두에 `'use strict';`를 추가한다.
- 전역의 선두에 추가하면 스크립트 전체에 strict mode가 적용된다.
```js
'use strict';

function foo() {
	x = 10; // ReferenceError: x is not defined
}
foo();
```
- 함수 몸체의 선두에 추가하면 해당 함수와 중첩 함수에 strict mode가 적용된다.
```js
function foo() {
	'use strickt';

	x = 10; // ReferenceError: x is not defined
}
foo();
```
- 코드의 선두에 `'use strict';`를 위치시키지 않으면 strict mode가 제대로 동작하지 않는다.
```js
function foo() {
	x = 10; // 에러 발생 X
	'use strict';
}
foo();
```
### ◉ 주의사항
#### ▪︎ 전역에 strict mode를 적용하는 것은 피하자
- 전역에 적용한 strict mode는 스크립트 단위로 적용되기 떄문에 다른 스크립트에 영향을 주지 않는다.
- 하지만 strict mode 스크립트와 non-strict mode 스크립트를 혼용하는 것은 오류를 발생시킬 수 있다.
- 특히 외부 서드파티 라이브러리를 사용하는 경우 라이브러리가 non-strict mode인 경우도 있기 때문에 전역에 strict mode를 적용하는 것은 바람직하지 않다.
- 이러한 경우 즉시 실행 함수로 스크립트 전체를 감싸서 스코프를 구분하고 즉시 실행 함수의 선두에 strict mode를 적용한다.
```js
(function () {
	'use strict';

	// Do something...
}());
```
#### ▪︎ 함수 단위로 strict mode를 적용하는 것은 피하자
- 어떤 함수는 strict mode를 적용하고 어떤 함수는 적용하지 않는 것은 바람직하지 않으며 모든 함수에 일일이 strict mode를 적용하는 것은 번거로운 일이다.
- 그리고 strict mode가 적용된 함수가 참조할 함수 외부의 컨텍스트에 strict mode를 적용하지 않는다면 이 또한 문제가 발생할 수 있다.
```js
(function () {
	// non-strict mode
	var let = 10; // 에러 발생 X

	function foo() {
		'use strict';

		let = 20; // SyntaxError: Unexpected strict mode reserved word
	}
	foo();
}());
```
- 따라서 strict mode는 즉시 실행 함수로 감싼 스트립트 단위로 적용하는 것이 바람직하다.
### ◉ strict mode가 발생시키는 에러
#### ▪︎ 암묵적 전역
- 선언하지 않은 변수를 참조하면 `ReferenceError`가 발생한다.
```js
(function () {
	'use strict';

	x = 1;
	console.log(x); // ReferenceError: x is not defined
}());
```
#### ▪︎ 변수, 함수, 매개변수의 삭제
- `delete` 연사자로 변수, 함수, 매개변수를 삭제하면 `SyntaxError`가 발생한다.
```js
(function () {
	'use strict';

	var x = 1;
	delete x; // SyntaxError: Delete of an unqualified identifier in strict mode

	function foo(a) {
		delete a; // SyntaxError: Delete of an unqualified identifier in strict mode
	}
	delete foo; // SyntaxError: Delete of an unqualified identifier in strict mode
}());
```
#### ▪︎ 매개변수 이름의 중복
- 중복된 매개변수 이름을 사용하면 `SyntaxError`가 발생한다.
```js
(function () {
	'use strict';

	// SyntaxError: Duplicate parameter name not allowd in this context
	function foo(x, x) {
		return x + x;
	}
	console.log(foo(1, 2));
}());
```
#### ▪︎ with 문의 사용
- `with` 문을 사용하면 `SyntaxError`가 발생한다.
- `with` 문은 전달된 객체를 스코프 체인에 추가한다.
- `with` 문은 동일한 객체의 프로퍼티를 반복해서 사용할 때 객체 이름을 생략할 수 있어서 코드가 간단해지는 효과가 있지만 성능과 가독성이 나빠지는 문제가 있다.
- 따라서 `with` 문은 사용하지 않는 것이 좋다.
```js
(function () {
	'use strict';

	// SyntaxError: Strict mode code may not include a with statement
	with({ x: 1 }) {
		console.log(x);
	}
}());
```
### ◉ strict mode 적용에 의한 변화
#### ▪︎ 일반 함수의 this
- strict mode에서 함수를 일반 함수로서 호출하면 `this`에 `undefined`가 바인딩된다.
- 생성자 함수가 아닌 일반 함수 내부에서는 `this`를 사용할 필요가 없기 때문이다.
- 이때 에러는 발생하지 않는다.
```js
(function () {
	'use strict';

	function foo() {
		console.log(this); // undefined
	}
	foo();

	function Foo() {
		console.log(this); // Foo
	}
	new Foo();
}());
```
#### ▪︎ arguments 객체
- strict mode에서는 매개변수에 전달된 인수를 재할당하여 변경해도 `arguemtns` 객체에 반영되지 않는다.
```js
(function () {
	'use strict';
	// 매개변수에 전달된 인수를 재할당하여 변경
	a = 2;

	// 변경된 인수가 arguments 객체에 반영되지 않는다.
	console.log(arguments); // { 0: 1, length: 1 }
}(1));
```
## 📌 Reference
- "모던 자바스크립트 Deep Dive" by 이웅모, p.313-319