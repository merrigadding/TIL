# async & await
async와 await는 자바스크립트의 비동기 처리 패턴 중 가장 최근에 나온 문법이다. 기존의 비동기 처리방식인 콜백함수와 Promise의 단점을 보완하고 개발자가 읽기 좋은 코드를 작성 할 수 있게 도와준다.

## 기본문법
```java
async function 함수명() {
  await 비동기_처리_메서드_명();
}
```
먼저 함수의 앞에 async 라는 예약어를 붙인다. 그러고 나서 함수의 내부 로직 중 HTTP통신을 하는 비동기 처리 코드 앞에 await를 붙인다. 여기서 주의 할 점은 비동기 처리 메서드가
꼭 프로미스 객체를 반환해야 await가 의도한 대로 동작한다.

*일반적으로 await의 대상이 되는 비동기 처리 코드는 Axios등 프로미스를 반환하는 API 호출 함수이다.*

### vue js 적용 예시

```java
methods: {
  async test() {
    var user = await this.fetchUser() // axios 등 promise 객체를 반환 받아야 함.
    console.log(user);
    if(user.id ===1) {
     var todo = await this.fetchTodo() // 비동기 처리를 순차적으로 진행함.
     console.log(todo.title);
    }
  },
  fetchTodo() {
    var url = 'https://jsonplaceholder.typicode.com/todos/1'
    return fetch(url).then(function (response) { // fetch 함수로 HTTP 요청을 하여 프로미스 객체를 반환 받음.
      return response.json() // body 텍스트를 JSON 형식으로 바꿈
    })
  },
  fetchUser() {
    var url = 'https://jsonplaceholder.typicode.com/users/1'
    return fetch(url).then(function (response) {
      return response.json()
    })
  },
},
```

### 예외 처리 (try ~ catch)
```java
async function logTodoTitle() {
  try {
    var user = await fetchUser();
    if (user.id === 1) {
      var todo = await fetchTodo();
      console.log(todo.title); // 성공시 promise 객체의 resolve 값으로 들어감
    }
  } catch (error) {
    console.log(error); // 실패시 promise 객체의 reject 값으로 들어감
  }
}
```

### 실제 프로젝트에 적용
```java
async test() {
    try {
      const prom = prompt('입력해보셈')
      var user = await this.noTest(prom)
      console.log(user) // 123 입력했을시 '성공'
    } catch (err) {
      console.log(err) // 123 아닐때 '실패'
    }
  },
  noTest(abc) {
    return new Promise((resolve, reject) => {
      if (abc === '123') {
        resolve('성공')
      } else {
        reject('실패')
      }
    })
  },
```
# 에러 핸들링
프라미스가 정상적으로 이행되면 await promise는 프라미스 객체의 result에 저장된 값을 반환한다. 반면 프라미스가 거부되면 마치 throw문을 작성한 것처럼 에러가 던져진다.
```java
async function f() {
  await Promise.reject(new Error('에러 발생!'))
}
```
위 아래와 같음
```java
async function f() {
  throw new Error('에러발생')
}
```
try..catch를 사용해 잡을수 있다.
```java
async function f() {
    try {
      let response = await fetch('https://api.github.com/users/iliakan')
      let user = await response.json()
      console.log(user)
    } catch (err) {
      // fetch와 response.json에서 발행한 에러 모두를 여기서 잡습니다.
      console.log(err)
    }
  }

f()
```
async/await 를 사용하면 promise.then/catch가 거의 필요 없다. 하지만 가끔 가장 바깥 스코프에서 비동기 처리가 필요할 때 같이
promise를 써야만 하는 경우가 생기기 때문에 async/await가 프라미스를 기반으로 한다는 사실을 알고 있어야 한다.
출처<https://joshua1988.github.io/web-development/javascript/js-async-await/>
