# Java - 변수

# 변수

- 변수는 이름 그대로 변할 수 있다는 뜻임.

### Var1

```java
package variable;

public class Var1 {
    
    public static void main(String[] args) {
        System.out.println(10);
        System.out.println(10);
        System.out.println(10);
    }
}
```

### 패키지

- 처음으로 패키지를 만듦.
- 패키지는 자바 파일을 구분하기 위한 폴더로 이해하면 됨.
- variable이라는 패키지를 만들었다면, 해당 패키지에 들어가는 자바 파일 첫줄에 package variable; 과 같이 소속된 패키지를 선언해주어야 함.
- 자바 파일이 위치하는 패키지와 package variable 선언 위치가 같아야 함.

```
실행 결과
```

10

10

10

### Var2

```java
package variable;

public class Var2 {

    public static void main(String[] args) {
        int a;  // 변수 선언
        a = 20; // 10 -> 20으로 변경

        System.out.println(a);
        System.out.println(a);
        System.out.println(a);
    }
}
a = 20 실행 결과
```

20

20

20

- a의 값을 변경하면 출력 결과가 모두 함께 변경됨.

## 코드 분석

### 변수 선언

- 숫자 정수 보관소

  `int a`

  - 숫자 정수를 보고나할 수 있는 이름이 a라는 데이터 저장소를 만듦.(변수라고 함.)
  - 변수를 만드는 것을 변수 선언이라고 함.
  - 변수 a에는 숫자 정수 보관 가능.

### 변수에 값 대입

```
a = 10
```

- 자바에서 `=` 은 오른쪽에 있는 값을 왼쪽에 저장한다는 뜻임. (두 값이 같다는 것과는 다른 뜻.)
- 숫자를 보관할 수 있는 데이터 저장소인 변수 a에 값 10을 저장함.
- 선언한 변수에 처음으로 값을 대입해서 저장하는 것을 변수 초기화라고 함.

### 변수 값 읽기

```
System.out.println(a)
```

- 변수에 저장되어 있는 값을 읽어서 사용하는 방법은 변수 이름을 적어주기만 하면 됨.

- 변수 

  ```
  a
  ```

   에 

  ```
  10
  ```

  이 들어가 있다면 자바는 실행 시점에 변수의 값을 읽어서 사용함.

  - System.out.println(a)    // 변수 a의 값을 읽음
  - System.out.println(10)  // a의 값인 10으로 변경, 숫자 10 출력

- 변수의 값은 반복해서 읽을 수 있음.

## 참고 자료

- https://www.inflearn.com/course/lecture?courseSlug=김영한의-자바-입문&unitId=194543