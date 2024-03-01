# Java - While문

## 반복문

- 반복문은 이름 그대로 특정 코드를 반복해서 실행할 때 사용함.

### 반복문의 종류

- while
- do-while
- for

## While문1

- while문은 조건에 따라 코드를 반복해서 실행할 때 사용함.

```java
while (조건식) {
    // 코드
}
```

- 조건식을 확인함. 참이면 코드 블럭을 실행하고, 거짓이면 while문을 벗어남.
- 코드 블럭이 끝나면 다시 조건식 검사로 돌아가서 조건식을 검사함. (무한 반복)

### While1_2

```java
package loop;

public class While1_2 {

    public static void main(String[] args) {
        int count = 0;

        while (count < 3) {
            count++;
            System.out.println("현재 숫자는:" + count);
        }
    }
}
```

**출력 결과**

```
현재 숫자는:1 현재 숫자는:2 현재 숫자는:3
```

- `while(count < 3)`에 있는 숫자를 `while(count < 100)`으로 변경하면 `while`문읜 코드 블럭을 100번 반복함.

## 참고 자료

- https://www.inflearn.com/course/lecture?courseSlug=김영한의-자바-입문&unitId=194577
- https://www.inflearn.com/course/lecture?courseSlug=김영한의-자바-입문&unitId=194578