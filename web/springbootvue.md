# Springboot + Vue.js 연동

spring boot : eclipse
vue.js : visual studio code



### 1. eclipse실행 후 File - New - Spring Starter Project
![1](https://user-images.githubusercontent.com/83282953/179518477-96e202bc-5c1d-441e-ad6f-df7c788ca535.png)

### 2. Name, Package 등 알맞게 변경 후 Next
![2](https://user-images.githubusercontent.com/83282953/179514637-1c373ba4-ac84-4ace-b77a-ab82988fbbda.png)

### 3. porm.xml에 추가할 것들을 선택 (추후에 추가 가능하니 Spring Boot DevTools, Oracle만 선택함)
<img src="https://user-images.githubusercontent.com/83282953/179514787-e0e5574f-bf31-4fda-b2a6-9a4fe16e8df1.png"  width="50%" height="50%"/>
![3](https://user-images.githubusercontent.com/83282953/179514787-e0e5574f-bf31-4fda-b2a6-9a4fe16e8df1.png)

### 4. application.properties를 열어 포트를 변경
    server.port=9990

### 5. vs code에서 프로젝트 폴더 - src/main/resources로 이동 
<img src="https://user-images.githubusercontent.com/83282953/179517319-ba54f090-9914-48b3-a0c0-852b228b79a4.png"  width="50%" height="50%"/>

### 6. 터미널 - vue create 프로젝트명(npm이 설치 되었다는 가정 하에) - 알맞은 vue 버전 선택
<img src="https://user-images.githubusercontent.com/83282953/179517598-794bf78d-d7a8-4093-8dd6-da192d13bd5e.png"  width="50%" height="50%"/>

### 7. 현재 vs code가 열린 폴더가 아닌 생성된 vue 폴더로 이동 (cd 프로젝트명도 가능)
    * open folder - resources - vue
![6](https://user-images.githubusercontent.com/83282953/179518200-e10c73dc-06b1-43d3-86d6-ba5b177e0421.png)
