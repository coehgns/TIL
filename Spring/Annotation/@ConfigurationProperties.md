## @ConfigurationProperties
- `.properties`파일이나 `.yml`파일에 있는 `property`를 자바 클래스에 바인딩하여 사용할 수 있도록 해주는 어노테이션입니다.

Spring boot에서는 사용할 때 필요한 정보를 `.properties`파일이나 `.yml`파일에서 key와 value의 형태로 써두고 관리하게 됩니다.

이때, `@ConfigurationProperties`어노테이션을 사용하지 않고 `@Value`어노테이션을 사용하여 클래스에 바인딩을 해줄 수 있습니다.
```properties
site-url.naver=https://www.naver.com 
site-url.google=https:/google.com
```
```Java
@Value("${site-url.naver}") 
private String naver; 

@Value("${site-url.google}") 
private String google;
```
위 처럼 `@Value`어노테이션을 사용할 수 있지만 이렇게 사용하게 되면 오타가 날 확률이 늘어나게 됩니다.

아래와 같이 `@ConfigurationProperties`를 사용하여 `property`의 값을 사용하게 되면 매핑을 좀 더 유연하게 할 수 있고, 코드를 좀 더 깔끔하게 작성할 수 있습니다.
```Java
@Component 
@ConfigurationProperties(prefix = "site-url") 
@Data 
public class siteUrlProperties { 
	private String naver; 
	private String google;
}
```
`@ConfigurationProperties`어노테이션을 사용할 때에는 위와 같이 `prefix`를 지정해주고, `@Component`어노테이션을 사용해 `bean`으로 등록해주어야 합니다.
## 참고 자료
- https://programmer93.tistory.com/47
- https://blog.yevgnenll.me/posts/spring-configuration-properties-fetch-application-properties