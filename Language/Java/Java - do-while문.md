# Java - do-while문

- `do-while`문은 `while`문과 비슷하지만, 조건에 상관없이 무조건 한 번은 코드를  실행함.

### do-while문 구조

```java
do {
    // 코드
} while (조건식);
```

### DoWhile2

```java
package loop;

public class DoWhile2 {

    public static void main(String[] args) {
        int i = 10;

        do {
            System.out.println("현재 숫자는:" + i);
            i++;
        } while (i < 3);
    }
}
```

- `do-while`문은 최초 한번은 항상 실행됨. 따라서 `현재 숫자는 : 10`이 출력됨.
- 코드 블럭을 실행 후에 조건식을 검증함.
- `i = 10`이기 때문에 `while (i < 3)` 조건식은 거짓이 되므로 `do-while`문을 빠져나옴.

**출력 결과**

```
현재 숫자는 : 10
```

## 참고 자료

- https://www.inflearn.com/course/lecture?courseSlug=김영한의-자바-입문&unitId=194580