# HttpServlet
- HTTP 프로토콜을 사용하는 웹 브라우저에서 Servlet 기능을 수행합니다.
- HttpServlet을 상속 받아 많은 기능을 사용할 수 있습니다.

웹 브라우저로부터 Servlet 요청을 받은 WAS는 HttpServletRequest 객체를 생성하여 요청 받을 때 전달 받은 정보를 해당 객체에 저장합니다. 그 후 웹 브라우저에 응답할 HttpServletResponse 객체를 생성하여 저장합니다. 이렇게 생성된 두 객체를 Servlet에게 전달합니다.

# Servlet
- 동적 웹 페이지를 만들 때 사용되는 자바 기반 웹 애플리케이션 프로그래밍 기술입니다.
- 웹 브라우저의 요청과 응답의 흐름을 간단한 메소드 호출만으로 체계적으로 다룰 수 있습니다.
- 서블릿 관련 추상 메소드를 제공하는 인터페이스입니다
# HttpServletRequest
- Http 프로토콜의 request 정보를 Servlet에게 전달하기 위해 사용됩니다.
- Http 요청 정보(클라이언트 요청, 쿠키, 세션 등)를 제공하는 인터페이스입니다.
# HttpServletResponse
- Http 응답 정보를 제공하는 인터페이스입니다.
- Servlet은 HttpServletResponse 객체에 content-type, 응답 코드, 응답 메시지 등을 담아서 전송합니다.
## 참고 자료
- https://velog.io/@oliviarla/HttpServletRequest-HttpServletResponse-%EA%B0%9D%EC%B2%B4%EB%9E%80
- https://velog.io/@green9930/HttpServletRequest-HttpServletResponse-%EC%A0%95%EB%A6%AC
- https://velog.io/@falling_star3/Tomcat-%EC%84%9C%EB%B8%94%EB%A6%BFServlet%EC%9D%B4%EB%9E%80