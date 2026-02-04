# Interceptor
`Spring Context` 내부에서 `DispatcherServlet`과 컨트롤러 사이에서 다음과 같은 역할을 합니다.
## Interceptor 역할
- 세부적인 보안 및 인증/인가 공통 작업
- API 호출에 대한 로깅과 감사
- Controller 데이터 가공

`DispatcherServlet`은 `HandlerMapping`을 통해서 적절한 컨트롤러를 동작하도록 요청을 보내는데 이 때 결과로 `HandlerExcutionChain`을 응답 받습니다. 이 `HandlerExcutionChain`에 등록되어 있는 `Interceptor`들을 거치고 `Controller`를 실행하게 되는데, 만약 등록되어 있는 `Interceptor`가 없다면 바로 `Controller`가 실행됩니다.

<img width="1280" height="484" alt="Image" src="https://github.com/user-attachments/assets/44398897-a1d8-44c1-adaa-72cbde471d38" />

## 참고 자료
- https://gngsn.tistory.com/153#google_vignette
- https://mangkyu.tistory.com/173
