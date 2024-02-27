# Java - 변수 타입

## 변수 타입 1

### Var7

```java
package variable;

public class Var7 {

    public static void main(String[] args) {
        int a = 100; // 정수
        double b = 10.5; // 실수
        boolean c = true;  // 불리언(boolean) true, false 입력 가능
        char d = 'A';  // 문자 하나
        String e = "Hello java"; // 문자열, 문자열을 다루기 위한 특별한 타입.

        System.out.println(a);
        System.out.println(b);
        System.out.println(c);
        System.out.println(d);
        System.out.println(e);
    }
}
실행 결과
```

100 10.5 true A Hello java

- 변수는 데이터를 다루는 종류에 따라 다양한 형식이 존재함.

### 변수 타입의 예

- `int` : 정수를 다룸.
- `double` : 실수를 다룸.
- `boolean` : 불리언 타입이라고 함. true, false 값만 사용 가능. 참과 거짓을 판단 할 때.
- `char` : 문자 하나를 다룰 때 사용함. 작은 따옴표(`'`)로 감싸야함.
- `String` : 문자열을 다룸. 큰따옴표`"`를 사용함.

## 리터럴(literal)

- 코드에서 개발자가 직접 적은 `100, 10.5, true, ‘A’, “Hello Java”`와 같은 고정된 값을 프로그래밍 용어로 리터럴이라고 함.

```java
int a = 100;  // 정수 리터럴
double b = 10.5;  // 실수 리터럴
boolean c = true;  // 불리언 리터럴
char d = 'A';  // 문자 하나 리터럴
String e = "Hello Java";  // 문자열 리터럴
```

- 참고 : 리터럴이라는 단어의 어원이 문자 또는 글자를 의미함.

## 변수 타입 2

### Var8

```java
package variable;

public class Var8 {

    public static void main(String[] args) {
        // 정수
        byte b = 127; // -127 ~ 127
        short s = 32767; // -32,768 ~ 32,767
        int i = 2147483647; // -2,147,483,648 ~ 2,147,483,647 (약 20억)

        // -9,223,372,036,854,775,808 ~ 9,223,372,036,854,775,807
        long l = 9223372036854775807L;

        // 실수
        float f = 10.0f;
        double d = 10.0;
    }
}
```

- 메모리를 작세 사용하면 작은 숫자를 표현할 수 있고, 만이 사용하면 큰 숫자를 표현할 수 있음.
- 변수를 선언하면 표현 범위에 따라 메모리 공간을 차지함.

### 변수와 메모리 공간 크기

- 정수형

  - `byte` : -127 ~ 127 (실무에서 거의 사용하지 않음.)
  - `short` : -32,768 ~ 32,767 (실무에서 거의 사용하지 않음.)
  - `int` : -2,147,483,648 ~ 2,147,483,647
  - `long` : -9,223,372,036,854,775,808 ~ 9,223,372,036,854,775,807

- 실수형

  - `float` : 대략 -3.4E38 ~ 3.4E38, 7자리 정밀도 (실무에서 거의 사용하지 않음.)
  - `double` : 대략 -17E308 ~ -1.7E308, 15자리 정밀도

- 기타

  - `boolean` : true, false(1byte)

  - ```
    char
    ```

     : 문자 하나(1byte) (실무에서 거의 사용하지 않음. 문자 하나를 표현할 때도 문자열 사용 가능함.)

    - ex) `String a = “b”`

  - `String` : 문자열을 표현함. 메모리 사용량은 문자 길이에 따라 동적으로 달라짐.

### 리터럴 타입 지정

- 정수 리터럴은 `int`를 기본으로 사용함.
- 실수 리터럴은 기본이 `double`형을 사용함.

## 참고 자료

- https://www.inflearn.com/course/lecture?courseSlug=김영한의-자바-입문&unitId=194546
- https://www.inflearn.com/course/lecture?courseSlug=김영한의-자바-입문&unitId=194547