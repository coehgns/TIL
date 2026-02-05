# Kafka 멱등성
`멱등성`이란 동일한 작업을 여러 번 실행해도 한 번 실행한 것과 결과가 같은 것을 말합니다.
## 멱등성 Producer
`Producer`가 동일한 요청을 여러 번 보내더라도 `PID`(`Producer unique ID`)와 `Sequence Number`를 함께 보내어 브로커가 해당 메세지의 `PID`와 `Sequence Number`를 통해 중복 여부를 확인하고 해당 메세지가 이미 브로커에 저장되었으면 중복을 방지하여 저장하지 않습니다.

하지만 `Producer`의 문제거 해당 `Producer`가 종료되어 다시 시작하게 되면 `Producer`의 `PID`가 달라지는데, `PID`가 달라지면 브로커는 새로운 메세지로 판단하여 메세지를 저장하게 됩니다.


<img width="1280" height="703" alt="Image" src="https://github.com/user-attachments/assets/86a5135a-9125-4a8e-9a77-34e2cf5c2c1a" />

## Transaction Producer + Consumer
- 하나의 트랜잭션에 Producer와 Consumer를 묶어 처리합니다. 이 때 커밋은 Producer가 합니다.
- 해당 트랜잭션의 격리 수준은 커밋이 성공한 레코드만 읽는 read_commited여야 합니다.
## 참고 자료
- https://dkswnkk.tistory.com/741
- https://yanacoding.tistory.com/227
- https://zave7.github.io/kafka/Kafka-026-%EB%A9%B1%EB%93%B1%EC%84%B1-%ED%94%84%EB%A1%9C%EB%93%80%EC%84%9C/
- https://sehui-ing.tistory.com/114