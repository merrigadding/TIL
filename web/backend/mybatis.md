# 1. pom.xml 의존성 추가
```java
<dependency>
    <groupId>org.mybatis.spring.boot</groupId>
    <artifactId>mybatis-spring-boot-starter</artifactId>
    <version>2.1.1</version>
</dependency>
```
# 2. application.properties (Oracle)
```java
server.port=포트
spring.datasource.driver-class-name=oracle.jdbc.OracleDriver 
spring.datasource.url=jdbc:oracle:thin:@localhost:1521:xe
spring.datasource.username=이름
spring.datasource.password=패스워드
mybatis.mapper-locations= mybatis-mapper/*.xml
```

# 3. Mybatis 
* 데이터의 입력, 조회, 수정, 삭제(CRUD)를 보다 편하게 하기 위해 xml로 구조화 하여 Mapper 설정 파일을 통해서 JDBC를 구현한 영속성 프레임워크
  * mybatis-config.xml
    * mybatis에서 사용될 DB를 연동하기 위한 설정값들과 mapper.xml을 등록하기 위한 xml
  * mybatis-mapper.xml
    * mybatis에서 사용될 SQL  구문을 담고 있는 xml
  
 ## 3.2 초기 설정
 * xml 파일 생성시 config 파일인지 mapper 파일인지 명시하는 설정
  * preferences > XML > XML Catelog > User Specified Entries > Add..
  * config.dtd
    * Location : http://mybatis.org/dtd/mybatis-3-config.dtd
    * Key : //mybatis.org//DTD Config 3.0//EN
  * mapper.dtd
    * Location : http://mybatis.org/dtd/mybatis-3-mapper.dtd
    * Key : //mybatis.org/DTD Mapper 3.0//EN
