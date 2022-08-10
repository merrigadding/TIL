## 객체 생성하기
```java
let now = new Date();
console.log(now);
```

## 타임스탬프
1970년의 첫날을 기준으로 흘러간 밀리초를 나타내는 정수 를 뜻함.
* date.getTime() // Date 객체에서 추출 가능
* new Date(timeStamp) // 생성자로 가능
* Date.now() // 객체를 만들지 않고 생성 가능

### 달의 마지막 날
```java
getLastDayOfMonth(2022, 7)

function getLastDayOfMonth(y, m) {
  let date = new Date(y, m + 1, 0) 
  // 세번째 인자는 date(일)이 오는날인데 기본값이 1이지만 0을 해주게 되면 자동으로 1일전이 조정해줌

  console.log(date.getDate())
}
```

### 오늘 하루가 시작된 이후 몇초가 되었을까
```java
getSecondsToday()

function getSecondsToday() {
  let now = new Date()
  let today = new Date(now.getFullYear(), now.getMonth(), now.getDate())

  let diff = now - today
  console.log(Math.round(diff / 1000))
}
```
### 다음 날까지 몇초가 남았을까
```java
getSecondsToday()

function getSecondsToday() {
  let now = new Date()
  let tom = new Date(now.getFullYear(), now.getMonth(), now.getDate() + 1)

  let diff = tom - now
  console.log(Math.round(diff / 1000))
}
```
