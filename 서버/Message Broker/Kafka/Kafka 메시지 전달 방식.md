# Kafka 메시지 전달 방식
`Kafka`의 메시지 전달 방식에는 `At Most Once`, `At Least Once`, `Exactly Once`가 있습니다.
## At Most Once
- 카프카 메세지가 최대 한 번 발송되며 이 과정에서 메시지 중복이 불가능합니다.
- 최대 한 번 발송되기 때문에 발송 도중 문제가 발생하면 데이터가 유실될 수 있습니다.

`정상 처리`
<img width="892" height="281" alt="Image" src="https://github.com/user-attachments/assets/196c9e11-3ded-44ef-a965-1a148fbf7154" />
`문제 발생`
<img width="891" height="413" alt="Image" src="https://github.com/user-attachments/assets/c7c8d44e-f9f6-44a3-afe6-85b8db416436" />
## At Least Once
- 카프카 메세지가 최소 한 번 발송됩니다.
- 메세지가 최소 한 번 발송되므로 네트워크 오류나 재시도 로직으로 인해 재전송되어 메세지 중복이 가능해집니다.
- 데이터 손실을 피할 수 있다는 장점이 있지만 중복 전달이 가능하다는 단점이 있습니다.
- 이러한 중복 전달은 멱등성 구현을 통해서 해결 할 수 있습니다.
## Exactly Once
- 카프카 메세지가 정확히 한 번 발송되며 메세지 손실과 중복이 없는 방법입니다.
## 참고 자료
- https://curiousjinan.tistory.com/entry/kafka-message-delivery-guarantees
- https://dkswnkk.tistory.com/741