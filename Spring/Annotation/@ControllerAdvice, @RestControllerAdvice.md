# @ControllerAdvice와 @RestController Advice
- 두 어노테이션은 스프링에서 제공하는 전역적으로 예외를 처리하기 위한 어노테이션입니다.
## @ControllerAdvice
```java
@Target({ElementType.TYPE})  
@Retention(RetentionPolicy.RUNTIME)  
@Documented  
@Component  
public @interface ControllerAdvice {  
    ... 
}
```
위와 같이 ControllerAdvice는 @Component 어노테이션이 붙어있기 때문에 ControllerAdvice가 선언된 클래스는 스프링 빈으로 등록됩니다. 그러므로 에러를 전역적으로 핸들링 해주는 클래스를 만들어 어노테이션을 붙여주게 되면 해당 클래스에게 에러 처리를 위임할 수 있게 됩니다.

## @RestControllerAdvice
- @ControllerAdivce와 다르게 @ResponseBody가 붙어있어 응답을 Json으로 내려줍니다.
```java
@Target({ElementType.TYPE})  
@Retention(RetentionPolicy.RUNTIME)  
@Documented  
@ControllerAdvice  
@ResponseBody  
public @interface RestControllerAdvice {  
     ...
}
```
### 장점
- 하나의 클래스를 통해 모든 컨트롤러에 전역적으로 예외 처리가 가능해집니다.
- 직접 정의한 에러 응답을 일관성 있게 클라이언트에게 내려줄 수 있습니다.
- 별도의 try-catch문이 없어 코드의 가독성이 높아집니다.

## 참고 자료
- https://velog.io/@rlvy98/Spring-Global-Exception-Handler-%EB%A7%8C%EB%93%A4%EA%B8%B0
- https://mangkyu.tistory.com/205