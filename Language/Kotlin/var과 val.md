# 변수
## 변수 선언
```Kotlin
var 변수명: 타입
val 변수명: 타입

var a: Int = 123
val a: Int = 123

var b: String = "123"
val b: String = "123"
```
코틀린에서 변수를 선언할 때에는 위와 같은 방법으로 변수를 선언합니다.
## var
- 변수값이 변경 가능합니다.
```Kotlin
fun main() {  
    var a: Int = 123  
    a = 444  
    print(a)  
}
```
### val
- 선언시에만 초기화 가능합니다.
- Java의 final과 같습니다.
```Kotlin
fun main() {  
    val a: Int = 123  
    a = 444 // 에러가 발생함.  
}
```
