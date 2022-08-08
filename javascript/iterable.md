# iterable 객체
반복 가능한(iterable,이터러블) 객체는 배열을 일반화한 객체다. 이터러블 이라는 개념을 사용하면 어떤 객체이든 for..of 반복문을 사용할 수 있다.
배열은 대표적인 이터레블이다. 배열 외에도 다수의 내장 객체가 반복 가능하다. 문자열 역시 이터러블의 예이다.

## Symbol.iterator
일반 객체를 이터러블로 만들려면(for..of 가 동작하도록 하려면) 객체에 Symbol.iterator(특수 내장 심볼)라는 메서드를 추가해 아래와 같은 일이 벌어지도록 해야한다.
1. for..of가 시작되자마자 for..of는 Symbol.iterator를 호출합니다(Symbol.iterator가 없으면 에러가 발생합니다). Symbol.iterator는 반드시 이터레이터(iterator, 메서드 next가 있는 객체) 를 반환해야 합니다.
2. 이후 for..of는 반환된 객체(이터레이터)만을 대상으로 동작합니다.
3. for..of에 다음 값이 필요하면, for..of는 이터레이터의 next()메서드를 호출합니다.
4. next()의 반환 값은 {done: Boolean, value: any}와 같은 형태이어야 합니다. done=true는 반복이 종료되었음을 의미합니다. done=false일땐 value에 다음 값이 저장됩니다.
```java
let range = {
  from: 1,
  to: 5,
}
// for..of 호출시 Symbol.iterator가 호출됨.
range[Symbol.iterator] = function() {
  
  // Symbol.iterator는 이터레이터 객체를 반환한다.
  // 이후 for..of는 반환된 이터엘이터 객체만을 대상으로 동작함.
  return {
   current: this.from,
   last: this.to,
   
   // for..of 반복문에 의해 반복마다 next()가 호출됨
   next() {
      
      // next()메소드는 값을 객체 {done:.., value: ..} 형태로 반환 해야함
      if(this.current <= this.last){
        return {done:false, value:this.current++}
      } else {
        return {done:true}
      }
    }
  }
 }
}
for(let num of range) {
  alert(num); // 1, 2, 3, 4, 5
}

```

## 문자열은 이터러블이다.
```java
for (let char of "test") {
  // 글자 하나당 한 번 실행됩니다(4회 호출).
  alert( char ); // t, e, s, t가 차례대로 출력됨
}
```

## 이터러블과 유사 배열
* 이터러블 : Symbol.iterator가 구현된 객체.
* 유사 배열 : 인덱스와 length 프로퍼티가 있어서 배열처럼 보이는 객체.
```java
let arrayLike = { // 인덱스와 length프로퍼티가 있음 => 유사 배열
  0: "Hello",
  1: "World",
  length: 2
};

// Symbol.iterator가 없으므로 에러 발생
for (let item of arrayLike) {}
```
*이터러블과 유사 배열은 대개 배열이 아니기 때문에 push,pop등의 메서드를 지원하지 않다.*

## Array.from
이터러블이나 유사 배열을 받아 '진짜' 배열로 반들어준다.
```java
유사배열)
let arrayLike = {
  0: 'hello',
  1: 'world',
  length: 2
};
let arr = Array.from(arrayLike);
alert(arr.pop()); // 마지막요소 제거 , world

이터러블)
let arr = Array.from(range);
alert(arr); // 1,2,3,4,5 (배열 - 문자열 형 변환이 제대로 동작함.)
```


