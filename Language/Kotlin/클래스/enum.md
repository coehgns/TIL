enum 클래스는 이름과 동일하게 여러 개의 값을 정해 놓고 사용할 수 있는 클래스입니다.
```Kotlin
enum class Fruit {  
    APPLE,  
    BANANA,  
    GRAPE  
}
```
위 코드처럼 `enum class` 안에 이름을 `,`를 사용해 정해 놓으면 해당 이름들이 그 클래스의 인스턴스가 되는 것 입니다.

`enum class`에서 따로 생성자를 지정하지 않으면 위에서 부터 0, 1 , 2의 값이 정해집니다.
`enum class`는 `name`과 `ordinal`이라는 프로퍼티를 가지는데 `name`은 인스턴스의 이름을 나타내고, `ordinal`은 인스턴스의 순서를 나타냅니다.

```Kotlin
val fruit = Fruit.APPLE
fruit.name //APPLE
fruit.ordinal // 0
```

아래 코드와 같이 정수 값 이외에도 다른 값을 지정해 줄 수 있는데 이런 경우에는 생성자를 지정해주어야 합니다.
```Kotlin
enum class Fruit(price: Int, tag: String) {  
    APPLE(2000, "apple"),  
    BANANA(5000, "banana"),  
    GRAPE(6000, "grape")  
}

val fruit = Fruit.APPLE
fruit.price // 2000
fruit.tag // "apple"
```

이 외에도 `enum class`도 클래스이므로 함수 및 프로퍼티를 추가할 수 있습니다.

## 참고 자료
- https://velog.io/@gjgustjd70/Kotlin-enum-class%EC%97%90-%EB%8C%80%ED%95%98%EC%97%AC-s5r0tt2s
- https://cjw-awdsd.tistory.com/20