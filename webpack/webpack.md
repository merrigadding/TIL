# 웹팩 사용하기

1. node.js 설치

2. npm이라는 커멘드 라인을 사용함.
```
    npm init 
```

3. package.json 생성된 후
```
    npm install -D webpack webpack-cli //  -D는 애플리케이션 자체를 위한게아니라 개발을 하기 위한 옵션
```
4. bundling할 파일을 생성 후 (index.js) 기존에 있던 index.html의 script문을 그대로 복붙함.
<img src=https://user-images.githubusercontent.com/83282953/180805729-bb70d9ad-fdc5-4745-9ba8-363cec56534a.png width=50% height=50%>

5. 작업한 결과를 public이라는 폴더 아래에 생성하고 싶을때 터미널에서
```
    npx webpack --entry ./source/index.js --output-path ./public/ --output-filename index_bundle.js
    // entry는 bundling할 파일, output-path는 결과 된 파일의 경로, filename은 파일 이름
```

6.  index.html 파일 수정
```
     <body>
        <h1>Hello, Webpack</h1>
        <div id="root"></div>
        <script src="./public/index_bundle.js"></script>
      </body>
```

7. 결과 
<img src=https://user-images.githubusercontent.com/83282953/180808898-788ea70f-0c07-4370-8b13-3ca75ea71a60.png width=50% height=50%>

* js파일이 한개만 불러온 것을 알 수 있다.

