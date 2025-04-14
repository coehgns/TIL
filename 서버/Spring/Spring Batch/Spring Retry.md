# Spring Retry
- `Spring Retry`는 서버에 요청을 보낸 후 실패했을 때 요청을 다시 시도하고, 실패할 경우 다른 메서드를 반환하는 기능이 담긴 라이브러리입니다.
- 요청이 실패하면 실패 지점에 중단을 시키는 `circuit breaker`와는 다르게 `Retry`는 요청을 재시도합니다.
## 과정
![Image](https://github.com/user-attachments/assets/352bc022-c1a8-4d29-9265-9bd124208c23)
1. 클라이언트에서 서버에 이미지 요청을 보냅니다.
2. 서버는 DB에서 이미지를 GET하는 요청을 보냅니다.(이 과정에서 오류 발생)
3. 오류 발생 후 `Retry`는 `DB` 서버에 요청을 다시 보냅니다.
4. 그 후 사진을 `Client`에게 응답을 보냅니다.
## @EnableRetry
- `Retry`를 활성화시키기 위해 `@EnableRetry`를 `SpringbootApplication` 클래스에 작성합니다.
```Kotlin
package com.example.demospringretry  
  
import org.springframework.boot.autoconfigure.SpringBootApplication  
import org.springframework.boot.runApplication  
import org.springframework.retry.annotation.EnableRetry  
import org.springframework.retry.annotation.Retryable  
  
@EnableRetry  
@SpringBootApplication  
class DemoSpringRetryApplication  
  
fun main(args: Array<String>) {  
    runApplication<DemoSpringRetryApplication>(*args)  
}
```

```Kotlin
@Service  
class CreateBoardService(  
    private val boardRepository: BoardRepository  
) {  
  
    companion object {  
        private val logger = LoggerFactory.getLogger(CreateBoardService::class.java)  
    }  
  
    @Retryable(  
        maxAttempts = 3,  
        backoff = Backoff(delay = 1000),  
        include = [RuntimeException::class],  
        recover = "recover"  
    )  
    @Transactional  
    fun execute(request: CreateBoardRequest) {  
        val board = request.run {  
            Board(  
                title = title,  
                content = content  
            )  
        }  
        boardRepository.save(board)  
    }  
  
    @Recover  
    fun recover(e: RuntimeException) {  
        logger.info("recover $e")  
    }  
}
```
## @Retryable
- `maxAttempts`: 요청 재시도 횟수를 정의합니다.
- `backoff`: 요청 재시도 시간 간격을 정의합니다.
- `include`: 재시도 대상을 정의합니다.

	`include`와 `value`는 같은 속성입니다.
## @Recover
- 재요청을 했음에도 실패하면 `@Recover`를 작성한 메서드를 실행합니다.
## 참고 자료
- https://hyeon9mak.github.io/spring-retry/#dependent-libraries
- https://seungpnag.tistory.com/72
- https://velog.io/@ssuh0o0/Spring-Spring-Retry
