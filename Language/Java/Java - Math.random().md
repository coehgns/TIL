# Java - Math.random()

# Math.random()

- ```
  Math.random() * 숫자
  ```

  - 입력한 숫자보다는 작지만 무한히 가까운 수들이 만들어집니다.

- ```
  ((int) Math.random() * 10 );
  ```

  - 0부터 9까지의 값을 반환합니다.

- ```
  ((int) Math.random() * 10 + 1);
  ```

  - 1부터 10까지의 값을 반환합니다.

```java
// Ex

int[] iArr1 = new int[10];
int iArr1_length = iArr1.length;

for(int i = 0; i < iArr1_length; i++) {
    iArr1[i] = (int) (Math.random() * 10) + 1;  // 1 ~ 10의 값을 배열에 저장
}
```