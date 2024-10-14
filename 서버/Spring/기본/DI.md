# DI(Dependency Injection)

- 의존 관계 주입 또는 의존성 주입이라고 불림.
    - 외부에서 의존성을 결정 해줌.
- 객체 간의 의존성을 프레임워크가 주입하는 개념.
- 객체를 직접 생성하는 것이 아닌 외부에서 생성 후 주입 시켜주는 방식.
- 객체 간의 관계를 동적으로 주입하여 유연성을 확보, 결합도를 낮출 수 있음.
- 의존성 주입은 Bean으로 등록된 객체들 끼리만 가능함.

# Spring에서의 DI 방법

- Construct Injection(생성자 주입)
- Field Injection(필드 주입)
- Setter Injection(Setter 주입)

## Construct Injection(생성자 주입)

- 현재 가장 권장되는 의존성 주입 방식.
    - Spring 4.3부터 @Autowired 생략 가능.
        - `@Autowired` : 필요한 의존 객체의 타입에 해당하는 빈을 찾아 주입함.
    - Lombok 라이브러리의 @RequiredArgsContrutor를 함께 사용하면 생성자를 생략 가능함.
- 생성자 주입만이 final 키워드를 사용할 수 있고, 생성자를 통해 주입되는 방식.
    - final 키워드를 사용해서 값이 할당되면 변경할 수 없어 객체의 불변성이 보장됨.

`객체의 불변성` : 생성 후 상태를 변경할 수 없는 객체

```java
@RequiredArgsConstructor
public class Injection {

	private InjectionService injectionService;
	
}
```

- @RequiredArgsConstructor는 Lombok 어노테이션 중에 하나임.
    - @RequiredArgsConstructor는 final 키워드가 붙은 주입에만 생성자를 만들어줌.

## Field Injection(필드 주입)

- Bean으로 등록된 객체를 사용하고자 하는 클래스에 Field로 선언한 뒤 @Autowired를 붙여주면 자동으로 의존 관계가 주입됨.
- @Autowired를 사용하여 객체 내 필드에 선언해서 주입하는 방법
- 참조 관계를 눈으로 확인하기 어렵고, 순환 참조를 막을 수 없음.
- 생성자 이후에 호출되므로 필드에 final 키워드를 사용할 수 없음.

### 장점

- 코드가 간결해짐.

### 단점

- 단일 책임 원칙 주의(SRP)를 위반함.
- Unit Test가 어려움.
- final 키워드 사용 X
    - 불변성 보장 X → 객체가 변할 수 있음.

```java
public class Injection {
	@Autowired
	private InjectionService injectionService;
}
```

## Setter Injection(Setter 주입)

- Spring에서 @Autowired 어노테이션을 사용해서 Setter 메서드를 통해 주입하는 방법
    - @Autowired는 Field, Setter Method, Contructor에 사용 가능함.
- NPE(Null Pointer Exception) 발생 할 수 있음.
- 생성자 이후에 호출되므로 필드에 final 키워드를 사용할 수 없음.

```java
public class Injection {
	
	private InjectionService injectionService;
	
	@Autowired
	public void setInjectionService(InjectionService injectionService) {
			this.injectionService = injectionService;
	}
}
```

## 참고 자료

- [https://velog.io/@khsb2012/자바-객체-지향](https://velog.io/@khsb2012/%EC%9E%90%EB%B0%94-%EA%B0%9D%EC%B2%B4-%EC%A7%80%ED%96%A5)
- [https://backendcode.tistory.com/249](https://backendcode.tistory.com/249)
- [https://velog.io/@jinyeong-afk/기술-면접-Spring-IoC-Inversion-of-Control와-DI-Dependency-Injection에-대하여](https://velog.io/@jinyeong-afk/%EA%B8%B0%EC%88%A0-%EB%A9%B4%EC%A0%91-Spring-IoC-Inversion-of-Control%EC%99%80-DI-Dependency-Injection%EC%97%90-%EB%8C%80%ED%95%98%EC%97%AC)