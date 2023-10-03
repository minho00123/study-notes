
# 반환문(return)
---
## 📌 Summary
> 함수 실행을 종료하고, 함수 값을 반환한다.
## 📌 Description
- 함수는 실행 결과(자바스크립트에서 사용 가능한 모든 값)를 함수 외부로 반환(return)할 수 있다.
```js
function multiply(x, y) {
	return x * y; // 반환문
}

const result = multiply(3, 5);
console.log(result); // 15
```
- 반환문은 생략이 가능하다.
	- 함수는 함수 몸체의 마지막 문까지 실행한 후 암묵적으로 `undefined`를 반환한다.
- 반환문은 함수 몸체 내부에서만 사용할 수 있다. 전역에서 반환문을 사용하면 문법 에러(SyntaxError)가 발생한다.
	- 참고로 Node.js는 모듈 시스템에 의해 파일별로 독립적인 파일 스코프를 갖는다. 따라서 Node.js 환경에서는 파일의 가장 바깥 영역에 반환문을 사용해도 에러가 발생하지 않는다.
### 역할 두가지
1. 반환문은 함수의 실행을 중단하고 함수 몸체를 빠져나간다. 따라서 반환문 이후에 다른 문이 존재하면 그 문은 실행되지 않는다.
```js
function multiply(x, y) {
	return x * y;
	console.log('실행되지 않는다.');
}

console.log(multiply(3, 5)); // 15
```

2. 반환문은 `return` 키워드 뒤에 오는 표현식을 평가해 반환한다. `return` 키워드 뒤에 반환값으로 사용할 표현식을 명시적으로 지정하지 않으면 `undefined`가 반환된다.
## 📌 Reference
- "모던 자바스크립트 Deep Dive" by 이웅모, p.173-175