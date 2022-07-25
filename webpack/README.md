# Webpack 이란
    여러개의 리로스 파일(js, css, jpg)을 하나의 js 파일로 묶어주는 도구인 웹팩

### 웹팩의 장점
1. 여러개의 파일을 하나로 묶어주기 때문에 네트워크 접속의 부담을 줄 일 수 있다. 더 빠른 서비스를 제공할 수 있다.
2. 여러개의 서로 다른 패키지들이 서로 같은 이름의 전역 변수를 사용하면 프로그램은 오동작하게 되는데, 이런 문제를
극복하기 위해서 등장한 것이 모듈이다. 웹팩은 최신 기술이라서 적용하기가 애매한 기술인 모듈을 브라우저에서도 사용할 수 있게 도와준다.
3. 웹팩에는 매우 많은 플러그인들이 존재한다. 이런 플러그인을 이용하면 웹 개발시에 필요한 다양한 작업을 자동화 할 수 있다.


<img src=https://user-images.githubusercontent.com/83282953/180798684-d0d736a4-2f58-41b6-ab69-85e1546e3d08.png width=50% height=50%> 
<img src=https://user-images.githubusercontent.com/83282953/180798483-6976d690-f9c5-4c6d-b842-29b13d207dd3.png width=50% height=50%>
* 이와같이 서로 다른 파일에 변수이름이 같아서 나중에 선언한 world.js가 기존에 있던 변수를 덮어 쓰게 된다.

* 이런 문제를 극복하기 위한 개념이 모듈이다. 모듈에 대한 기능이 최신 브라우저에는 탑재 되어있다.

### 모듈

    * index.html
        <head>
            <!-- <script src="./source/hello.js"></script>
            <script src="./source/world.js"></script> -->
        </head>
        <body>
            <h1>Hello, Webpack</h1>
            <div id="root"></div>
            <script type="module">
                import hello_word from './source/hello.js';
                import world_word from './source/world.js';
                document.querySelector('#root').innerHTML = hello_word + ' ' + world_word;
            </script>
        </body>

    * hello.js
        var word = 'Hello';
        export default word;
        
    * world.js
        var word = 'World';
        export default word;

* hello.js 라고 하는 모듈을 import하는 쪽에서 export default 뒤에 있는 값을 사용 할 수 있다.
<img src=https://user-images.githubusercontent.com/83282953/180801458-bb9b111c-ea09-4ddd-904c-74ee303bcc3d.png width=30% height=30%>

