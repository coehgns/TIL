# Queue
- `FIFO(Frist In First Out`의 자료 구조입니다.
- 기본 함수로는 `push`, `pop`, `empty`, `front`, `back`, `swap` 등이 있습니다.
![Image](https://github.com/user-attachments/assets/0dbc1118-3fb8-4b8f-a0fe-3449a44e3f03)
```C++
#include <queue>
queue<int> q;
```
위와 같이 `C++`에서 큐를 사용할 수 있습니다.

### 기본 함수
- 데이터 삽입 함수
```C++
q.push(element);
```

- 데이터 삭제 함수
```C++
q.pop();
```

- 큐의 첫 번째 데이터 반환
```C++
q.front();
```

- 큐의 마지막 데이터 반환
```C++
q.back();
```

- 큐의 사이즈 반환
```C++
q.size();
```

- 큐가 비어있는지 확인
```C++
q.empty();
```

- 두 큐의 내용 변경
```C++
swap(q1, q2);
```
## 참고 자료
- https://life-with-coding.tistory.com/408
- https://sanghyu.tistory.com/83