# Webpack 설치 및 설정

### 1. html 및 js 파일 생성
```java
  # index.html
  
  <!DOCTYPE html>
  <html lang="en">
    <head>
      <meta charset="UTF-8" />
      <meta http-equiv="X-UA-Compatible" content="IE=edge" />
      <meta name="viewport" content="width=device-width, initial-scale=1.0" />
      <title>Document</title>
    </head>
    <body>
      <div id="root"></div>
      <script src="./index.js"></script>
    </body>
  </html>
```
```java
  # index.js
  
  document.getElementById('root').innerHTML = '코딩앙마'
```

### 2. 터미널에서 npm init 명령어를 이용하여 package.json 생성
    npm init -y
    
### 2-1. package.json 이란? 
```
  프로젝트의 정보를 정의하고, 의존하는 패키지 버전 정보를 명시하는 파일이다.
  * 프로젝트의 정보 - name, version 영역
  * 패키지 버전 정보 - dependecies 또는 devDependencies 영역
```
 * 참조링크 <https://velog.io/@leyuri/Node.js-package.json-%ED%8C%8C%EC%9D%BC%EC%9D%B4%EB%9E%80/>

### 3. webpack과 webpack-cli를 개발용으로 설치(devDependencies)
    npm install webpack webpack-cli -D
    * webpack-cli는 터미널에서 webpack 커맨드를 실행 할 수 있게 해주는 커맨드라인 도구이다.
    * -D옵션은 두 개의 패키지 모두 개발할 때만 필요한 의존성이기 때문에 사용함

### 4. 루트 폴더에 webpack.config.js 파일 생성 후 설정
*이 파일은 webpack 명령어를 실행 했을때 이 파일이 설정된 내용을 자동으로 적용함.*
```java
    const path = require('path')

    module.exports = {
      entry: './src/index.html', // bundling할 파일의 정보
      output: { // bundle후에 나올 파일의 정보 
        filename: 'main.js', // bundling한 파일 명
        path: path.require(__dirname, 'dist'), 
        // path는 파일경로, __dirname은 현재 경로, 'dist'는 bundling할 파일들에 대한 최상위 root파일
      },
    }
```
### 4-1. bundling할 파일을 생성 후 몇가지의 함수를 추가
```java
# utils.js

function name(word) {
  return word;
}

const add = (num1, num2) => {
  return num1 + num2;
}

export { name, add }
```

```java
# index.js

import { name, add } from './utils.js'
const word = name('하이요')
const num = add(1, 6)

console.log('하위12');

document.getElementById('root').innerHTML = word + '' + num;
```



### 4-2. package.json 에서 webpack을 실행하기위해 script문에 추가
```java
"scripts": {
  "build": "webpack",
  "test": "echo \"Error: no test specified\" && exit 1"
},
```
### 4-3. 터미널에서 npm run build 실행
    npm run build
    
*결과* <br/>
<img src=https://user-images.githubusercontent.com/83282953/181017020-c8ee752c-eaa5-4f5f-96bf-87e6a37348a1.png width=50% height=50%>
```java
;(() => {
  'use strict'
  console.log('하위12'), (document.getElementById('root').innerHTML = '하이요7')
})()
```

### 5. index.html에서 bundling된 파일로 변경
```java
<body>
  <div id="root"></div>
  <script src="./dist/main.js"></script>
</body>
```

### 5-1. 결과
<img src=https://user-images.githubusercontent.com/83282953/181018204-81adcd7e-03ed-4c16-92ab-817d36ab8406.png width=50% height=50%>


