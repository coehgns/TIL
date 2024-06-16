# Bean

- Spring 컨테이너에 의해 관리되는 재사용 가능한 컴포넌트입니다.
- Spring 컨테이너가 관리하는 자바 객체입니다.
- 스프링 컨테이너에 등록된 객체입니다.
- 인스턴스화된 객체를 의미하기도 합니다.

## Bean을 사용하는 이유

- 스프링 간 객체가 의존 관계를 관리하는 것이 큰 목적입니다.
- 객체가 의존 관계를 등록할 때 스프링 컨테이너에서 해당 빈을 찾은 다음에 의존성과 해당 빈은 만듭니다.

## Bean 등록 방법

- xml에 직접 등록
- @Bean 어노테이션 활용
- @Controller, @Service, @Component, @Repository 어노테이션 활용

## xml에 직접 등록

- <bean> 태그를 활용합니다.

```xml
<bean id="helloService" class="com.example.myapp.di.HelloService"/>

<bean id="helloController" class="com.example.myapp.di.HelloController" p:helloService-ref="helloService">		
</bean>
```

## @Bean 어노테이션 활용

```java
@Configurable
@ComponentScan(basePackages= {"com.example.myapp"})
@ImportResource(value= {"classpath:application-config.xml"})
public class AppConfig {
		@Bean
		public IHelloService helloService() {
			return new HelloService();
		}
		
		@Bean
		public HelloController helloController() {
			HelloController controller = new HelloController();
			controller.setHelloService(helloService());
			return controller;
		}
}
```

- 빈에 등록하는 코드입니다.
- 메서드 위에 @Bean 어노테이션을 사용하고, AppConfig 위에 @Configurable, @ComponentScan, @ImportResource 어노테이션을 선언해줍니다.
- 어노테이션을 사용하기 위해서는 xml에 context를 추가해주어야 합니다.

## @**Component, @Controller, @Service, @Repository 어노테이션 활용**

```java
@Controller
public class EmpController {
	
	private IEmpService empService;
	
	@Autowired
	public EmpController(IEmpService empService) {
		this.empService = empService;
	}
	
	void printInfo() {
		int count = empService.getEmpCount(50);
		System.out.println("사원의 수 : " + count);
	}
}
```

- @Controller와 @Autowired를 사용하여 의존성 주입을 한 코드입니다.

## 참고 자료

- [https://dev-wnstjd.tistory.com/440](https://dev-wnstjd.tistory.com/440)