# Java - 배열의 복사

# 배열의 복사

- 배열의 저장 공간이 더 필요하다면 보다 큰 배열을 새로 만들고 이전 배열로부터 내용을 복사해야 합니다.

```java
// for문을 이용한 배열 복사 방법.

int[] arr = new int[5];
int arr_length = arr.length;
        
int[] tmp = new int[arr.length * 2];

for(int i = 0; i < arr_length; i++) {
    tmp[i] = arr[i];
}
arr = tmp; // 참조 변수 arr가 새로운 배열을 가리키게 합니다.
```

- 이러한 작업들은 꽤나 비용이 많이 들어가므로 처음부터 배열의 길이를 넉넉하게 잡아주는게 좋습니다.
- 그렇다고 배열의 길이를 너무 크게 잡으면 메모리가 낭비되므로 기존의 2배 정도의 길이로 생성하는 것이 좋습니다.

## System.arraycopy()

- for문 대신 System 클래스의 `arraycopy()`를 사용하면 보다 간단하고 빠르게 배열을 복사할 수 있습니다.
- `arraycopy()` 는 지정된 범위이 값들을 한 번에 통째로 복사합니다.
- `arraycopy()` 를 호출할 때는 어느 배열의 몇 번째 요소에서 어느 배열로 몇 번째 요소로 몇 개의 값을 복사할 것인지 지정해줘야 합니다.

```java
System.arraycopy(num, 0, newNum, 0, num.length);
```

- `num, 0` : num[0]에서

- `newNum, 0` : newNum[0]으로

- ```
  num.length
  ```

  :num.length개의 데이터를 복사합니다.

  - 배열 num의 내용을 배열 newNum으로, 배열 num의 첫 번째 요소(num[0])부터 시작해서 num.length개의 데이터를 newNum의 첫 번째 요소(newNum[0])에 복사합니다.
  - 복사하려는 내용보다 여유 공간이 적으면 에러가 발생합니다.