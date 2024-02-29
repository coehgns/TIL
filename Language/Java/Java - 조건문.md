# Java - 조건문

## if문 1 - if, else

- 특정 조건에 따라서 다른 코드를 실행하는 것을 조건문이라고 함.
- 조건문에는 `if문`, `switch문`이 있음.

### if문

`if`문은 특정 조건이 참인지 확인하고, 그 조건이 참(`true`)일 경우 특정 코드 블록을 실행함.

```java
if (condition) {
    // 조건이 참일 때 실행되는 코드
}
```

코드 블록: `{}` (중괄호) 사이에 있는 코드

### else 문

- `else` 문은 `if` 문에서 만족하는 조건이 없을 때 실행하는 코드를 제공함.

```java
if (condition) {
    // 조건이 참일 때 실행되는 코드
} else {
    // 만족하는 조건이 없을 때 실행되는 코드
}
```

### else if

- `else if` 문은 앞선 `if` 문의 조건이 거짓일 때 다음 조건을 검사함. 만약 앞선 `if` 문이 참이라면 `else if` 를 실행하지 않음.

### if-else 코드

```java
if (condition1) {
    // 조건1이 참일 때 실행되는 코드
} else if (condition2) {
    // 조건1이 거짓이고, 조건2가 참일 때 실행되는 코드
} else if (condition3) {
    // 조건2가 거짓이고 조건 3이 참일 때실행되는 코드
} else {
    // 모든 조건이 거짓일 때 실행되는 코드
} 
```

- 특정 조건이 만족하면 해당 코드를 실행하고 `if`문 전체를 빠져 나옴.
- 특정 조건을 만족하지 않으면 다음 조건을 검사함.
- 순서대로 맞는 조건을 찾아보고, 맞는 조건이 있으면 딱 1개의 코드만 실행이 됨.

(`else`는 생략할 수 있음.)

## 참고 자료

- https://www.inflearn.com/course/lecture?courseSlug=김영한의-자바-입문&unitId=194569
- https://www.inflearn.com/course/lecture?courseSlug=김영한의-자바-입문&unitId=194570
- https://www.inflearn.com/course/lecture?courseSlug=김영한의-자바-입문&unitId=194571