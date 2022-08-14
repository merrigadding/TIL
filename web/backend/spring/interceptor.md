# 인터셉터
이름 그대로 '무언가를 가로챈다' 라는 의미이다. 스프링 컨텍스트의 기능으로 임의의 URI를 호출시 DispatcherServlet에서 해당 Controller가 처리되기 전과 후에 발생하는 이벤트이다.
<br>
<img src=https://user-images.githubusercontent.com/83282953/184533537-fa7c4810-21ab-4695-a3ff-f2523026975c.png width="500px" heigth="300px">

## 구현
HandlerInterceptorAdapter를 상속받아 구현하며 preHandle, postHandle, afterCompletion, afterConcurrentHandlingStarted 네 개의 메소드를 포함하고 있다.
1. preHandle : 컨트롤러 실행 전 수행한다. 반환값이 true인 경우 컨트롤러로 진입하고 false 면 진입하지 않는다.
2. postHandle : 컨트롤러가 실행 후 view가 렌더링 되기전에 수행한다.
3. afterCompletion : 컨트롤러 실행되고 view가 렌더링 된 후에 실행된다. 
4. afterConcurrentHandlingStarted : 비동기 요청 시 PostHandle과 afterCompletion이 수행되지 않고 afterConcurrentHandlingStarted가 수행된다.

## 실제 구현한 코드
```java
@Component
public class CommonInterCeptor implements HandlerInterceptor{
	
	private final Logger LOGGER = LoggerFactory.getLogger(CommonInterCeptor.class);
	
	@Override
	public boolean preHandle(HttpServletRequest request, HttpServletResponse response, Object handler)
			throws Exception {
		// TODO Auto-generated method stub
		LOGGER.info("[prehanlder] request : {}", request);
		LOGGER.info("[prehanlder] request path info: {}", request.getPathInfo());
		LOGGER.info("[prehanlder] request head name: {}", request.getHeaderNames());
		LOGGER.info("[prehanlder] request method: {}", request.getMethod());
		LOGGER.info("[prehanlder] request parameter map: {}", request.getParameterMap());
		LOGGER.info("[prehanlder] request uri: {}", request.getRequestURI());
		LOGGER.info("[prehanlder] request url: {}", request.getRequestURL());
		LOGGER.info("[prehanlder] request session: {}", request.getSession().getAttribute("userInfo"));
		LOGGER.info("[prehanlder] request session id: {}", request.getRequestedSessionId());
		return true;
	}
	
	@Override
	public void postHandle(HttpServletRequest request, HttpServletResponse response, Object handler,
			ModelAndView modelAndView) throws Exception {
		// TODO Auto-generated method stub
		HandlerInterceptor.super.postHandle(request, response, handler, modelAndView);
	}
	
	@Override
	public void afterCompletion(HttpServletRequest request, HttpServletResponse response, Object handler, Exception ex)
			throws Exception {
		// TODO Auto-generated method stub
		HandlerInterceptor.super.afterCompletion(request, response, handler, ex);
	}
}
```
출처 : <https://dejavuhyo.github.io/posts/spring-boot-interceptor/>
