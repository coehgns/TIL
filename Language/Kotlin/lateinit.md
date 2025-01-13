# lateinit
- `lateinit`은 뜻에서도 알 수 있듯이 초기화를 늦게하는 것 입니다.
- 어떤 객체를 사용해야하는데 첫 정의가 애매한 객체에 `lateinit`을 사용합니다.
- `null` 사용을 지양하는 코틀린에서 첫 정의에 애매한 객체를 `null`로 정의하는 것은 코틀린에서의 어긋나는 행동으로 볼 수 있습니다.

```Kotlin
fun main() {  
    lateinit var title: String  
  
    val content = "cotent는 title임."  
  
    title = content  
  
    println(title)  
}
```
위 예제를 보면 `latieinit`으로 선언된 객체는 `var`로 선언되어 있는데 늦은 초기화 이후에도 `var`선언되어 있기 때문에 `title`의 값이 계속해서 변경될 수 있습니다.
`lateinit`은 값이 계속해서 변경될 수 있다는 속성이 있으므로 `var`로 선언해야 합니다.

만약 `lateinit`으로 객체를 선언해놓고 늦은 초기화를 하지 않는 경우에는 컴파일 시점에서 아래와 같은 예외를 던지게 됩니다.
```kotlin
Exception in thread "main" kotlin.UninitializedPropertyAccessException: lateinit property text has not been initialized
```
## 참고 자료
- https://velog.io/@haero_kim/Kotlin-lateinit-vs-lazy-%EC%A0%95%ED%99%95%ED%9E%88-%EC%95%84%EC%84%B8%EC%9A%94
- https://parade621.tistory.com/35
- https://velog.io/@seojh5939/Why-%EC%BD%94%ED%8B%80%EB%A6%B0-lateinit-%EC%9D%B4%EB%9E%80