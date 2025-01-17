# unorderd_map
- `map` 보다 더 빠른 탐색을 할 수 있는 자료 구조입니다.
- 많은 양의 데이터를 저장할 때 성능이 뛰어납니다.
- 데이터를 `key`와 `value`의 형태로 저장합니다.
- 자료를 순서대로 유지하지 않습니다.
- `hash_map`에서 표준으로 정의되어 `unorderd_map`으로 되었습니다.
## 해시를 사용하는 이유
- `vector`나 `list` 같은 경우 시간 복잡도가 `O(N)`이지만 해시 같은 경우 시간 복잡도가 `O(1)`로 만들어주기 때문입니다.

하지만 이러한 `unorderd_map`은 많은 양의 데이터를 저장할 때에 성능이 확실하지만 저장되어있는 데이터의 양이 적을 때에는 메모리 낭비가 발생하게 됩니다.
## 참고 자료
- https://math-coding.tistory.com/31
- https://blog.naver.com/PostView.naver?blogId=do9562&logNo=221754890348