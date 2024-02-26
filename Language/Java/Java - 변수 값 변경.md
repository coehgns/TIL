# Java - 변수 값 변경

## 변수 값 변경

- 변수는 이름 그대로 변할 수 있는 수임.

### Var3

```java
package variable;

public class Var3 {

    public static void main(String[] args) {
        int a;   // 변수 선언
        a = 10;  // 변수 초기화 a(10)
        System.out.println(a);
        a = 50;
        System.out.println(a);
    }
}
실행 결과
```

10

50

- 프로그램은 한 줄씩 순서대로 실행됨.

```java
a = 10;  // 변수 초기화 a(10)   // 1. 변수 a에 10을 저장.
System.out.println(a);         // 2. 변수 a의 값을 읽음. a에는 10일 들어있음. 10 출력. 
a = 50;                        // 3. 변수 a의 값을 50으로 변경함. a(10 -> 50)
System.out.println(a);         // 4. 변수 a의 값을 읽음. a에는 50이 들어왔음. 50 출력.
```

- 변수의 값을 변경하면 변수에 들어있던 기존 값은 삭제됨.

## 참고 자료

- https://www.inflearn.com/course/lecture?courseSlug=김영한의-자바-입문&unitId=194544