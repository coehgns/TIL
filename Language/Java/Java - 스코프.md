# Java - 스코프

# 스코프 - 지역 변수와 스코프

- 변수는 선언한 위치에 따라 지역 변수와 전역 변수로 분류가 됨.
- 지역 변수는 특정 지역을 벗어나면 사용할 수 없음.
- 지역 변수는 자신일 선언된 코드 블록 `{}`안에서만 생존함.
- 자신이 선언된 코드 블록을 벗어나면 제거됨.

### Scope1

```java
package scope;

public class Scope1 {

    public static void main(String[] args) {
        int m = 10;  // m 생존 시작
        if (true) {
            int x = 20;  // x 생존 시작
            System.out.println("if m = " + m);
            System.out.println("if x = " + x);
        } // x 생존 종료

        // System.out.println("main x = " + x);  // 변수 x는 종료되었기 때문에 에러가 남.
        System.out.println("main m = " + m);
    } // m 생존 종료
}
```

**실행 결과**

if m = 10 if x = 20 main m = 10

- 이렇게 변수의 접근 가능한 범위를 스코프(Scope)라고 함.

# 스코프 존재 이유

- **비효율적인 메모리 사용** : `temp` 는 `if` 코드 블록에서만 필요하지만, `main()`코드 블록이 종료될 때 까지 메모리에 유지됨. 따라서 불필요한 메모리가 낭비됨.
- **코드 복잡성 증가**

## 참고 자료

- https://www.inflearn.com/course/lecture?courseSlug=김영한의-자바-입문&unitId=194588
- https://www.inflearn.com/course/lecture?courseSlug=김영한의-자바-입문&unitId=194589