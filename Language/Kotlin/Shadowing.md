# Shadowing
- 프로퍼티와 파라미터가 같은 이름을 가질 때, 파라미터가 프로퍼티의 이름를 가리는 현상을 `shadowing(섀도잉)`이라고 합니다.
```Kotlin
fun execute(refreshToken: String): TokenResponse {
    val refreshToken
	// ..
}
```
위와 같이 `execute` 함수의 파라미터인 `refreshToken`과 프로퍼티의 이름인 `refreshToken`이 이름이 같을 경우 `섀도잉` 현상이 발생합니다.

```Kotlin
interface Tree
class Birch: Tree
class Spruce: Tree

// Type parameter "T" is never used
class Forest<T: Tree> {
	// Forest와 addTree의 타입 파라미터가 독립적으로 동작하는 문제
	fun <T: Tree> addTree(tree: T) {
	// ..
	}
}

val forest = Forest<Birch>()

forest.addTree(Birch())
forest.addTree(Spruce())
```
예제 코드를 보면 `Forest` 클래스의 파라미터 타입과 `addTree` 함수의 파라미터 타입이 각각 독립적으로 작동하게 되어 의도치 않은 타입이 전달될 수 있습니다.\

독립적으로 전달되는 것을 의도하였다면 이름을 다르게 하는게 좋습니다.
## 참고 자료
- https://kyucumber.github.io/posts/book/effective-kotlin/effective-kotlin-item-23
- https://gyeong-log.tistory.com/108
- https://onlyfor-me-blog.tistory.com/535