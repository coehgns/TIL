```java
@Configuration
public class 클래스명() {

	@Bean
	public ShineResource shine() {
		return new ShineREsource;
	}
}
```
위 코드와 같이 클래스 위에 @Configuration 어노테이션을 작성 한 뒤, 메소드 위에 @Bean 어노테이션을 작성해주게 되면 수동으로 빈을 등록할 수 있음. 이 때 빈 이름은 메서드 이름으로 결정됨.
스프링 컨테이너는 @Configuration이 붙어 있는 클래스를 자동으로 빈으로 등록하게 됨.
## @Configuration의 역할
- 스프링 컨테이너에서 Bean을 관리할 수 있게 해줌.
- Bean을 등록할 때 [[싱글톤]]이 되도록 보장해줌.
```java
public class MyBean {

	public MyBean() {
		System.out.println("MyBean instance created");
	}
}
```
```java
public class MyBeanConsumer() {

	public MyBeanConsumer(MyBean myBean) {
		System.out.println("MyBeanConsumer created");
		System.out.println("myBean hashcode = " + myBean.hashCode());
	}
}
```
```java
@Configuration
public class AppConfig() {

	@Bean
	public MyBean myBean() {
		return new MyBean();
	}

	@Bean
	public MyBeanConsumer myBeanConsumer() {
		return new MyBeanConsumer(myBean());
	}
}
```
위 코드들을 보면 @Configuration이 사용되었으므로 빈이 싱글톤으로 등록됨. 그러므로 출력은 한 번씩만 되게 됨.
## 참고 자료
- https://blogshine.tistory.com/551