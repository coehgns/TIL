# Java - 배열의 출력

# 배열의 출력

- for문을 사용하여 배열에 저장된 값을 확인할 수 있습니다.

```java
int[] score = {50, 60, 70, 80, 90};

for(int i = 0; i < score.length; i++) {
    System.out.println(score[i]);
}
```

### Arrays.toString(배열이름)

- 배열의 모든 요소를 ‘[첫 번째 요소, 두 번째 요소, …]’와 같은 형식의 문자열로 만들어서 반환합니다.
- `import java.util.Arrays;`  import를 사용해야 합니다.

```java
int[] iArr = { 100, 95, 80, 75, 60};

System.out.println(Arrays.toString(iArr));
```