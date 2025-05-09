# SAGA Pattern
기존 `Monolithic` 아키텍쳐에서는 `DBMS`가 기본적으로 제공해주는 트랜잭션 기능을 활용하여 데이터를 `commit`하거나 `roolback`할 수 있었지만 `MSA`를 사용하게되면 서비스들이 분산되어 있어 `DBMS`가 제공해주는 기능으로는 트랜잭션을 해결할 수 없습니다. 그래서 나온 것이 `Saga Pattern`입니다.

`Saga Pattern`은 `MSA`에서 서비스끼리 이벤트를 주고 받는 상황에서 한 서비스에 이벤트가 실패할 경우 이전에 작업이 완려된 서비스에 `보상 이벤트`를 발생시켜 **원자성**을 지키는 패턴입니다.

## 이벤트 성공 시
![Image](https://github.com/user-attachments/assets/b511111d-8ebe-4a99-b947-07a98284f71e)

## 이벤트 실패 시
![Image](https://github.com/user-attachments/assets/1e8b7631-3c63-47ff-98bf-305339668eaa)
위와 같이 한 서비스에서 이벤트가 실패하게 되면 이전에 이벤트가 작업되었던 서비스에 트랜잭션 실패 이벤트를 발생시킵니다.

# SAGA 패턴의 종류
## Choreography based SAGA Pattern
![Image](https://github.com/user-attachments/assets/d253a4e7-6254-4095-82ba-9fca7c6783cb)
각각의 서비스에서는 자신의 로컬 트랜잭션을 관리하여 트랜잭션이 종료되면 완료 이벤트를 발행하고, 다음 실행되어야 할 로컬 트랜잭션을 관리하는 서비스가 완료 이벤트를 받고 다음 트랜잭션을 처리하게 됩니다.

![Image](https://github.com/user-attachments/assets/f7d891c4-ac8a-4c51-9f08-7d6cc99f942a)
트랜잭션이 실패하게 되면 서비스에서 실패한 정보를 바탕으로 이벤트를 발생하여 이전 트랜잭션을 완료했던 서비스에게 복구 이벤트를 발행시켜 `Rollback`하게 됩니다. 
## Orchestration based SAGA Pattern
![Image](https://github.com/user-attachments/assets/46e88148-fdfe-4615-94c7-afb844f84675)
트랜잭션을 처리하는 `SAGA 인스턴스`가 존재합니다. 모든 서비스는 `SAGA 인스턴스`에 의해 트랜잭션을 수행하며 결과를 전달하게 되고, 마지막 트랜잭션이 종료되면 `SAGA 인스턴스`를 종료하여 트랜잭션을 전체 종료합니다.

![Image](https://github.com/user-attachments/assets/ce7bcd06-0723-4fb1-8e6b-00b5f045fae2)
만약 트랜잭션이 중간에 실패할 경우 `SAGA 인스턴스`가 `보상 트랜잭션`을 발행하여 일관성을 유지하게 됩니다. 이렇게 중앙에서 서비스에 대한 관리를 해주는 `SAGA 인스턴스`가 있기 때문에 복잡성이 떨어지고 구현과 테스트가 쉽지만, `SAGA 인스턴스`인 `Orchestrator`를 따로 추가해주어야 한다는 단점이 있습니다.
## ​​참고 자료
- https://azderica.github.io/01-architecture-msa/#google_vignette
- https://joobly.tistory.com/69
- https://velog.io/@daehoon12/%EB%A7%88%EC%9D%B4%ED%81%AC%EB%A1%9C%EC%84%9C%EB%B9%84%EC%8A%A4-%ED%8C%A8%ED%84%B4-4.-%ED%8A%B8%EB%9E%9C%EC%9E%AD%EC%85%98-%EA%B4%80%EB%A6%AC-%EC%82%AC%EA%B0%80
- https://devyonghee.github.io/theory/2022/09/24/orchestration-vs-choreography/
- https://devk0ng.github.io/2021/07/27/saga_pattern/#SAGA-Choreography