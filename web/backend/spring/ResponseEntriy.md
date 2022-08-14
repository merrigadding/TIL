# ResponseEntity란?
Spring Framework에서 제공하는 클래스 중 HttpEntiy라는 클래스가 존재한다. 이것은 HTTP요청(Request) 또는 응답(Response)에 해당하는 HttpHeader와 HttpBody를 포함하는 클래스이다.

* RequestEntity의 생성자를 보면 this( ) 를 통해서 매개변수가 3개인 생성자를 호출해 결국엔 아래 보이는 매개변수가 3개인 생성자로 가게된다.
```java

public ResponseEntity(@Nullable T body, HttpStatus status) { 
  this(body, null, status);
}
```
반환할 객체를 생성함
```java
/// StatusObj - 반환할 객체를 담은 클래스

@Getter
@Setter
public class StatusObj {

    private StatusEnum status; // 상태 코드를 담은 변수
    private String message; // 메세지를 담은 변수
    private Object data; // 객체를 담은 변수

    public StatusObj() {
        this.status = StatusEnum.BAD_REQUEST;
        this.data = null;
        this.message = null;
    }
}

```
```java
/// StatusEnum - 상태코드 클래스

public enum StatusEnum {
	 OK(200, "OK"),
    BAD_REQUEST(400, "BAD_REQUEST"),
    NOT_FOUND(404, "NOT_FOUND"),
    INTERNAL_SERER_ERROR(500, "INTERNAL_SERVER_ERROR");

    int statusCode;
    String code;

    StatusEnum(int statusCode, String code) {
        this.statusCode = statusCode;
        this.code = code;
    }
}

```
```java
/// RestController

...
UserVo userVo= service.userInfo(vo);
StatusObj sto = new StatusObj();
sto.setData(userVo);
sto.setStatus(StatusEnum.BAD_REQUEST);
sto.setMessage("성공코드");
return new ResponseEntity<>(sto, HttpStatus.OK);
...
```

출처 : <https://devlog-wjdrbs96.tistory.com/182>
