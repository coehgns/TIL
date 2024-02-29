# Java - 비교 연산자

## 비교 연산자

- 비교 연산자는 두 값을 비교하는 데 사용함. 비교 연산자는 주로 뒤에서 설명하는 조건문과 함께 사용함.

**비교 연산자**

- `==` : 동등성
- `!=` : 불일치
- `>` : 크다
- `<` : 작다
- `>=` : 크거나 같다
- `<=` : 작거나 같다
- 비교 연산자를 사용하면 참(`true`) 또는 거짓(`false`)이라는 결과가 나옴.
- 참 거짓은 `boolean` 형을 사용함.

**주의할 점**

- `=`와 `==` 는 다름.
- `=` : 대입 연산자
- `==` : 동등한지 확인하는 비교 연산자.
- 불일치 연산자는 `!=` 를 사용함. `!` 는 반대라는 뜻임.

## **문자열 비교**

- 문자열이 같은지 비교할 때는 `==` 이 아니라 `.equals()` 메서드를 사용해야 함.

### Comp2

```java
package operator;

public class Comp2 {

    public static void main(String[] args) {
        String str1 = "문자열1";
        String str2 = "문자열2";

        boolean result1 = "hello".equals("hello");  // 리터럴 비교
        boolean result2 = str1.equals("문자열1");  // 문자열 변수, 리터럴 비교
        boolean result3 = str1.equals(str2);  // 문자열 변수 비교

        System.out.println(result1);
        System.out.println(result2);
        System.out.println(result3);
    }
}
```

**실행 결과**

true true false

## 참고 자료

- https://www.inflearn.com/course/lecture?courseSlug=김영한의-자바-입문&unitId=194564