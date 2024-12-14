## [[싱글턴]]
- 코틀린에서는 `object` 키워드를 이용하여 클래스를 선언하는 동시에 싱글턴 객체를 생성할 수 있습니다.
```Kotlin
package Class  
  
object CarFactory {  
    val cars = mutableListOf<Car>()  
  
    fun makeCar(horsePowers: Int): Car {  
        val car = Car(horsePowers)  
        cars.add(car)  
        return car  
    }  
}  
  
class Car(power: Int)
```
또한 `object`로 선언한 클래스는 다른 클래스를 상속 받을 수도 있고, `interface`를 구현할 수도 있습니다.
## companion object
- 동반 객체인 `companion object`는 외부 클래스의 `private`한 속성도 접근이 가능하기 때문에 주로 팩토리 메서드를 구현할 때 사용됩니다.
- 자바에서 `class` 내부에 `static` 메서드를 사용하는 것과 같습니다.
```Kotlin
class A {
    companion object {
        fun bar() {
            println("Companion object called")
        }
    }
}
```
## 무명 클래스
- 무명 클래스를 선언할 때 `object` 키워드가 사용됩니다. 
- 이때 무명 클래스는 싱글턴 객체가 아니기 때문에 호출 시 매번 객체가 생성됩니다.
```Kotlin
package Class  
  
import java.sql.Array  
  
interface ClickListener {  
    fun onClick()  
}  
  
fun main(args: Array) {  
    setClickAction(object: ClickListener {  
        override fun onClick() {  
            println("click!!")  
        }  
    })  
}  
  
fun setClickAction(clickListener: ClickListener) {  
    clickListener.onClick()  
}
```

## 참고 자료
- https://youngdroidstudy.tistory.com/entry/Kotlin-%EC%BD%94%ED%8B%80%EB%A6%B0%EC%9D%98-object%EC%99%80-class-%ED%82%A4%EC%9B%8C%EB%93%9C
- https://tourspace.tistory.com/109
- https://medium.com/depayse/kotlin-%ED%81%B4%EB%9E%98%EC%8A%A4-10-object-%ED%82%A4%EC%9B%8C%EB%93%9C%EC%9D%98-%EC%82%AC%EC%9A%A9-d7fe736a3dcb