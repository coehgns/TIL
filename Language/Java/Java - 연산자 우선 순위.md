# Java - 연산자 우선 순위

- 자바도 수학과 같이 연산자 우선 순위가 동일함.

### Operator3

```java
package operator;

public class Operator3 {

    public static void main(String[] args) {
        int sum1 = 1 + 2 * 3;  // 1 + (2 * 3)
        int sum2 = (1 + 2) * 3;
        System.out.println("sum1 = " + sum1);
        System.out.println("sum2 = " + sum2);

    }
}
```

**실행 결과**

sum1 = 7 sum2 = 9

- 우선 순위를 변경하려면 괄호`()`를 사용하면 됨.

### 정리

- 연산자 우선 순위는 상식선에서 생각하고, 애매하면 괄호 사용.
- 누구나 코드를 보고 쉽게 명확하게 이해할 수 있어야 함. 개발자들이 연산자 우선순위를 외우고 개발하는 것이 아님.
- 개발에서 가장 중요한 것은 단순함과 명확함임. 애매 복잡 X.

## 참고 자료

- https://www.inflearn.com/course/lecture?courseSlug=김영한의-자바-입문&unitId=194562