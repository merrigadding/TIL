# vuex-persistedstate
뒤로가기 버튼, 새로고침시 지금까지 vuex의 store에 가지고 있ㄷ거나 계산되어져 있던 모든 값들이 초기화 되어버리는 상황이 발생한다.
이런 불편함을 해소하기 위해 localstroage를 이용하여 값들을 다시 살려내주는 기능이다.

## vuex-persistedstate 원리
1. 프로젝트 전체에서 사용되는 변수를 store의 state에 저장을 하고 사용하게 된다.
2. 그러면 vuex-persistedstate는 이 state에 저장된 변수와 값을 그대로 localstoreage에 업데이트를 해준다.
3. 다시 말하면 state와 localstorage를 지속적으로 동기화를 해주는 역활을 한다.
4. localstorage에 등록된 내용은 쿠키나 세션처럼 화면을 새로고침 해도 없어지지 않기 때문에 새로 화면이 로딩을 하게되면 localstorage에 있는 내용을 state에 다시 동기화 시켜준다

## 설치 방법
* npm : npm install --save vuex-persistedstate
* yarn : yarn add vuex-persistedstate

```java
// store - index.js

import createPersistedState from "vuex-persistedstate";

export default new Vuex.Store({
  state,
  getters,
  mutations,
    plugins: [
    createPersistedState({
      // 여기에 쓴 모듈만 저장됩니다.
      paths: ['userInfo'],
    }),
  ],
});
```
출처 : <https://uxgjs.tistory.com/207> ,https://dong-queue.tistory.com/72
