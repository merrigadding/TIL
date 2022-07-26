# plugin 이란?
웹팩의 기본적인 동작에 추가적인 기능을 제공하는 속성입니다. 로더랑 비교하면 로더는 파일을 해석하고 변환하는 과정에 관여하는 반면,
플러그인은 해당 결과물의 형태를 바꾸는 역할을 한다고 보면 된다.

### plugin은 아래와 같이 선언한다.
```java
// webpack.config.js
module.exports = {
  plugins: []
}
```

***

### HtmlWebpackPlugin 이란?
웹팩으로 빌드한 결과물로 HTML 파일을 생성해주는 플러그인 이다.

### HtmlWebpackPlugin 설치
    npm i html-webpack-plugin
```java
# webpack.config.js
const HtmlWebpackPlugin = require('html-webpack-plugin');
module.exports = {
  ...
  plugins: new HtmlWebpackPlugin({
      template: './index.html', // template은 기존에 만들어 두었던 파일을 이용해서 HTML을 만들어줌
    }),
}
```




