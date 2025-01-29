# deque(double ended queue) container
- `front`와 `back` 양쪽에서 삽입과 삭제가 가능한 구조입니다.
- `vector`의 단점을 보완하기 위해 만들어진 `container`입니다.
- `vector`와 같은 배열 기반의 구조입니다.
### 사용
- 아래와 같이 사용할 수 있습니다.
```C++
#include <deque>
deque<[DataType]> dq;
```
## 기본 함수
- 첫 번째 원소 앞에 데이터 추가.
```C++
dq.push_front(data);
```

- 첫 번째 데이터 제거.
```C++
dq.pop_front();
```

- 마지막 원소 뒤에 데이터 추가.
```C++
dq.push_back(data);
```

- 마지막 데이터 제거.
```C++
dq.pop_back();
```

 - `dq`의 원소의 개수 반환.
 ```C++
 dq.size();
```

- `dq`가 비어있으면 `true`를 반환.
```C++
dq.empty();
```
## 참고 자료
- https://blockdmask.tistory.com/73
- https://velog.io/@kbk5675/C-STL-deque%EB%9E%80
- https://choiiis.github.io/cpp-stl/basics-of-deque-class/