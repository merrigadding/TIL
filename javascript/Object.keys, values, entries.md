# Object.keys, values, entries
일반 객체엔 다음과 같은 메서드를 사용할 수 있다.
* Object.keys(obj) - 객체의 키만 담은 배열을 반환한다.
* Object.values(obj) - 객체의 값만 담은 배열을 반환한다.
* Object.entries(obj) - [키, 값] 쌍을 담은 배열을 반환한다.
```java
let obj = {
  name: '홍길동',
  age: 30,
}

console.log(Object.keys(obj)) // 2) ['name', 'age']
console.log(Object.values(obj)) // 2) ['홍길동', 30]
console.log(Object.entries(obj))
// 0: (2) ['name', '홍길동'] 1: (2) ['age', 30]
```

## 객체 변환하기
객체엔 map, filter 같은 배열 전용 메서드를 사용할 수 없다.
하지만 Object.entries와 Object.fromEntries를 순차적으로 적용하면 객체에도 배열 전용 메서드를 사용 할 수 있다.
1. Object.entries(obj) 를 사용해 [키,값] 쌍이 요소인 배열을 얻는다.
2. 1.에서 만든 배열에 map이나 filter 등 배열 전용 메소드를 사용한다.
3. 2.에서 반환된 배열에 Object.fromEntries를 적용해 배열을 객체로 되돌린다.
```java
let obj = {
  name: '홍길동',
  age: 30,
}
let newMap = Object.fromEntries(
  Object.entries(obj).filter(([key, value]) => typeof value == 'string')
)
console.log(newMap) // {name: '홍길동'}
```
