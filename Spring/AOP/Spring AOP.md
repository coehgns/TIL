# AOP(Aspect Oriented Programming)
- 어떠한 로직을 기준으로 여러 부가적인 **관점**으로 나누어서 보고 그 관점을 기준으로 **모듈화**하는 프로그래밍 방법입니다.
	- 이 때 모듈화란 공통적인 로직이나 기능을 하나의 단위로 묶는 것을 말합니다.
- 소스 코드상에서 다른 부분에서 계속 반복해서 사용하는 코드들을 **흩어진 관심사**(Crosscutting Concerns)라고 합니다.

그러므로 **흩어진 관심사**들을 Aspect로 모듈화하고 **비즈니스 로직**에서 분리하여 해당 모듈화한 것을 **재사용**하겠다는 의미입니다.

## Spring AOP 주요 개념
- **Aspect** 
	- 흩어진 관심사를 모듈화 한 것입니다.
- **Target** 
	- Aspect를 적용하는 곳입니다. (클래스, 매서드 등)
	- Advice를 받는 객체이고, Point Cut으로 결정됩니다.
- **Advice**
	- Aspect를 언제 핵심 코드에 적용할지 정의합니다.
	- 실질적인 부가 기능을 담은 구현체입니다.
- **Join Point** 
	- AOP를 적용할 수 있는 모든 지점을 말합니다.
	- 애플리케이션 실행 흐름에서의 특정 포인트입니다. (메서드 호출, 예외 발생, 클래스 초기화 등)
- **Point Cut**
	- Joint Point 중 Advice가 적용될 지점을 선별하는 기능입니다.
- Advisor
	- 하나의 Advice와 하나의 Point Cut으로 구성된 Aspect를 특별하게 지칭하는 말입니다.

## Spring AOP 특징
- Spring Bean에서만 AOP를 적용할 수 있습니다.
- 프록시 패턴 기반의 AOP 구현체입니다.
- 모든 AOP 기능을 지원하는 것이 아닌 Spring IoC와 연동하여 중복 코드나 프록시 클래스 작성의 번거로움, 객체들 간의 관계 복잡도 증가 등의 문제의 해결책을 지원합니다.

## 참고 자료
- https://velog.io/@kai6666/Spring-Spring-AOP-%EA%B0%9C%EB%85%90
- https://engkimbs.tistory.com/entry/%EC%8A%A4%ED%94%84%EB%A7%81AOP
