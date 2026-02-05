# Apache Kafka
- `Kafka`는 고성능 분산 이벤트 스트리밍 플랫폼입니다.
`Kafka`는 아래와 같은 문제점들 때문에 개발되었습니다.
- 시스템 복잡도 증가
- 데이터 일관성 유지 어려움
- 데이터 실시간 처리 어려움
- 확장성 제한
![Image](https://github.com/user-attachments/assets/8cb68488-5f61-419a-829f-2b36e4bba993)
## 1. 프로듀서(Producer)
- `Producer`는 다양한 데이터 소스들 중 데이터를 가져와 `Kafka`의 특정 `Topic`에 메시지를 발행하는 역할을 합니다.
## 2. 브로커(Broker)
- `Broker`는 `Producer`로부터 메시지를 전달 받고 특정 `Topic`에 저장한 뒤, 해당 `Topic`을 구독하는 `Consumer`에게 메시지를 전달하는 역할을 합니다.
이러한 브로커들이 여러 개 모여 `Kafka Cluster`를 구성합니다.
## 3. 컨슈머(Consumer)
- `Consumer`는 `Broker`의 특정 `Topic`을 구독하고 해당 `Topic`에 저장되어 있던 메시지를 전달 받는 역할을 합니다.
`Consumer`는 `Broker`의 `Topic`을 한 개 이상 구독할 수 있고, `Topic`의 `Partition`을 동시에 소비할 수 있습니다.
## 4. 토픽(Topic)
- `Topic`은 `Kafka`에서 데이터를 분류하는 역할을 합니다.
이러한 `Topic`은 여러 `Partition`으로 나뉘어지고, 이러한 `Partition`을 `Broker`가 `Kafka Cluster` 내에서 분산하여 저장합니다.

# Apache Zookeeper
![Image](https://github.com/user-attachments/assets/6642c005-4cf9-4a19-bc44-c2927fc8e24a)
- `Kafka`는 `Zookeeper`를 사용하여 `Kafka Cluster`를 관리합니다.
- `Zookeeper`는 `Broker`, `Topic`, `Partition`등 `Kafka`의 정보를 저장하고 관리하게 됩니다.
그러므로 `Kafka`를 띄우기 위해서는 `Zookeeper`가 반드시 실행해야 되어야 합니다.
## 참고 자료
- https://dkswnkk.tistory.com/705#spring-boot-+-kafka-%EC%97%B0%EB%8F%99
- https://www.youtube.com/watch?v=0lyrd5FlETQ
- https://velog.io/@holicme7/Apache-Kafka-%EC%B9%B4%ED%94%84%EC%B9%B4%EB%9E%80-%EB%AC%B4%EC%97%87%EC%9D%B8%EA%B0%80
- https://aws.amazon.com/ko/what-is/apache-kafka/
- https://sjh9708.tistory.com/151