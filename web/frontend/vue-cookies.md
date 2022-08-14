# vue-cookies
Cookie는 clien단 (로컬)에 저장하는 임시 저장소 같은것이다.
쿠키 삭제등을 하게되거나 만료일이 지남녀 삭제될수 있다.

### 쿠키 외에 로컬에 사용하는 저장소
1. localStorage
2. sessionStroage

## vue-cookies 설치
```java
npm install vue-cookies
```
```java
// main.js
import vueCookies from 'vue-cookies'

Vue.use(vueCookies)
Vue.$cookies.config('1d') // expire 1일 (global 설정)

```

## 사용법 
1. cookie에 저장하기
```java
this.$cookies.set('userIdCookie', this.userId)
```
2. cookie 값 불러오기
```java
this.$cookies.get('userIdCookie')
```
3. cookie 모든 값 삭제
```java
this.$cookies.keys().forEach((cookie)=> this.$cookies.remove(cookie))
```
출처 : <https://hello-bryan.tistory.com/270>
