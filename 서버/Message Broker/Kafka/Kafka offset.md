# Kafka offset
`Kafka offset`이란 각 파티션마다 메세지가 저장되는 위치를 말하며 `Consumer` 메세지를 어디까지 읽었는지 저장하는 값을 말합니다.

<img width="1280" height="328" alt="Image" src="https://github.com/user-attachments/assets/d1f540c0-f0fa-4a42-97da-68b86bd24582" />

위 이미지처럼 만약 `offset`이 4라면 `Consumer`는 데이터를 `0, 1, 2, 3`까지 읽은 것 이고 현재 `offset`은 `4`, 다음 `offset`은 `5`가 됩니다.

만약 메세지를 처리 중에 예외가 발생하게 된다면 `Consumer`가 메세지를 제대로 소비하지 못하기 때문에 `offset`은 변하지 않습니다. 하지만 메세지가 제대로 처리 되지 않았을 때 `DLQ`로 이동하게 설정하였다면 메세지 처리 중 예외가 발생하여도 `DLQ`로 메세지가 이동하기 때문에 `offset`이 증가합니다.
## Kafka offset reset 방법
- `latest`: 가장 마지막에 있는 `offset` 부터(default)
- `earliest`: 가장 처음에 있는 `offset` 부터
- `none`: `offset`에 대한 정보가 없을 경우 `예외 throw`

## 참고 자료
 - https://kimmayer.tistory.com/entry/Kafka-offset%EC%97%90-%EB%8C%80%ED%95%B4%EC%84%9C
 - https://velog.io/@so-eun/Kafka-Offset-Consumer-Group-Rebalancing
 - https://eyeballs.tistory.com/343