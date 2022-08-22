# 프로퍼티 getter와 setter
객체의 프로퍼티는 두 종류로 나뉜다.
1. 데이터 프로퍼티 : 지금까지 사용한 모든 프로퍼티는 데이터 프로퍼티
2. 접근자 프로퍼티 : 접근자 프로퍼티의 본질은 함수인데, 이 함수는 값을 획득(get)하고 설정(set)하는 역할을 담당한다.

## getter와 setter
접근자 프로퍼티는 'getter(획득자)'와 'setter(설정자)' 메서드로 표현된다.
```java
let obj = {
  get propName() {
    // getter, obj.propName을 실행할 때 실행되는 코드
  },

  set propName(value) {
    // setter, obj.propName = value를 실행할 때 실행되는 코드
  }
};
```
* getter 메서드 : obj.propName 를 사용해 프로퍼티를 읽을때 실행됨.
* setter 메서드 : obb.proName = value 으로 값을 할당 할때 실행됨.
```java
let obj = {
  name: '홍길동',
  get sayHi() {
    return this.name + ' 안녕'
  },
}
console.log(obj.sayHi) // 외부 코드에서 접근자 프로퍼티를 일반 프로퍼티처럼 사용할 수 있다.
```
```java
let obj = {
  name: '홍길동',
  get sayHi() {
    return this.name + ' 안녕'
  },
  set sayHi(value) {
    this.name = value
  },
}
obj.sayHi = '아오' // set 메서드 실행
console.log(obj.sayHi) // 아오 안녕
```
### 접근자 프로퍼티 설명자
데이터 프로퍼티의 설명자와 접근자 프로퍼티의 설명자는 다르다.
1. value와 writable가 없는 대신 get와 set이라는 함수가 있다.
2. enumerable , configurable - 데이터 프로퍼티와 동일
```java
Object.defineProperty(user, 'fullName', {
  get() {
    return `${this.name} ${this.surname}`;
  },

  set(value) {
    [this.name, this.surname] = value.split(" ");
  }
});
```

