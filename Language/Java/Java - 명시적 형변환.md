# Java - 명시적 형변환

# 명시적 형변환

**Casting2**

```java
package casting;

public class Casting2 {

    public static void main(String[] args) {
        double doubleValue = 1.5;
        int intValue = 0;

        // intValue = doubleValue;  컴파일 오류 발생

        intValue = (int) doubleValue;  // 형변환
        System.out.println("intValue = " + intValue);
    }
}
```

- `int`형은 `double`형 보다 숫자의 표현 범위가 작으므로 실수를 표현할 수 없습니다.
- 이 경우 숫자가 손실되는 문제가 발생할 수 있습니다.
- 하지만 이런 위험을 개발자가 직접 감수하고도 값을 대입하고 싶다면 데이터 타입을 강제로 변경할 수 있습니다.

```java
// 다음과 같이 변환하고 싶은 데이터 타을 괄호를 사용하여 명시적으로 입력하면 됩니다.
intValue = (int) doubleValue; // 형변환
```

- 이렇게 개발자가 직접 형변환 코드를 입력한다고 하여 명시적 형변환이라고 합니다.

## 명시적 형변환 과정

```java
//doubleValue = 1.5
intValue = (int) doubleValue;
intValue = (int) 1.5; // doubleValue에 있는 값을 읽습니다.
intValue = 1; // (int)로 형변환 합니다.
              // intValue에 int형 숫자 1을 대입니다.
```

- 형변환을 한다고 하여 doubleValue 자체의 타입이 변경되거나 그 안에 있는 값이 변경되는 것은 아닙니다.

## 참고 자료

- https://www.inflearn.com/course/lecture?courseSlug=김영한의-자바-입문&unitId=194591