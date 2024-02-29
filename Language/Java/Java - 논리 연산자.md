# Java - 논리 연산자

## 논리 연산자

- 논리 연산자는 `boolean`형인 `true`, `false`를 비교하는데 사용함.

**논리 연산자**

- `&&` (그리고) : 두 피연산자가 모두 참이면 참을 반환, 둘 중 하나라도 거짓이면 거짓을 반환.
- `||` (또는) : 두 피연산자 중 하나라도 참이면 참을 반환, 둘 다 거짓이면 거짓을 반환.
- `!` (부정) : 피연산자의 논리적 부정을 반환. 참이면 거짓을, 거짓이면 참을 반환.

### Logical1

```java
package operator;

import java.sql.SQLOutput;

public class Logical1 {

    public static void main(String[] args) {
        System.out.println("&&: AND 연산");
        System.out.println(true && true);
        System.out.println(true && false);
        System.out.println(false && false);

        System.out.println("||: OR 연산");
        System.out.println(true || true);
        System.out.println(true || false);
        System.out.println(false || false);

        System.out.println("! 연산");
        System.out.println(!true);
        System.out.println(!false);

        System.out.println("변수 활용");
        boolean a = true;
        boolean b = false;
        System.out.println(a && b);
        System.out.println(a || b);
        System.out.println(!a);
        System.out.println(!b);
    }
}
```

## 논리 연산자 활용

### Logical2

```java
package operator;

public class Logical2 {

    public static void main(String[] args) {
        int a = 15;
        // a는 10보다 크고 20보다 작다
        boolean result = a > 10 && a < 20;  // (a > 10) && (a < 20)
        System.out.println("result = " + result);
    }
}
```

**실행 결과**

result = true

## 참고 자료

- https://www.inflearn.com/course/lecture?courseSlug=김영한의-자바-입문&unitId=194565