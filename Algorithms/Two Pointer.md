# Two Pointer
- 1차원 배열에서 순차적으로 접근하면서 두 점의 위치를 기록하며 처리하는 알고리즘입니다.
- 원하는 값을 찾을 때까지 탐색합니다.
## 동작 방식
- `start`, `end`, `target(찾으려고 하는 값)`
1. `start`와 `end`가 첫 번째 원소의 인덱스를 가리킵니다.
2. 현재 부분 합이 `target`과 같가면 카운트합니다.
3. 현재 부분 합이 `target`보다 작다면 end를 1 증가시킵니다.
4. 현재 부분 합이 `target`보다 크면 `start`를 1 증가시킵니다.
5. 모든 경우를 확인할 때 까지 2~4를 반복합니다.
## 시간 복잡도
- `O(N)`
- 매 루프마다 항상 두 포인트 중 하나가 1씩 증가하고 각 포인터가 n번 누적 증가해야 하는 알고리즘입니다.
## 참고 자료
- https://butter-shower.tistory.com/226
- https://velog.io/@heyggun/Algorithm-Two-Pointers-Algorithm-%ED%88%AC-%ED%8F%AC%EC%9D%B8%ED%84%B0-%EC%95%8C%EA%B3%A0%EB%A6%AC%EC%A6%98