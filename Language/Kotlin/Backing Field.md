# Backing Field
- 백킹 필드는 프로퍼티의 값을 저장하기 위한 숨겨진 필드를 말합니다.
- 코틀린에서는 핃드를 선언하면 `getter`, `setter`와 같은 접근 메서드를 자동으로 생성 해주므로 프로퍼티를 선언하면 자동으로 백킹 필드가 생깁니다.

- 명시적으로 작성하는 `getter`와 `setter`를 `custom getter`, `custom setter`라고 말합니다.
- field라는 식별자를 통해서 코틀린의 백킹 필드에 접근합니다.

```Kotlin
var String name
```
위와 같이 코틀린에서 필드를 작성하게 되면 아래처럼 `get` 메서드와 `set` 메서드를 내부적으로 **바이트 코드**를 자동 생성해줍니다.

```Kotlin
private String name;
public String getName() { return name; }
publict void setName(String value) { this.name = value; }
```
## 참고 자료
- https://idea-beyond.tistory.com/206
- https://velog.io/@sdhong0609/Kotlin-%EB%B0%B1%ED%82%B9-%ED%95%84%EB%93%9C-Backing-field-%EB%B0%B1%ED%82%B9-%ED%94%84%EB%A1%9C%ED%8D%BC%ED%8B%B0-Backing-property
- https://colour-my-memories-blue.tistory.com/6