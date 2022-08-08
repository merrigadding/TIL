# new 연산자
객체 리터럴{...} 을 사용하면 객체를 쉽게 만들수 있다. 그런데 개발을 하다 보면 유사한 객체를 여러개 만들어야 할때가 생기곤 한다.
복수의 사용자,메뉴 내 다양한 아이템을 객체로 표현하려고 하는 경우.

1. 함수 이름의 첫 글자는 대문자로 시작한다.
2. 반드시 'new' 연산자를 붙여 실행한다.
```java
  function User(name) {
    this.name = name;
    this.isAdmin = false;
  }
  
  let user = new User("보라");
  
  alert(this.name); //보라
```

## 동작원리
1. 빈 객체를 만들어 this에 할당.
2. 함수 본문을 실행한다. this에 새로운 프로퍼티를 추가해 this를 수정한다.
3. this를 반환한다.

```java
  function User(name) {
    // this = {}; // 빈 객체가 암시적으로 만들어짐
    
    // 새로운 프로퍼티를 this에 추가함
    this.name = name;
    this.isAdmin = false;
    
    // return this; // this가 암시적으로 반환됨.
  }
```

## 생서자 내 메서드
생성자 함수를 사용하면 매개변수를 이용해 객체 내부를 자유롭게 구성할 수 있다.
```java
  function User(name) {
    this.name = name;
    
    this.sayHi = function() {
      alert('제 이름은' + this.name + '입니다.')
    }
  }
  
  let bora = new User('보라');
  
  bora.sayHi(); // 제 이름은 보라입니다.
```
