# Map
맵은 키가 있는 데이터를 저장한다는 점에서 객체와 유사합니다. 다만, 맵은 키에 다양한 자료형을 허용한다는 점에서 차이가 있다.

### Map 메소드
* new Map() - 맵을 만든다.
* map.set(key,value) - key를 이용해 value 를 저장한다.
* map.get(key) - key에 해당하는 값을 반환한다. key가 존재하지 않으면 undefined를 반환한다.
* map.has(key) - key가 존재하면 true, 없으면 false를 반환한다.
* map.delete(key) - key에 해당하는 값을 삭제.
* map.clear(); - 맵의 모든 요소 제거.
* map.size - 요소의 개수
```java
let map = new Map();
map.set(1,'num1');
map.set('1','str1');
map.set(true,'boolean1');

alert( map.get(1)   ); // 'num1'
alert( map.get('1') ); // 'str1'

alert( map.size ); // 3
```

#### 맵은 키로 객체를 허용한다.
```java
let obj = {
  name: '홍길동',
  age: 30,
}
let map = new Map() or new Map(Object.entries(obj))
map.set(obj, '123')
console.log(map.get(obj)) // 123
```

### 맵의 요소에 반복 작업하기.
* map.keys() - 각 요소의 키를 모은 반복가능한(iterable, 이터러블) 객체를 반환한다.
* map.values() - 각 요소의 값을 모은 이터러블 객체를 반환한다.
* map.entries() - 요소의 [키,값] 을 한 쌍으로 하는 이터러블 객체를 반환한다.

```java
let obj = {
  name: '홍길동',
  age: 30,
}
let map = new Map()
map.set(obj, '123')

for (let a of map.keys()) {
  console.log(a) // {name: '홍길동', age: 30}
}
for (let a of map.values()) {
  console.log(a) // 123
}
for (let a of map.entries()) {
  console.log(a) // 0: {name: '홍길동', age: 30}1: "123"
}
```
### Object.entries : 객체를 맵으로 바꾸기

```java
let obj = {
  name: '홍길동',
  age: 30,
}
let map = new Map(Object.entries(obj))

for (let a of map) {
  console.log(a) // (2) ['name', '홍길동'] (2) ['age', 30]
}
```
### Object.fronEntries : 맵을 객체로 바꾸기
```java
let obj = {
  name: '홍길동',
  age: 30,
}
let map = new Map(Object.entries(obj))

let fromEntries = Object.fromEntries(map)

console.log(fromEntries) // {name: '홍길동', age: 30}
```
# Set
셋은 중복을 허용하지 않는 값을 모아놓은 특별한 컬렉션이다. 셋에 키가 없는 값이 저장된다.

### Set 메소드
* new Set(iterable) - 셋을 만든다. 이터러블 객체를 전달받으면(대개 배열을 받음) 그 안의 값을 복사해 셋에 넣음.
* set.add(value) - 값을 추가하고 셋 자신을 반환한다.
* set.delete(value) - 값을 제거하고 성공하면 true, 아니면 false를 반환한다.
* set.has(value) - 셋 내에 값이 존재하면 true, 아니면 false를 반환한다.
* set.clear() - 셋을 비운다.
* set.size - 셋에 값이 몇개있는지 세준다.

### 셋의 값에 반복 작업하기
for..of 나 forEach를 사용하면 셋의 값을 대상으로 반복 작업을 수행 할 수 있다.
```java
let arr = ['a', 'b', 'c']

let set = new Set(arr)

set.forEach((res) => console.log(res)) // a b c

for (let a of set) {
  console.log(a) // a b c
}
```
### 셋에도 맵과 마찬가지로 반복 작업을 위한 메서드가 있다.
* set.keys() - 셋 내의 모든 값을 포함하는 이터러블 객체를 반환한다.
* set.values() - set.keys와 동일한 작업을 한다. 맵과의 호환성을 위해 만들어진 메서드.
* set.entries() - 셋 내의 각 값을 이용해 만든 [value, value] 배열을 포함하는 이터러블 객체를 반환한다. 맵과의 호환성을 위해 만들어진 메서드.
* 
