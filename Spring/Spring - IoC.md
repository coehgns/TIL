# IoC(Inversion of Control)

- 제어의 역전을 의미함.
- 프레임워크가 객체의 생성, 관리, 제어 흐름을 담당하도록 변경하는 개념.
- IoC를 지원하기 위해 ApplicationContext라는 컨테이너를 제공함.

[[ApplicationContext]] : 애플리케이션의 컴포넌트를 생성하고 조립하며 객체의 생명 주기를 관리함.

- Bean으로 등록된 객체에게 의존성을 주입해줌.

## [[Bean]]으로 등록 방법

- Component Scanning
    - @Component Annotation 활용
    - 직접 작성한 Class를 Bean으로 등록해줄 때 사용함.
    - @Component Annotation이 붙어 있는 모든 클래스를 찾아 그 클래스의 인스턴스를 만들고 Bean으로 등록해 주는 작업을 하는 어노테이션 처리기가 스프링에 있음.

## 과정

1. 객체의 생성 및 관리
    - ApplicationContext를 사용하여 빈(Bean)을 생성하고, 관리함.
    - 빈은 Spring이 제어하고, 개발자가 객체의 생성과 관리를 직접 처리하지 않음.
2. 의존성 관리
    - 객체 간의 의존성을 Spring이 주입함.
    - 객체가 필요로 하는 다른 객체를 직접 생성하거나 찾는 대신 Spring 컨테이너가 의존성을 찾아줌.
3. 제어 흐름의 역전
    - 개발자가 코드의 흐름 결정 X
    - 프레임워크가 객체의 생명 주기 및 실행 흐름을 관리

## 참고 자료

- [https://velog.io/@jinyeong-afk/기술-면접-Spring-IoC-Inversion-of-Control와-DI-Dependency-Injection에-대하여](https://velog.io/@jinyeong-afk/%EA%B8%B0%EC%88%A0-%EB%A9%B4%EC%A0%91-Spring-IoC-Inversion-of-Control%EC%99%80-DI-Dependency-Injection%EC%97%90-%EB%8C%80%ED%95%98%EC%97%AC)
- [https://chanhuiseok.github.io/posts/spring-4/](https://chanhuiseok.github.io/posts/spring-4/