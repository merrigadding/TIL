# 믹스인
특정 행동을 실행해주는 메서드를 제공하는데 단독으로 쓰이지 않고 다른 클래스에 행동을 더해주는 용도로 사용된다.

### 예시
메서드 여러개가 담긴 객체를 하나 만든다.
```java
let sayHiMixin = {
  sayHi() {
    alert(`Hello ${this.name})`
  }
  ,
  sayBye() {
    alert(`Bye ${this.name}`);
  }
}

class User {
  constructor(name){
    this.name = name;
  }
}

// 메서드 복사
Object.assign(User.prototype,sayHiMixin);

new User('길동'),sayHi(); // Hello 길동
```

상속 받는 클래스도 가능
```java
class User extends Person {
  //..
}
Object.assign(User.prototype, sayHiMixin);
```

