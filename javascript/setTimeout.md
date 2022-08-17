# setTimeout()
setTimeout이란 일정 시간 후에 특정 코드, 함수를 의도적으로 지연한 뒤 실행하고 싶을 때 사용하는 함수로 setTimeout()을 사용한다.
```java
// 문법
let timerId = setTimeout(func|code, [delay], [arg1], [arg2], ...)
```
```java
setTimeout(function() {
  console.log('Works!');
}, 3000);

//  3초 후 함수가 실행됨
```
### 언제 사용하는가 ?
  * 접속 후 몇 초 후에 팝업 또는 배너창 띄우기
  * 방문자의 스크롤이 브라우저 일정 위치에 올 경우 몇 초 뒤에 애니메이션 실행
  * 검색창 또는 일부 섹션 몇 초 뒤에 사라질 경우
  * 방문자 접속 후 20-30초가 지난 뒤 메일 구독을 신청하는 팝업창을 띄울 경우


*함수를 실행하지 말고 넘기라.*
```java
// 잘못된 코드
setTimeout(sayHi(), 1000); // sayHi() -> sayHi 로 
```

### clearTimeout으로 스케줄링 취소하기
setTimeout을 호출하면 '타이머 식별자'가 반환된다.
스케줄링을 취소하고 싶을 땐 이 식별자를 사용하면 된다.
```java
let timerId = setTimeout(...);
clearTimeout(timerId);
```

# setInterval
setTimeout과 동일한 문법을 사용한다. 다만 함수를 주기적으로 실행하게 만든다. 중단하려면 clearInterval(timerId)를 사용한다.
```java
let timerId = setInterval(func|code, [delay], [arg1], [arg2], ...)
```

# 중첩 setTimeout = setInterval
무언가를 일정 간격을 두고 실행하는 방법에는 2가지가 있다.
1. setInterval 사용 -> 지연 간격을 보장하지 않음. (호출 사이의 지연 간격이 선언한 ms보다 짧음)
2. 중첩 setTimeout 사용 -> 지연 간격을 보장함. (호출 사이의 지연 간격이 함수의 실행이 종료된 이후에 다음 함수 호출을 하기 때문에 )

```java
let timerId = setTimeout(function tick() {
  alert('째깍');
  timerId = setTimeout(tick, 2000); // (*)
}, 2000);
```
## 대기 시간이 0인 setTimeout
0으로 설정하면 func을 '가능한 한' 빨리 실행할 수 있다. 다만 현재 실행 중인 스크립트의 처리가 종료된 이후에 스케줄링한 함수를 실행함
