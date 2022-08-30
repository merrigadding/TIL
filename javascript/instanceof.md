# 'instanceof'로 클래스 확인하기
instanceof 연산자를 사용하면 객체가 특정 클래스에 속하는지 아닌지를 확인할 수 있다.<br>
상속 관계도 확인해준다.
```java
obj instanceof Class
```
obj가 Class에 속하거나 Class를 상속받는 클래스에 속하면 true를 반환한다.
```java
class Rabbit {}
let rabbit = new Rabbit();

// rabbit이 클래스 Rabbit의 객체인가요?
alert( rabbit instanceof Rabbit ); // true
```
```java
let arr = [1, 2, 3];
alert( arr instanceof Array ); // true
alert( arr instanceof Object ); // true
```

## 타입 확인을 위한 Object.prototype.toString
```java
let obj = {};

console.log(obj.toString()); // [object Object] 
```
toString의 구현 방식 때문에 [object Object]가 된다.
1. 숫자형 – [object Number]
2. 불린형 – [object Boolean]
3. null – [object Null]
4. undefined – [object Undefined]
5. 배열 – [object Array]

내장 객체의 타입 확인을 넘어서 타입을 문자열 형태로 받고 싶다면 instanceof대신, {}.toString.call을 사용할 수 있다.
```java
console.log({}.toString.call(1)) // [object Number]
console.log({}.toString.call(false)) // [object Boolean]
```
