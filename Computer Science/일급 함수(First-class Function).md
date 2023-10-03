# 일급 함수(First-class Function)
---
## 📌 Summary
> 함수가 변수처럼 취급될 때 해당 프로그래밍 언어의 함수를 일급 함수라 한다.
## 📌 Description
### ◉ 특징
1. 함수를 다른 함수에 argument로 전달할 수 있다.
2. 다른 함수에서 반환할 수 있다.
3. 변수에 값으로 할당할 수 있다.
## 📌 Example
- 변수에 함수 할당
``` jsx
const foo = () => {
  console.log("foobar");
};
foo(); // Invoke it using the variable
// foobar
```
- 함수를 argument로 전달
``` jsx
function sayHello() {
  return "Hello, ";
}
function greeting(helloMessage, name) {
  console.log(helloMessage() + name);
}
// Pass `sayHello` as an argument to `greeting` function
greeting(sayHello, "JavaScript!");
// Hello, JavaScript!
```
- 다른 함수에서 함수를 반환
``` jsx
function sayHello() {
  return () => {
    console.log("Hello!");
  };
}
```
## Reference
- 