### __proto__ 는 구식
모던한 메서드를 사용
* Object.create(proto, [descriptors]) - [[Prototype]] 이 proto를 참조하는 빈 객체를 만든다.
* Object.getPrototypeOf(obj) - obj의 [[Prototype]]을 반환한다.
* Object.setPrototypeOf(obj, proto) - obj의 [[Prototype]] 이 proto가 되도록 설정한다.
```java
let rabbit = Object.create(animal)
console.log(rabbit.eats) // true
console.log(Object.getPrototypeOf(rabbit) == animal) // true
Object.setPrototypeOf(rabbit, { name: 30 }) // rabbit의 [[Prototype]]을 {name: 으로 설정}
console.log(rabbit.name) // 30
```

설명자를 이용해 프로퍼티 추가
```java
let animal = {
  eats: true
};

let rabbit = Object.create(animal, {
  jumps: {
    value: 10
  }
});

alert(rabbit.jumps); // 10
```

### __proto__에서 getPrototypeOf, setPrototypeOf로 대체된 이유
프로토타입을 그때그때 바꾸는 연산은 객체 프로퍼티 접근 관련 최적화를 망치기 때문이다.

* __proto__ 는 객체의 프로퍼티가 아니라  Object.prototype의 접근자 프로퍼티(get, set)이다.
* obj.__proto__를 읽거나 쓸때는 이에 대응하는 getter,setter가 프로토타입에서 호출된다.
* obj는 [[Prototype]]을 통해 getter와 setter에 접근한다.
* __proto__는 [[Prototype]]에 접근하기 위한 수단이지 [[Prototype]] 그 자체가 아니다.
