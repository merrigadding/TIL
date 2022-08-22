# func.call
this를 명시적으로 고정해 함수를 호출할 수 있게 해주는 특별한 내장 함수 메서드
```java
func.call(context, arg1, arg2, ...)
```
첫 번째 인수가 this, 이어지는 함수가 func의 인수가 된 후, func이 호출된다.

```java
function Hi() {
  alert(this.name)
}
let user = { name: 'John' }
let user2 = { name: 'Alex' }

Hi.call(user) // this가 user를 가리킴
Hi.call(user2) // this가 user2를 가리킴
```
아래는 인수를 추가할 때
```java
function Hi(age) {
  alert(`${this.name} 나이는 ${age}`)
}
let user = { name: 'John' }

Hi.call(user, 10) // John 나이는 10
```

# 여러 인수 전달하기 func.apply
func.call(this, ...arguments) = func.apply(this, arguments)
```java
func.apply(context, args) // args : 유사 배열 객체
```

## 차이점
* 전개 문법 ...은 이터러블 args를 분해 해 call에 전달할 수 있도록 해준다.
* apply는 오직 유사 배열 형태(arguments, NodeList 등)
* 컨텍스트와 함께 인수 전체를 다른 함수에 전달하는 것을 콜 포워딩 이라고 한다.
