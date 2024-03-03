# Java - break, continue

- `break`와 `continue`는 반복문에서 사용할 수 있는 키워드임.
- `break`는 반복문을 즉시 종료하고 나감.
- `continue`는 반복문의 나머지 부분을 건너뛰고 다음 반복으로 진행하는데 사용됨.

## **break**

```java
while(조건식) {
  코드1;
  break;  // 즉시 while문 종료로 이동함.
  코드2;
}
//while문 종료
```

- `break`를 만나면 `코드2`가 실행되지 않고 while문이 종료됨.

## **continue**

```java
while(조건식) {
  코드1;
  continue;  // 즉시 조건식으로 이동함.
  코드2;
}
```

- `continue`를 만나면 `코드2`가 실행되지 않고 다시 조건식으로 이동함. 조건식이 참이면 while문을 실행함.

## 참고 자료

- https://www.inflearn.com/course/lecture?courseSlug=김영한의-자바-입문&unitId=194581