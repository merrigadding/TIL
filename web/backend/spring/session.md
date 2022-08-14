# session
로그인 로직을 구성할때 처리하기 위해 사용함

## session에 값 추가 및 조회
1. request.getSession() : 기본값 true, session 이 있으면 기존 세션 반환, session 이 없으면 신규 생성
2. request.getSession(session key값) // 값이 없으면 null
3. request.getSession(false) // 없으면 session 생성 X , null을 반환
```java
@RequestMapping(value = "/login",method = RequestMethod.GET,produces = "application/json")
public ResponseEntity<StatusObj> login(
    HttpServletRequest request,
    HttpServletResponse response,
    ...
  ) { 
  UserVo vo = new UserVo();
  ...
  UserVo userVo= service.userInfo(vo);
  if(userVo != null) {
    HttpSession session = request.getSession();
    session.setAttribute("userInfo", userVo);
    log.info("user 정보 : {}", session.getAttribute("userInfo").toString());
  }
  ...
}
```
## session 값 삭제
1. session.invalidate(); // 전부삭제
2. session.removeAttribute(session 값) // 해당 session 삭제
```java
HttpSession session = request.getSession(false); // 추가로 생성하지 않기 위함 ( 기본값 : true)
if(session != null) {
  session.invalidate(); // 전부 삭제 , 일부 삭제할땐 ;
}
```
