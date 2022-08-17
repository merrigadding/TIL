# new Function 문법
```java
let func = new Function ([arg1, arg2, ...argN], functionBody);
```

어떤 문자열도 함수로 바꿀 수 있다.
```java
let sayHi = new Function('alert("Hello")');

sayHi(); // Hello
```
