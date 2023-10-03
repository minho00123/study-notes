# 표현식(Expression)
---
## 📌 Description
- 값으로 평가될 수 있는 문(Statement)이다. 
	- 여러 개의 문이 모여 문을 형성한다.
- 표현식이 평가되면 새로운 값을 생성하거나 기존 값을 참조한다.
- 표현식은 리터럴(Literals), 식별자(Identifier), 연산자(Operators), 함수 호출 등의 조함으로 이루어질 수 있다.
## 📌 Examples
```js
// 리터럴 표현식
10
'Hello'

// 식별자 표현식(선언이 이미 존재한다고 가정)
sum
person.name
arr[1]

// 연산자 표현식
10 + 20
sum = 10
sum !== 10

// 함수/메서드 호출 표현식(선언이 이미 존재한다고 가정)
square()
person.getName()
```
## 📌 Reference
-  "모던 자바스크립트 Deep Dive" by 이웅모, p.52-53