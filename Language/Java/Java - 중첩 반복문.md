# Java - 중첩 반복문

## 중첩 반복문

- 반복문은 내부에 또 반복문을 만들 수 있음.

### Nested1

```java
package loop;

public class Nested1 {

    public static void main(String[] args) {
        for(int i = 0; i < 2; i++) {
            System.out.println("외부 for 시작 i:" + i);
            for(int j = 0; j < 3; j++) {
                System.out.println("-> 내부 for " + i + "-" + j);
            }
            System.out.println("외부 for 종료 i:" + i);
            System.out.println(); // 라인 구분을 위해 실행
        }
    }
}
```

**실행 결과**

외부 for 시작 i:0 -> 내부 for 0-0 -> 내부 for 0-1 -> 내부 for 0-2 외부 for 종료 i:0

외부 for 시작 i:1 -> 내부 for 1-0 -> 내부 for 1-1 -> 내부 for 1-2 외부 for 종료 i:1

- 외부 `for`는 2번, 외부 `for`는 3번 실행됨.
- 외부 `for` 1번당 내부 `for`가 3번 실행되기 때문에 외부(2) * 내부(3)해서 총 6번의 내부 `for` 코드가 수행됨.

## 참고 자료

- https://www.inflearn.com/course/lecture?courseSlug=김영한의-자바-입문&unitId=194584