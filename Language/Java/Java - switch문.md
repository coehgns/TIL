# Java - switch문

## switch문

- `switch` 문은 앞서 배운 `if` 문을 조금 더 편리하게 사용할 수 있는 기능임.
- `if`문은 비교 연산자를 사용할 수 있지만, `switch`문은 단순히 값이 같은지만 비교할 수 있음.
- `switch`문은 조건식에 해당하는 특정 값으로 실행할 코드를 선택함.

```java
switch (조건식) {
    case value1:
        // 조건식의 결과 값이 value1일 때 실행되는 코드
        break;
    case value2:
        // 조건식의 결과 값이 value2일 때 실행되는 코드
        break;
    default:
        // 조건식의 결과 값이 위의 어떤 값에도 해당하지 않을 때 실행되는 코드
    }
```

- 조건식의 결과 값이 어떤 `case`의 값과 일치하면 해당 `case`의 코드를 실행함.
- `break`문은 현재 실행 중인 코드를 끝내고 `switch`문을 빠져나가게 하는 역할을 함.
- 만약 `break`문이 없으면, 일치하는 `case` 이후의 모든 `case` 코드들이 순서대로 실행됨.
- `default`는 조건식의 결과값이 모든 `case`의 값과 일치하지 않을 때 실행됨. (`if`문의 `else`와 같음. `default` 구문은 선택.)
- `if`, `else-if` , `else` 구조와 동일함.

### Switch2

```java
package cond;

public class Switch2 {

    public static void main(String[] args) {
        int grade = 2;

        int coupon;
        switch (grade) {
            case 1:
                coupon = 1000;
                break;
            case 2:
                coupon = 2000;
                break;
            case 3:
                coupon = 3000;
                break;
            default:
                coupon = 500;
        }
        System.out.println("발급받은 쿠폰 " + coupon);
    }
}
```

**실행 결과**

```
발급받은 쿠폰 2000
```

**break문이 없으면?**

### Switch3

```java
package cond;

public class Switch3 {

    public static void main(String[] args) {
        int grade = 2;

        int coupon;
        switch (grade) {
            case 1:
                coupon = 1000;
                break;
            case 2:
            case 3:
                coupon = 3000;
                break;
            default:
                coupon = 500;
        }
        System.out.println("발급받은 쿠폰 " + coupon);
    }
}
```

- `grade`가 2등급이라면 `case 2`가 실행됨.
- 하지만 `case 2`에는 `break`문이 없기 때문에 중단하지 않고 바로 다음에 있는 `case 3`의 코드를 실행함.
- `coupon = 3000;`을 수행하고 `break`문을 만나서 `switch`문 밖으로 빠져 나감.
- `발급 받은 쿠폰 3000`이 출력됨.

## 자바 14 새로운 switch문

```java
package cond;

public class Switch4 {

    public static void main(String[] args) {
        int grade = 2;

        int coupon = switch (grade) {
            case 1 -> 1000;
            case 2 -> 2000;
            case 3 -> 3000;
            default -> 500;
        };
        System.out.println("발급받은 쿠폰 " + coupon);
    }
}
```

- 기존 

  ```
  switch
  ```

  문과 차이점

  - `->` 를 사용함.
  - 선택된 데이터를 반환할 수 있음.

## 참고 자료

- https://www.inflearn.com/course/lecture?courseSlug=김영한의-자바-입문&unitId=194572