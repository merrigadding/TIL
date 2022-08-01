# 1. HTMLCollection

HTMLCollection은 문서내에 순서대로 정렬된 노드의 컬렉션으로, 유사 배열이다. HTMLCollection을 얻을 수 있는 간단한 방법은 HTML 엘리멘트의 children 프로퍼티에 접근하는 것이다.

```java
console.log(el.children)

> HTMLCollection(2) [input, div.agreement-mg]
```
*유사배열 이기 때문에, 배열에서 제공하는 모든 메서드를 가지고 있지 않다. ex) forEach, map* 

.forEach나 .map을 사용하려면 배열구조나 Array.from() 으로 HTMLCollection으로부터 배열을 생성해서 해당 메서드를 사용할 수 있다.

```java
const arr = el.children
console.log(arr) // HTMLCollection(2) [input, div.agreement-mg]

const res = [...arr].map((node) => node)
console.log(res) // (2) [input, div.agreement-mg]

Array.from(arr).forEach((res) => console.log(res)) // <input type="text" />

for (let a of arr) {
  console.log(a) // <input type="text" />
}
```

### 요소에 접근하기 

1. 객체의 속성에 접근하듯이 .[속성명] 의 방식으로 접근
```java
<template>
  <input type="checkbox" name="test" />
</template>
<script>
  const arr = el.children
  console.log(arr.test) // <input type="checkbox" name="test">
</script>
```
2. 배열의 인덱스로 접근
```java
<template>
  <input type="checkbox" name="test" />
</template>
<script>
  const arr = el.children
  console.log(arr[0]) // <input type="checkbox" name="test">
</script>
```

***

# 2. NodeList
NodeList는 element.childNodes 프로퍼티나 document.querySelectorAll 메서드에서 반환되는 노드의 모음이다.
NodeList도 유사 배열인데, forEach 메서드는 갖고 있다. 하지만 map,filter등의 메서드를 사용하려면 위에서 언급한 방법을 이용해
배열로 바꿔주어야 한다.

*또 다른 이용 가능한 메서드에는 entries(), keys(), values()가 있다.*

### childNodes와 querySelectAll() 의 차이

둘다 NodeList를 반환하지만 차이점을 갖고 있다. 변경사항의 유무이다.

Node.childNodes의 NodeList는 라이브 콜렉션으로, DOM의 변경사항을 실시간으로 반영한다.
반면에, document.querySelectAll()의 NodeList는 정적 콜렉션으로, DOM이 변경되어도 collection의 내용에는 영향을 주지 않는다.

```java
const staticNList = document.querySelectorAll('div');
const dynamicNList = document.body.childNodes;

console.log(dynamicNList);
> NodeList(33) [text, script, text, ul#nav-access, text, comment, text, header#main-header.header-main, ...]

console.log(staticNList);
> NodeList(52) [div.nav-toolbox-wrapper, div#nav-tech-submenu.submenu.js-submenu, div.submenu-column, div#nav-learn-submenu.submenu.js-submenu, ...]


// DOM 변경
const div = document.createElement('div');
document.body.appendChild(div);

console.log(dynamicNList);
> NodeList(34) [text, script, text, ul#nav-access, text, comment, text, header#main-header.header-main, ...]

console.log(staticNList);
> NodeList(52) [div.nav-toolbox-wrapper, div#nav-tech-submenu.submenu.js-submenu, div.submenu-column, div#nav-learn-submenu.submenu.js-submenu, ...]
```

*동적콜렉션인 childNodes는 실시간 반영되는 반면, 정적콜렉션인 querySelectAll은 반영되지 않았다.*

출처 <https://devsoyoung.github.io/posts/js-htmlcollection-nodelist>
