# data class
- `data class`는 데이터를 다루는데 최적화된 클래스입니다.
- `equals()`, `toString()`, `hashCode()`, `copy()`, `componentX()` 등 총 5개의 메서드를 내부에 자동으로 생성해줍니다.
- `DTO`와 같이 데이터를 전송하기 위한 목적으로 사용되는 경우 `data class`를 사용합니다.
## 특징
- 상속 받을 수 없습니다.
- `val` 또는 `var`로 선언해야 합니다.
- 최소 1개 이상의 프로퍼티를 가지고 있어야 합니다.
## 참고 자료
- https://medium.com/kenneth-android/kotlin-kotlin-data-class-%EC%9D%B4%ED%95%B4%ED%95%98%EA%B8%B0-7d7f51885075
- https://www.youtube.com/watch?v=SKosPXHLT5Q&list=PLQdnHjXZyYadiw5aV3p6DwUdXV2bZuhlN&index=25
- https://hoestory.tistory.com/50