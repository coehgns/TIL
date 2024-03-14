# Java - overflow

**Casting3**

```java
package casting;

public class Casting3 {

    public static void main(String[] args) {
        long maxIntValue = 2147483647; // int 최고값
        long maxIntOver = 2147483648L; // int 최고값 + 1(초과)
        int intValue = 0;

        intValue = (int) maxIntValue; // int 형변환
        System.out.println("maxIntValue casting = " + intValue);

        intValue = (int) maxIntOver; // 형변환
        System.out.println("maxIntOver casting = " + intValue);
    }
}
```

**출력 결과**

maxIntValue casting = 2147483647 maxIntOver casting = -2147483648

### 초과 범위

- `long maxIntOver = 2147483648L` 를 보면 `int` 로 표현할 수 있는 숫자 중 가장 큰 숫자인 `2147483647`보다 1 큰 숫자를 입력하였습니다.
- 이 숫자는 `int`범위를 넘어가기 때문에 마지막에 `L`을 붙여서 `long` 형을 사용해야 합니다.
- 이 경우 `int`형의 범위를 넘었기 때문에 `long` → `int` 로 형변환을 할 때 문제가 발생합니다.
- 이렇게 기존 범우를 초과해서 표혆게 되면 전혀 다른 숫자가 표현되는 현상을 `오버플로우`라고 합니다.

## 참고 자료

- https://www.inflearn.com/course/lecture?courseSlug=김영한의-자바-입문&unitId=194591