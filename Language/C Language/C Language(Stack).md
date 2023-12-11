# Stack

## Stack

- 한쪽으로만 데이터를 넣고 뺄 수 있는 형태의 데이터 구조.
- 후입 선출(Last in,First Out)이라는 특성을 지니고 있음.

![Untitled](https://prod-files-secure.s3.us-west-2.amazonaws.com/07ac647d-0fae-4c52-a212-6a3030b53860/dc519113-e9b6-4314-8a7e-fab0a24fef49/Untitled.png)

- 스택은 그림과 같이 한쪽으로만 데이터를  넣고(pssh) 뺄(pop) 수 있음.
- 스택은 가장 위에 있는 자료를 확인(peek), 스택이 비어(isEmpty)있는지 확인 할 수 있음.

### 추상 자료형

```c
Stack<T> {
  push(T);
  pop();
  peek();
  isEmpty();
}
```

------

## 스택 구현

### 배열을 이용하여 스택 구현

```c
#define STACK_SIZE 10  //STACK_SIZE 라는 매크로 정의

int top = -1;   
int stack[STACK_SIZE];
```

- top: 스택 최상단 자료의 위치를 나타내는 변수.
- stack: 자료를 저장할 배열(스택 공간)