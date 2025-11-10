# Cache
- 캐시는 서버에 부하를 줄여주고, 성능을 향상 시키기 위해 사용됩니다.
- 캐시는 값을 저장해두고 저장해둔 값을 가져오기 때문에 값이 잘 변하지 않고 일정한 데이터에 적용하기 알맞습니다.
- 만약 반복적인 작업이지만 매번 값이 다르다면 오히려 성능을 떨어뜨릴 수 있습니다.

# Spring에서 Cache 사용하기 

### 1. CacheConfig
- Spring에서 캐시를 사용하기 위해서는 기본적으로 CacheConfig를 설정해주어야 합니다. 이 때 `@EnableCaching` 어노테이션을 사용해서 캐싱을 활성화시켜주어야 합니다.
```Java
@EnableCaching
@Configuration
public class CacheConfig {
	...
}
```
### 2. 캐시 매니저 빈 추가
CacheConfig를 설정해주었다면 Config 클래스 안에 캐시 매니저 빈을 추가해주어야합니다. 캐시 매니저 빈 종류는 다음과 같습니다.

- `ConcurrentMapCacheManager`
- `SimpleCacheManager`
- `EhCacheCacheManager`
- `CompositeCacheManager`
- `CaffeineCacheManager`
- `JCacheCacheManager`

이러한 캐시 매니저들 중 상황에 맞게 선택하여 사용하면 됩니다.

### 3. @Cacheable, @CacheEvict, @CachePut
#### 1. @Cacheable - 저장 및 조회
- 캐시를 적용할 메서드 위에 `@Cacheable` 어노테이션을 작성하여 적용할 수 있습니다.
- 이 때 캐시된 데이터가 없을 경우 해당 메서드 로직을 실행하고, 캐시된 데이터가 있을 경우 메서드를 실행하지 않고 캐시된 데이터를 가져옵니다.
```Java
@Cacheable("principalName")
public Teacher getPrincipalName(Long teacherId) {
	...	
}
```

위 로직은 교장 선생님의 성함을 가져오는 메서드입니다. `@Cacheable` 어노테이션을 사용하여 캐시를 적용해주고, `@Cacheable` 안에 캐시 이름을 작성할 수 있습니다.

매개변수로 받은 `teacherId`가 key가 되고 키에 해당하는 value로 교장 선생님의 성함이 캐시에 저장됩니다.

#### 2. @CachePut - 저장
- `@CachePut`은 `@Cacheable`처럼 캐시를 저장하지만 조회 시에 캐시된 내용을 사용하지 않고 항상 메서드 로직을 실행하여 캐시에 저장합니다.

#### 3. @CacheEvict - 제거
- 만약 캐시의 값이 달라진다면 캐시를 제거해야하는데 그렇지 못하면 캐시에 저장되어있던 잘 못된 데이터가 반한됩니다.
- 캐시를 제거하는 방법은 일정한 주기로 제거하는 방법과 저장된 값이 달라지면 제거하는 방법이 있습니다.
- Spring에서는 캐시를 제거하기 위해 AOP 기반으로 메서드에 적용할 수 있는 `@CacheEvict` 어노테이션을 제공합니다.
```Java
@CacheEvict(value = "principalName")
public void removePrincipalName {
	...
}
```
다음과 같이 `@CacheEvict`에 캐시 이름을 넣어주면 메서드가 실행될 때마다 캐시에 저장된 데이터를 제거합니다.

`@CacheEvict`는 기본적으로 key 해당되는 데이터만 제거합니다.
```Java
@CacheEvict(value = "book", key = "#book.bookNo")
public void updateBook(Book book) {
	...
}
```

다음과 같이 `@CacheEvict`를 지정해주면 `bookNo`과 같은 키 값을 가진 캐시 데이터를 제거합니다.

## 참고 자료
- https://mangkyu.tistory.com/179
- https://hyeri0903.tistory.com/237