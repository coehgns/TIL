# @EnableWebSecurity란?
- 스프링 시큐리티를 설정하고, 웹 보안 활성화 및 설정함.
## @EnableWebSecurity의 활용법
- 보통 [[@Configuration]] 어노테이션과 함께 사용됨.
- 스프링 시큐리티 설정을 위한 클래스에 해당 어노테이션을 선언함.
- @EnableWebSecurity 어노테이션이 자동으로 스프링 시큐리티 필터 체인을 생성하고 웹 보안을 활성화함.
## @EnableWebSecurity 기능
- 해당 어노테이션을 활용하면 스프링 시큐리티 필터 체인이 작동하여 요청을 인가하고 인증함.
## 참고 자료
- https://jjangadadcodingdiary.tistory.com/entry/%EC%8A%A4%ED%94%84%EB%A7%81-%EC%8B%9C%ED%81%90%EB%A6%AC%ED%8B%B0%EC%97%90%EC%84%9C-EnableWebSecurity-%EC%96%B4%EB%85%B8%ED%85%8C%EC%9D%B4%EC%85%98%EC%9D%98-%ED%99%9C%EC%9A%A9-%EB%B0%A9%EB%B2%95%EA%B3%BC-%EA%B8%B0%EB%8A%A5