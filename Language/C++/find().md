# 1. find()
```C++
#include<algorithm>
find(begin, end, value)
```
- `find()`는 특정 값을 탐색하는 함수입니다.
- `()`안에 `begin`과 `end` 값을 넣고 해당 원소들 중에서 `value`와 일치하는 원소를 탐색에 성공하면 첫 번째 원소의 `iterator`값을 반환합니다.
- 범위 내에 `value` 탐색에 실패하면 `end`를 반환합니다.\
- `<algorithm>` 헤더 파일을 통해 사용 가능합니다.
# 2. string.find()
```C++
#include<string>
string str;
str.find(value);
```
- 문자열에서 `value`를 탐색합니다.
- `value` 탐색에 성공하면 `value`의 첫 번째 인덱스를 반환합니다.
- `value`탐색에 실패하면 쓰레기 값(`string::npos`)을 반환합니다.
## 참고 자료
- https://velog.io/@doorbals_512/C-find-%ED%95%A8%EC%88%98