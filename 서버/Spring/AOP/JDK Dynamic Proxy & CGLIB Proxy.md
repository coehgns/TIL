# Proxy
`Proxy` 객체에는 기존 타겟 클래스에는 직접적으로 작성되어있지 않은 부가적인 기능(`로깅`, `트랜잭션`, `부가기능`) 로직을 포함하여 `Proxy` 객체가 생성됩니다. 이러므로 기존 서비스의 SRP를 해치지 않고 추가적인 책임을 추가할 수 있습니다.

```Java
@Transactional // 어노테이션만 붙이면 끝
public void registerUser(User user) {
    System.out.println("유저 등록 중..."); // [진짜 핵심 로직]에만 집중
}
```
위 코드처럼 `@Transactional`을 붙임으로써 트랜잭션이 수행되는데 이러한 부가적인 기능은 `Proxy` 객체를 생성하며 해당 `Proxy` 객체 내부 로직에 포함되어있습니다.

이러한 프록시 객체를 생성하는 방식에는 `JDK Dynamic Proxy`와 `CGLIB Proxy`가 있습니다.
## JDK Dynamic Proxy
- 자바에서 지원하는 동적 `Proxy` 구현 방식입니다.
- 타겟 클래스가 구현하고 있는 인터페이스를 똑같이 구현하는 방식입니다. 
	- 이 때 `JDK Dynamic Proxy`는 어떤 인터페이스가 들어올지 모르기 때문에 자바 리플렉션을 사용하여 어떤 인터페이스를 통해 구현할지 찾게됩니다.(`Java Reflection의 invoke()`)
- 타겟 클래스의 인터페이스를 구현하기 때문에 인터페이스가 없으면 에러를 발생합니다.

## CGLiB Proxy
- 인터페이스 없이 타겟 클래스를 상속 받아 `Proxy`를 구현하는 방식입니다.
- 이렇게 타켓 클래스를 상속 받아 구현하기 위해서는 라이브러리를 사용하여 바이트 코드를 조작해야합니다. 이로써 `JDK Dynamic Proxy`의 문제점을 완전히 해결하고 있습니다.
- CGLiB Proxy는 상속을 통해 생성되므로 기본 생성자가 기본적으로 필요하고, 생성자 2번 호출이나 final class, final method 사용에 제약이 있습니다.

`Spring Framework`에서는 `Proxy`를 기존 `JDK Dynamic Proxy`를 통해 생성할 것 인지, `CGLiB Proxy`를 통해 생성할 것인지 설정할 수 있는 `@EnableAspectJAutoProxy`의 `proxyTargetClass` 속성을 제공합니다.

```Java
@SpringBootApplication
@EnableAspectJAutoProxy(proxyTargetClass = true)
public class AtddMembershipApplication {

	public static void main(String[] args) {
	    ...
	}

}
```
## 참고 자료
- https://lob-dev.tistory.com/25
- https://mangkyu.tistory.com/175
