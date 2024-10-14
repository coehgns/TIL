# GlobalExceptionHandler
- 애플리케이션 전역에서 예외를 처리하고 사용자에게 응답을 제공하는 메커니즘입니다.
- [[@ControllerAdvice, @RestControllerAdvice]] 와 **@ExceptionHandler** 어노테이션을 통해 Controller에서 발생하는 에러를 해당 핸들러에서 캐치하여 오류를 발생시키지 않고 사용자에게 에러 메시지를 반환합니다.
```java
package com.example.springjwt.global.error;  
  
import com.example.springjwt.global.error.exception.BusinessException;  
import com.example.springjwt.global.error.exception.ErrorCode;  
import lombok.extern.slf4j.Slf4j;  
import org.springframework.http.HttpStatus;  
import org.springframework.http.ResponseEntity;  
import org.springframework.web.bind.annotation.ExceptionHandler;  
import org.springframework.web.bind.annotation.RestControllerAdvice;  
  
@Slf4j  
@RestControllerAdvice  
public class GlobalExceptionHandler {  
  
    @ExceptionHandler(BusinessException.class)  
    public ResponseEntity<ErrorResponse> handleBusinessException(
	    BusinessException e
	) {  
        ErrorCode errorCode = e.getErrorCode();  
        ErrorResponse errorResponse = ErrorResponse.of(
        errorCode, errorCode.getMessage()
        );  
  
        return new ResponseEntity<>(
        errorResponse, HttpStatus.valueOf(errorCode.getStatusCode())
        );  
    }  
  
    @ExceptionHandler(Exception.class)  
    public ResponseEntity<ErrorResponse> handleException(Exception e) {  
        ErrorCode errorCode = ErrorCode.INTERNAL_SERVER_ERROR;  
        ErrorResponse errorResponse = ErrorResponse.of(
        errorCode, errorCode.getMessage()
        );  
  
        return new ResponseEntity<>(
        errorResponse, HttpStatus.INTERNAL_SERVER_ERROR
        );  
    }  
}
```
- [[@Slf4j]] 어노테이션을 사용하여 예외 발생 시 클래스에 로깅 기능을 자동으로 추가하기 위해 사용하였습니다.
## 참고 자료
- https://velog.io/@rlvy98/Spring-Global-Exception-Handler-%EB%A7%8C%EB%93%A4%EA%B8%B0
- https://github.dev/EntryDSM/EntryRepo-Backend-Assignment/blob/main/src/main/java/com/practice/board/global/security/jwt/JwtFilter.java