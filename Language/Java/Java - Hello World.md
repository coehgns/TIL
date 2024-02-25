# Java - Hello World

# 자바 프로그램 실행

## HelloJava

```java
public class HelloJava {

    public static void main(String[] args) {
        System.out.println("Hello java");
    }
}
```

### 주의

- 자바 언어는 대소문자를 구분함. 대소문자가 다른 경우 오류가 발생할 수 있음.

### 실행 결과

- Hello java

## 코드 분석

### public class HelloJava

- HelloJava를 클래스라고 함. (클래스의 개념을 알아야 이해 가능함.)
- HelloJava.java라는 파일을 만들었다고 이해하면 됨.
- 파일명과 클래스 이름이 같아야 함.
- { } 블록을 사용해서 클래스의 시작과 끝을 나타냄.

### public static void main(String[] args)

- main 메서드라고 함. (함수, 메서드의 개념을 학습해야 이해할 수 있음.)
- 자바는 main(String[] args) 메서드를 찾아서 프로그램을 시작함.
- main은 프로그램의 시작점이라고 이해하면 됨.
- { } 블록을 사용해서 메서드의 시작과 끝을 나타냄.

### System.out.println(”Hello java”);

- System.out.println( ) : 값을 콘솔에 출력하는 기능임.
- “Hello java” : 자바는 문자열을 사용할 때 “(쌍따옴표)를 사용함.
- **;** : 자바는 세미콜론으로 문자을 구분함. (문장이 끝나면 세미콜론을 필수로 넣어주어야 함.)

### 실행 과정

1. HelloJava 프로그램을 실행함.
2. 자바는 시작점인 main() 메서드를 실행함.
3. System.out.println(”Hello java”)를 만나고, 문자열 Hello Java를 출력함.
4. main() 메서드의 { } 블록이 끝나면 프로그램은 종료됨.

## 추가 예제

```java
public class HelloJava2 {

    public static void main(String[] args) {
        System.out.println("Hello java1");
        System.out.println("Hello java2");
        System.out.println("Hello java3");
    }
}
```

### 실행 결과

Hello java Hello java2 Hello java3

- 프로그램은 main( )을 시작으로 위에서 아래로 한 줄 씩 실행됨.

## 참고 자료

- https://www.inflearn.com/course/lecture?courseSlug=김영한의-자바-입문&unitId=194539