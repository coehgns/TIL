# Java - 삼항 연산자

## 삼항 연산자

- 단순히 참과 거짓에 따라서 특정 값을 구하는 경우 **삼항 연산자** 또는 **조건 연산자**라고 불리는    `? :` 연산자를 사용할 수 있음.

  `(조건) ? 참_표현식 : 거짓_표현식`

  - 삼항 연산자는 항이 3개라는 뜻임. 특정 조건에 따라 결과가 나오기 때문에 조건 연산자라고도 함.
  - 조건에 만족하면 `참_표현식`이 실행되고, 조건에 만족하지 않으면 `거짓_표현식`이 실행됨.

### CondOp2

```java
package cond;

public class CondOp2 {

    public static void main(String[] args) {
        int age = 17;
        String status = (age >= 18) ? "성인" : "미성년자";
        System.out.println("age = " + age + " status = " + status);
    }
}
```

**실행 결과 분석**

```java
String status = (age >= 18) ? "성인" : "미성년자";  // age = 18
String status = (true) ? "성인" : "미성년자";  // 조건이 참이므로 참 표현식 부분이 선택됨.
String status = "성인";  // 결과
```

## 참고 자료

- https://www.inflearn.com/course/lecture?courseSlug=김영한의-자바-입문&unitId=194573