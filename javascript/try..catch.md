# try catch
스크립트가 죽는걸 방지하고, 에러를 잡아서 더 합당한 무언가를 할 수 있게 한다.

### 문법
```java
try{

  // ..
  
}catch(e) {
  // 에러 핸들링
}
```
```java
try{
  JSON.parse('{age:30}'); // 잘못된 형식 에러발생 
}catch(err) {
  console.log(err.name); SyntaxError
  console.log(err.message); Unexpected token b in JSON at position 
}
```
## 'throw' 연산자 ( 던지다 )
자바스크립트는 Error, SyntaxError, RefrenceError, TypeError 등의 표준 에러 객체 관련 생성자를 지원한다.
```java
let error = new Error(message);
let error = new SyntaxError(message);
let error = new ReferenceError(message);
```
예시
```java
let json = '{ "age": 30 }'; // 불완전한 데이터

try {

  let user = JSON.parse(json); // <-- 에러 없음

  if (!user.name) {
    throw new SyntaxError("불완전한 데이터: 이름 없음"); // (*)
  }

  alert( user.name );

} catch(e) {
  alert( "JSON Error: " + e.message ); // JSON Error: 불완전한 데이터: 이름 없음
}
```
### 에러 다시 던지기 ( 예기치 않은 에러 )
try 안의 try
```java
function readData() {
  let json = '{ "age": 30 }';

  try {
    // ...
    blabla(); // 에러!
  } catch (e) {
    // ...
    if (!(e instanceof SyntaxError)) {
      throw e; // 알 수 없는 에러 다시 던지기
    }
  }
}

try {
  readData();
} catch (e) {
  alert( "External catch got: " + e ); // 예외 에러
}
```
# try..catch..finally
다음과 같은 상황에서 실행
1. 에러가 없는경우 : try 실행이 끝난 후
2. 에러가 있는경우 : catch 실행이 끝난 후
```java
try {
   ... 코드를 실행 ...
} catch(e) {
   ... 에러 핸들링 ...
} finally {
   ... 항상 실행 ...
}
```

### try..catch..finally 안의 변수는 지역 변수이다.
try 블록 안에서 선언한 변수는 블록 안에서만 유효한 지역변수 이다.

### finally와 return
```java
function func() {

  try {
    return 1;

  } catch (e) {
    /* ... */
  } finally {
    alert( 'finally' );
  }
}

alert( func() ); // finally 안의 alert가 실행되고 난 후, 실행됨
```
