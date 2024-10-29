# Spring Security 
- 어떤 공격에 대한 인증과 인가, 그리고 방어를 제공해주는 프레임워크입니다.
- Spring 애플리케이션 기반의 보안을 담당합니다.
- 스프링 시큐리티는 `필터`기반으로 동작합니다.
### 인증 처리 과정
![image](https://github.com/user-attachments/assets/76792e17-a69f-489c-8c10-6e087e893998)
1. 사용자가 아이디와 비밀번호를 통해 인증 요청을 보냅니다.
2. 사용자의 요청의 아이디와 비밀번호를 통해`AuthenticationFilter`가 유효성 검사를 진행합니다.
3. 유효성 검사 후 아이디와 비밀번호를 바탕으로 `AuthenticationFilter`가 `UsernamePasswordAuthenticationToken` 객체를 생성합니다.
4. 생성된 `UsernamePasswordAuthenticationToken`객체를 `AuthenticationManager`에게 전달합니다.
5. `UsernamePasswordAuthenticationToken` 객체를 `AuthenticationProvider`에게 전달합니다.
6. 사용자의 아이디를 `UserDetailsService`로 보내고, `UserDetailsService`는 사용자의 아이디로 찾은 사용자의 정보를 `UserDetails` 객체를 생성하여 `AuthenticationProvider`에게 전달합니다.
7. DB에 저장되어 있는 사용자 정보를 가져와 `UserDetails`의 정보와 비교하여 인증 처리를 진행합니다.
8. 인증이 완료되면 `SecurityContextHolder`에 `Authentication`을 저장합니다. 
### SecurityFilterChain
- `Spring Security`에서 클라이언트로부터 HTTP 요청이 들어왔을 때 요청을 처리(인증, 인가)하는데 사용되는 여러 보안 필터들의 모음입니다.
- `FilterChain Proxy`가 관리합니다.
- `Spring Security`의 거의 대부분의 서비스가 `Security Filter Chain`에서 이루어집니다.
![image](https://github.com/user-attachments/assets/41d84660-ec23-4453-a713-676e2b9a7356)
### SecurityContextHolder
- `SecurityContext`를 가지고 있습니다.
- `SecurityContextHolder`는 싱글톤 객체이기 때문에 로드될 때 한 번만 호출됩니다.
![image](https://github.com/user-attachments/assets/8e67f61b-0715-4a0e-af58-330cd81eb2ab)
##### SecurityContext
- `Authentication`객체를 저장하는 역할을 합니다.
##### Authentication
- 현재 접근한 사용자의 정보와 권한을 담고 있는 객체입니다.
- 이 `Authentication`객체는 `SecurityContext`안에 저장됩니다.
-  `Authentication`은 `principal`, `credentials`, `authorities`의 정보들을 가지고 있습니다.
	- `principal` : 사용자의 정보들을 가지고 있으며, `UserDetails`객체를 뜻합니다.
	- `credentials` : 비밀번호를 저장할 때 활용되고, 비밀번호 유출을 막기 위해 사용자 인증 후 삭제됩니다.
	- `authorities` :  `GrantedAuthority` 객체를 통해서 사용자에게 부여된 권한을 가지고 있습니다.
#### GrantedAuthority 
- 사용자의 역할과 권한에 대한 정보를 가지고 있습니다.
- `Authentication.getAuthorities()` 메서드를 통해 사용자의 역할과 권한에 대해 조회할 수 있습니다.
- `UserDetailsService`에 의해 로드됩니다.
#### AuthenticationManager 
- `AuthenticationProvider`를 이용하여 실제 인증을 수행합니다.
#### AuthenticationProviders 
- 인증 전 객체를 받고 인증 후 객체를 반환합니다.
#### UserDetails  
- `Spring Security`를 사용하는 사용자의 이름, 비밀번호, 권한등의 정보들을 담고 있는 인터페이스입니다.
#### UserDetailsService
- `UserDetailsService`에서 `UserDetails` 객체를 반환하는 메서드를 통해 찾은 사용자의 식별 정보를 기반으로 `UserRepository`를 주입 받은 후, DB에 저장되어있던 사용자 정보를 조회하여 `UserDetails` 객체로 반환합니다.
## 참고 자료
- https://velog.io/@dl-00-e8/Spring-Spring-Security%EB%A1%9C-%EC%9D%BC%EB%B0%98-%EB%A1%9C%EA%B7%B8%EC%9D%B8-%EA%B5%AC%ED%98%84
- https://velog.io/@dh1010a/Spring-Spring-Security%EB%A5%BC-%EC%9D%B4%EC%9A%A9%ED%95%9C-%EB%A1%9C%EA%B7%B8%EC%9D%B8-%EA%B5%AC%ED%98%84-%EC%8A%A4%ED%94%84%EB%A7%81%EB%B6%80%ED%8A%B8-3.X-%EB%B2%84%EC%A0%84-1
- https://samori.tistory.com/64
- https://velog.io/@choidongkuen/Spring-Security-Spring-Security-Filter-Chain-%EC%97%90-%EB%8C%80%ED%95%B4
- https://ohtaeg.tistory.com/8