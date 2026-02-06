# Transaction Isolation Level
`트랜잭션 격리 수준`이란 여러 트랜잭션이 동싱 실행될 때 서로 다른 트랜잭션이 얼마나 격리되었는지 구별하는 수준을 말합니다.
## 트랜잭션 격리 수준 종류
- `SERIALIZABLE`
- `REPEATABLE_READ`
- `READ_COMMITED`
- `READ_UNCOMMITED`
### 1. SERIALIZABLE
- `SERIALIZABLE`은 트랜잭션을 순차적으로 처리합니다.
- 여러 트랜잭션이 동시에 접근할 수 없으므로 순차적으로 실행됩니다. 그렇기 때문에 동시 처리 성능이 떨어집니다.
- 이 방법은 데이터의 부정합 문제를 지키기에 가장 안전하지만 속도 측면에서 가장 성능이 떨어지므로 안전을 중요시하지 않은 작업이면 사용하지 않는 것이 좋습니다.
### 2. REPEATABLE_READ
- `REPEATABLE_READ`는 트랜잭션의 번호를 참고하여 자신 보다 먼저 실행된 트랜잭션의 데이터만 읽는 수준입니다. 이 수준이 가능한 이유는 `Undo 영역` 때문입니다.
	- `Undo 영역`: 트랜잭션 도중에 예외가 발생하면 롤백하기 위해 작업 전 데이터를 저장하는 영역입니다.

그리고 `트랜잭션 ID`로 트랜잭션의 데이터를 보관하여 `Undo 영역`의 데이터를 스냅샷처럼 관리하여 데이터를 보장하는 것을 `MVCC`라고 합니다.

<img width="731" height="571" alt="Image" src="https://github.com/user-attachments/assets/36ae2603-6316-4448-818a-3cd1adc49bed" />

위 이미지처럼 13번 트랜잭션에서 데이터의 변경을 커밋하여도 10번 트랜잭션에서는 13번이 자신보다 늦게 실행되었기 때문에 `Undo 영역`의 데이터를 읽게됩니다. 그러므로 동일한 쿼리를 두 번 날려도 결과 값은 같습니다.

`Dirty Read`: 한 트랜잭션에서 동일한 쿼리를 실행하였지만 첫 조회 후 트랜잭션 커밋의 의해서 두 쿼리의 결과값이 다른 것을 말합니다.
### 3. READ_COMMITED
- `READ_COMMITED`는 다른 트랜잭션에서 커밋된 데이터만 접근할 수 있게 하는 수준입니다.

아래 이미지처럼 10번 트랜잭션이 name 변경 후 커밋되지 않았기 때문에 13번 트랜잭션은 `Undo 영역`에 있는 데이터를 읽습니다.

<img width="726" height="564" alt="Image" src="https://github.com/user-attachments/assets/b89ec4ff-b8f1-4469-9697-c7226c4c0421" />

하지만 이 때 10번 트랜잭션 커밋 후 13번 트랜잭션 커밋 전에 `SELECT 쿼리`가 한 번 더 실행되면 `Non Repeatable Read`가 발생하게 됩니다.
 - `Non Repeatable Read`: 한 트랜잭션(`10번`) 커밋 전, 또 다른 트랜잭션(`13번`) 커밋 전에 실행한 쿼리와 한 트랜잭션(`10번`) 커밋 후, 다른 트랜젹션(`13번`) 커밋 전에 실행한 쿼리의 결과 값이 다른 것을 말합니다.
### 4. READ_UNCOMMITED
- `READ_UNCOMMITED`는 다른 트랜잭션에서 커밋되지 않은 데이터를 접근할 수 있게 하는 수준입니다.

<img width="715" height="695" alt="Image" src="https://github.com/user-attachments/assets/bf607a7f-ad81-45c5-991b-0ee1b578808f" />

위 이미지처럼 10번과 13번 트랜잭션이 시작한 후 10번에서 name을 수정하고 커밋되기 전에 13번에서 데이터에 접근하여 name을 읽게됩니다. 이 때 13번에서는 name을 `"박경"`이라고 조회를 하였지만 이 때 10번 트랜잭션에서 예외가 발생하여 커밋되지 않고 롤백이 되버리고, 13번 트랜잭션은 커밋이 되버리면 데이터가 부정합하기 때문에 해당 수준을 사용하지 않는 것이 좋습니다. 이 상황에서 `Dirty Read`가 발생합니다.
## 참고 자료
- https://velog.io/@gihogihogiho-/%ED%8A%B8%EB%9E%9C%EC%9E%AD%EC%85%98-%EA%B2%A9%EB%A6%AC-Transaction-Isolation-Level-%EA%B0%80-%EB%AD%90%EC%95%BC-%EB%82%B4%EA%B0%80-%EC%95%8C%EB%A0%A4%EC%A4%84%EA%B2%8C
- https://mangkyu.tistory.com/299
- https://tlatmsrud.tistory.com/118