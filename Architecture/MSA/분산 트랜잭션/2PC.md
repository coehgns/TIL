# 2PC(2-Phase Commit)
- 분산 트랜잭션 문제인 원자성과 일관성을 보장하기 위한 방법입니다.
- 2PC는 준비 단계와 커밋 단계로 총 두 단계 걸쳐서 진행됩니다.
## 1. 준비 단계(Prepare Phase)
중앙 관리자인 `Coordinator`가 `participant`(`분산 트랜잭션 참여자`)에게 커밋 준비가 되었는지 물어본 후 참여 노드들로부터 `Yes`라는 대답이 오면 커밋 단계로 넘어갑니다. 하지만 이 때 하나의 `participant`라도 대답이 `No`일 경우 커밋 단계로 넘어가지 않습니다.

이 때 `Coordinator`는 사전에 참여하는 데이터베이스의 정보를 미리 알고 있어야하므로 `확장성 문제`가 발생합니다.

<img width="780" height="542" alt="Image" src="https://github.com/user-attachments/assets/b04e8468-fb83-4603-8907-e8912257c6ce" />

## 2. 커밋 단계(Commit Phase)
모든 참여 노드가 `Yes`라고 대답이 올 경우 커밋 명령을 내리게 됩니다. 하지만 하나 이상의 노드가 타임 아웃이 나서 응답이 없거나 `No`라고 답하는 경우 `Rollback` 처리하게 됩니다.

<img width="684" height="514" alt="Image" src="https://github.com/user-attachments/assets/d38f545f-43c3-4619-84aa-d4f23b9a02e9" />

## 2PC의 한계
트랜잭션이 완료될 때까지 트랜잭션 참여자가 데이터에 대해 `락`을 걸게되어 다른 트랜잭션에서 접근하지 못하게 됩니다. 만약 트랜잭션 진행 중 데이터에 `락`을 걸어뒀는데 문제가 발생하여 락 걸린 데이터의 접근 대기가 길어지게 되면 서비스 영향이 커지게 됩니다.

이처럼 `2PC`는 강한 `원자성`과 `일관성`을 보장하지만 운영 측면에서는 효율이 떨어지는 것을 알 수 있습니다.

## 참고 자료
- https://kadensungbincho.tistory.com/125
- https://bezzang2.tistory.com/233
- https://argonautsfleece.tistory.com/112
- https://velog.io/@yangchef/Two-phase-commit-2PC
- https://xonmin.tistory.com/51