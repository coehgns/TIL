# Java - 변수 선언과 초기화

## 변수 선언

- 변수를 선언하면 컴퓨터의 메모리 공간을 확보해서 그 곳에 데이터를 저장할 수 있음.
- 변수의 이름을 통해서 해당 메모리 공간에 접근할 수 있음.
- 쉽게 말해 데이터를 보관할 수 있는 공간을 만들고, 그곳에 이름을 부여함.

### Var4

```java
package variable;

public class Var4 {

    public static void main(String[] args) {
        int a;
        int b;

        int c,d;
    }
}
```

- 변수는 하나 씩 선언할 수도 있고 한 번에 여러 변수를 선언할 수도 있음. `int a;` `int c,d;`

## 변수 초기화

- 변수를 선언하고 선언한 변수에 처음으로 값을 저장하는 것을 변수 초기화라고 함.

```java
package variable;

public class Var5 {

    public static void main(String[] args) {
        // 1. 변수 선언, 초기화 각각 따로
        int a;  // 선언
        a = 1;  // 초기화
        System.out.println(a);

        int b = 2;  // 2. 변수 선언과 초기화를 한번에
        System.out.println(b);

        int c = 3, d = 4;  // 3. 여러 변수 선언과 초기화를 한번에
        System.out.println(c);
        System.out.println(d);
    }
}
```

**변수를 초기화 하지 않고 사용하게 되면?**

### Var6

```java
package variable;

public class Var6 {

    public static void main(String[] args) {
        int a;
        System.out.println(a);
    }
}
```

- 다음과 같이 컴파일 에러가 발생함.

```
java: variable a might not have been initialized
```

- 변수가 초기화되지 않았다는 오류임.
- 컴퓨터에서 메모리는 여러 시스템이 함께 사용하는 공간이므로 어떠한 값들이 계속 저장됨. 변수를 선언하면 메모리상의 어떤 공간을 차지하고 사용함. 따라서 초기화를 하지 않으면 이상한 값이 출력될 수 있음.
- 이런 문제를 예방하기 위해 자바는 변수를 초기화 하도록 강제함.

> 참고 : 지금 학습하는 변수인 지역 변수는 개발자가 직접 초기화를 해주어야 함. 클래스 변수와 인스턴스 변수는 자바가 자동으로 초기화를 진행 해줌.

## 참고 자료

- https://www.inflearn.com/course/lecture?courseSlug=김영한의-자바-입문&unitId=194545