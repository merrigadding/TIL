# webpack-dev-server  이란?
애플리케이션을 빠르게 개발하는데 사용할 수 있다. <br>( js파일이 변경될때마다 npm run build를 해줘야하는 번거로움을 없애줌 )

### webpack-dev-server 설치
    npm i webpack-dev-server -D
```java
# webpack.config.js

  devServer: {
    port: 9551,
  },
```
```java
# package.json

"scripts": {
  "start": "webpack serve --open --mode=development", // --mode를 안해주면 에러남 
  "build": "webpack --mode=production", // 보통 build는 production으로 한다고 함
},
```
### webpack 실행
    npm start // run 생략가능
    
