# Java - String 배열

# 2.1 String 배열의 선언과 생성

```java
String[] name = new String[3];  // 3개의 문자열을 담을 수 있는 배열을 생성합니다.
```

- 3개의 String 타입의 참조 변수를 저장히기 위한 공간이 마련되고 참조형 변수의 기본값은 null이므로 각 요소의 값은 null로 초기화 됩니다.

**변수의 타입에 따른 기본값**

| 자료형           | 기본값        |
| ---------------- | ------------- |
| boolean          | false         |
| char             | ‘\u0000’      |
| byte, short, int | 0             |
| long             | 0L            |
| float            | 0.0f          |
| double           | 0.0d 또는 0.0 |
| 참조형 변수      | null          |

# 2.1 String 배열의 초기화

- int배열과 동일한 방법으로 합니다.

```java
String[] name = new String[3];  // 길이가 3인 STring 배열을 생성
name[0] = "Kim";
name[1] = "Park";
name[2] = "Yi";

// 괄호를 사용해서 초기화
String[] name = new String[]{ "Kim", "Park", "Yi" };
String[] name = { "Kim", "Park", "Yi" };
```