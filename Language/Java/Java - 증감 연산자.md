# Java - 증감 연산자

# 증감 연산자

- 증가 및 감소 연산자를 줄여서 증감 연산자라고 함.
- 증감 연산자는 `++`와 `--`로 표현되며, 이들은 변수의 값을 1만큼 증가 시키거나 감소 시킴.

### OperatorAdd1

```java
package operator;

public class OperatorAdd1 {

    public static void main(String[] args) {
        int a = 0;

        a = a + 1;
        System.out.println("a = " + a); // 1

        a = a + 1;
        System.out.println("a = " + a); // 2

        // 증감 연산자
        ++a;  // a = a + 1
        System.out.println("a = " + a); // 3
        ++a;
        System.out.println("a = " + a); // 4    
    }
}
```

**실행 결과**

a = 1 a = 2 a = 3 a = 4

- `a = a + 1` 을 `++a`로 간단히 표현할 수 있는 것이 증감 연산자임.
- `++`(증가) `--`(감소)

### 전위, 후위 증감 연산자

- 증감 연산자는 피연산자 앞에 두거나 뒤에 둘 수 있으며, 연산자의 위치에 따라 연산이 수행되는 시점이 달라짐.
- `++a` : 증감 연산자를 피연산자 앞에 둘 수 있음. 전위(Prefix) 증감 연산자라고 함.
- `--a` : 증감 연산자를 피연산자 앞에 둘 수 있음. 후위(Postfix) 증감 연산자라고 함.

### OperatorAdd2

```java
package operator;

public class OperatorAdd2 {

    public static void main(String[] args) {
        // 전위 증감 연산자 사용 예
        int a = 1;
        int b = 0;

        b = ++a;  // a의 값을 먼저 증가시키고, 그 결과를 b에 대입
        System.out.println("a = " + a + ", b = " + b);

        // 후위 증감 연산자 사용 예
        a = 1;
        b = 0;

        b = a++; // a의 현재 값을 b에 먼저 대입하고, 그 후 a의 값을 증가 시킴.
        System.out.println("a = " + a + ", b = " + b);
    }
```

**실행 결과**

a = 2, b = 2 a = 2, b = 1

## 참고 자료

- https://www.inflearn.com/course/lecture?courseSlug=김영한의-자바-입문&unitId=194563