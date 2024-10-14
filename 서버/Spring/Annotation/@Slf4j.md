# @Slf4j 
- Lombok에서 제공하는 어노테이션입니다.
- 해당 어노테인션을 사용하면 자동으로 log 변수를 선언하여 log를 편리하게 남길 수 있습니다.

#### @Slf4j를 사용하지 않았을 때
```java
import org.slf4j.Logger; 
import org.slf4j.LoggerFactory; 

public class Slf4jSample { 
	private static final Logger log = LoggerFactory.getLogger(Slf4jSample.class); 
	
	public static void main(String[] args) { 
		log.info("---------- Log 테스트 ---------"); 
	} 
}
```
#### @Slf4j를 사용하였을 때
```java
import org.slf4j.Logger; 
import org.slf4j.LoggerFactory; 

@Slf4j
public class Slf4jSample { 
	
	public static void main(String[] args) { 
		log.info("---------- Log 테스트 ---------"); 
	} 
}

```
위 코드들과 같이 @Slf4j를 사용하지 않았을 때는 따로 log 변수를 만들어야 하는 불편함이 있습니다.

## 참고 자료
- https://m.blog.naver.com/ygj01069/222422798246
- https://programmer93.tistory.com/64
- https://priming.tistory.com/143