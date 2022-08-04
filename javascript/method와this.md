# method
객체는 사용자(user), 주문(order) 등과 같이 실제 존재하는 개체(entify)를 표현하고자 할 때 생성된다.
```java
  let user = {
    name: "John",
    age: 30
  }
```

사용자는 현실에서 장바구니에서 물건 선택하기, 로그인하기, 로그아웃하기 등의 행동을 한다.
이와 마찬가지로 사용자를 나타내는 객체 user도 특정한 행동을 할 수 있다.

## 메서드 만들기
```java
let user = {
  name: "John",
  age: 30
};

user.sayHi = function() {
  alert('안녕하세요');
};
user.sayHi(); // 안녕하세요

```
함수 표현식으로 함수를 만들고, 객체 프로퍼티 user.sayHi에 함수를 할당해 주었다.
이렇게 객체 프로퍼티에 할당된 함수를 메서드(method)라고 한다.
*user에 할당된 sayHi가 메서드*

## 이미 정의된 함수를 이용해서 만들기
```java
let user = {
  //
};

// 함수 선언
function sayHi() {
  alert('안녕하세요');
}

user.sayHi = sayHi;

user.sayHi(); // 안녕하세요

```

## 메서드 단축 구문
```java
let user = {
  sayHi() {
    alert('안녕하세요');
  }
}
```
# 메서드와 this
메서드는 객체에 저장된 정보에 접근할 수 있어야 제 역할을 할 수 있다. 모든 메서드가 그런건 아니지만, 대부분의 메서드가
객체 프로퍼티의 값을 활용한다.
user.sayHi()의 내부 코드에서 객체 user에 저장된 이름(name)을 이용해 인사말을 만드는 경우가 이런 경우에 속한다.
```java
let user = {
  name : 'John',
  age : 30,
  sayHi() {
    alert(this.name);
  }
}

user.sayHi(); // John

```

## 자유로운 this
자바스크립트에서 모든 함수에 this를 사용할 수 있다.
```java
ex ) 
  function sayHi() {
    alert(this.name); // 에러는 안뜸
  }
```
*this값은 런타임에 결정된다.*
```java
let user = {name: 'John'};
let admin = {name: 'Admin'};

function sayHi() {
  alert(this.name);
}

user.f = sayHi;
admin.f = sayHi;

user.f(); // John
admin.f(); // Admin

```
# this가 없는 화살표 함수
화살표 함수는 일반 함수와 달리 this를 가지지 않다.
화살표 함수에서 this를 참조하면, 화살표 함수가 아닌 '평범한' 외부 함수에서 this를 가져온다.

```java
let user = {
  firstName: '보라',
  sayHi() {
    function arrow() {
      alert(this.firstName); // 메서드가아닌 함수로써 호출 되었기 때문에 window 객체(전역 객체)를 향함
    }
    arrow();
  }
}
user.sayHi(); 
```

```java
let user = {
  firstName: '보라',
  sayHi() {
    let arrow = () => {
      alert(this.firstName);
    }
    arrow();
  }
}
user.sayHi(); // 보라
```







