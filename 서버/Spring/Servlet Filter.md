# Servlet Filter
`Servlet Filter`는 `Spring Context` 범위 밖인 `DispatcherServlet` 앞단에 존재하며 `DispatcherServlet`으로 요청이 들어가기전에 클라이언트의 요청에 대해서 다음과 같은 역할을 합니다.
## Servlet Filter의 역할
- 공통된 보안 및 인증/인가 관련 작업
- 모든 요청에 대한 로깅과 감사
- 이미지 압축 및 문자열 인코딩

또한 `Servlet Filter`는 `Spring Context` 밖에 위치하고 있기 때문에 톰캣과 같은 `웹 컨테이너`에서 관리됩니다.

아래 이미지처럼 `Filter`에서 필터링 후에 `DispatcherServlet`에게 `ServletRequest`와 `ServletResponse`를 건네게 됩니다. 그 후 요청이 끝나면 `Response`에 대해서 다시 `Servlet Filter`가 필터링을 진행합니다.

<img width="1280" height="779" alt="Image" src="https://github.com/user-attachments/assets/c3f50579-1de4-4aca-9a43-df56a2330ab7" />

예전에는 `웹 컨테이너`에서 관리되어 스프링 빈을 주입하는 것이 까다로웠지만, 현재 `Spring Boot`에서 `DelegatingFilterProxy` 클래스를 통해서 `Filter`를 `웹 컨테이너`가 아닌 **스프링 빈**으로 등록하고 관리할 수 있습니다.

아래 이미지처럼 최전방에서 여러 `Filter`들이 엉켜있는 것을 `Filter Chain`이라고 합니다.

<img width="1280" height="650" alt="Image" src="https://github.com/user-attachments/assets/d59431d6-249b-44d3-a685-2de5602fa8a8" />

## Filter 동작 과정
1. `Filter init`
2. `Filtering`
3. `Filter destory`

```Java
import javax.servlet.*;
import java.io.IOException;

public class GumpFilter implements Filter {
    @Override
    public void init(FilterConfig filterConfig) throws ServletException {
        // FilterConfig를 통한 filter 설정
        // 서블릿 컨테이너가 필터 인스턴스 생성한 후 초기화 하기 위해서 사용 전 호출하는 메소드
    }

    @Override
    public void doFilter(ServletRequest request, ServletResponse response, FilterChain chain)
            throws IOException, ServletException {
        // 필터에서 구현해야 하는 로직을 작성하는 메소드

        // 처리 전
        ...
        chain.doFilter(request, response);
        ...
        // 처리 후
    }

    @Override
    public void destroy() {
        // 필터 인스턴스를 종료시키기 전에 호출하는 메소드
    }
}
```
## 참고 자료
- https://codingcho.tistory.com/207
- https://livenow14.tistory.com/60
- https://gngsn.tistory.com/153#google_vignette
- https://mangkyu.tistory.com/173