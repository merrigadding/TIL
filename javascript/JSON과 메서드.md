# JSON과 메서드
복잡한 객체를 다루고 있을때, 네트워크를 통해 객체를 어딘가에 보내거나 로깅 목적으로 객체를 출력해야 한다면 객체를 *문자열*로
전환해야한다. 이때 JSON을 사용한다.

* JSON.stringify - 객체를 JSON으로 바꿔준다.
* JSON.parse - JSON을 객체로 바꿔준다.

```java
let obj = {
  name: '홍길동',
  age: 30,
  boolean: false,
  arr: ['1', '2'],
}
let strObj = JSON.stringify(obj)
console.log(strObj) // {"name":"홍길동","age":30,"boolean":false,"arr":["1","2"]}
```

*JSON.stringify는 객체 뿐만아니라 원시값에도 적용 가능*
```java
// 숫자를 JSON으로 인코딩하면 숫자입니다.
alert( JSON.stringify(1) ) // 1

// 문자열을 JSON으로 인코딩하면 문자열입니다(다만, 큰따옴표가 추가됩니다).
alert( JSON.stringify('test') ) // "test"

alert( JSON.stringify(true) ); // true

alert( JSON.stringify([1, 2, 3]) ); // [1,2,3]
```

*JSON.sringify가 무시하는 프로퍼티*
* 함수 프로퍼티(메서드)
* 심볼형 프로퍼티
* 값이 undefined인 프로퍼티
```java
let user = {
  sayHi() { // 무시
    alert("Hello");
  },
  [Symbol("id")]: 123, // 무시
  something: undefined // 무시
};

alert( JSON.stringify(user) ); // {} (빈 객체가 출력됨)
```

## replacer로 원하는 프로퍼티만 직렬화
```java
let obj = {
  name: '홍길동',
  age: 30,
  boolean: false,
  arr: ['1', '2'],
}
let strObj = JSON.stringify(obj, ['name', 'age'])
console.log(strObj) // {"name":"홍길동","age":30}
```
## space로 가독성 높이기
```java
let user = {
  name: "John",
  age: 25,
  roles: {
    isAdmin: false,
    isEditor: true
  }
};

/* JSON.stringify(user, null, 4)라면 아래와 같이 좀 더 들여써집니다.
{
    "name": "John",
    "age": 25,
    "roles": {
        "isAdmin": false,
        "isEditor": true
    }
}
*/
```
# JSON.parse
JSON으로 인코딩된 객체를 다시 객체로 디코딩 할 수 있다.
```java
JSON.parse(str,[reviver]);
```
* str : JSON형식의 문자열
* reviver : 모든 (key,value) 쌍을 대상으로 호출되는 function(key,value)형태의 함수로 값을 변경시킬 수 있다.
```java
let obj = {
  x: 'test',
  objDate1: [
    {
      title: 'conf',
      date: new Date(),
    },
    {
      title: 'conf',
      date: new Date(2022, 8, 11),
    },
  ],
  objDate2: {
    date4: new Date(),
  },
}
let strObj = JSON.stringify(obj)
let parseObj = JSON.parse(strObj, function (key, value) { -> 모든 key값을 찾음 , 중첩객체에도 적용 가능
  if (key == 'x') {
    return value + '키가 x임'
  } else if (key.startsWith('date')) { // 'date'로 시작하는 key 값
    return new Date(value)
  }
  return value
})
console.log(parseObj.x) // test키가 x임
console.log(parseObj.objDate1[1].date.getDate()) // 11
console.log(parseObj.objDate2.date4.getDate()) // 11
```
