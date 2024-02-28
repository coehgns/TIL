# Java - 문자열 더하기

## 문자열 더하기

- 자바는 문자열에도 `+`연산자를 사용할 수 있음. 문자열에 `+`연산자를 사용하면 두 문자를 연결할 수 있음.

### Operator2

```java
package operator;

public class Operator2 {

    public static void main(String[] args) {

        //문자열과 문자열 더하기1
        String result1 = "Hello " + "World";
        System.out.println(result1);

        //문자열과 문자열 더하기2
        String s1 = "string1 ";
        String s2 = "string2";
        String result2 = s1 + s2;
        System.out.println(result2);

        //문자열과 숫자 더하기1
        String result3 = "a + b = " + 10;
        System.out.println(result3);

        //문자열과 숫자 더하기2
        int num = 20;
        String str = "a + b = ";
        String result4 = str + num;
        System.out.println(result4);
    }
}
```

**실행 결과**

Hello World string1 string2 a + b = 10 a + b = 20

**문자열과 숫자 더하기1**

- 자바에서 문자와 숫자를 더하면 숫자를 문자열로 변경한 다음에 서로 더함.

  - ```
    "a + b = " + 10
    ```

    - 문자: `"a + b = "`
    - 숫자 : `10`

**계산 과정**

```java
"a + b = "(String) + 10(int)  // 문자열과 숫자 더하기
"a + b = "(String) + "10"(int -> String)  // 숫자를 문자열로 변경
"a + b = " + "10" // 문자열과 문자열 더하기
"a + b = 10" // 결과
```

## 참고 자료

- https://www.inflearn.com/course/lecture?courseSlug=김영한의-자바-입문&unitId=194561