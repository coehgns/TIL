# Rollup
- `Rollup`은 사용자의 트랜잭션 요청을 L1 계층인 메인 체인에서 처리하는 것이 아닌, L2 계층에서 오프체인에서 처리하는 것을 말합니다. 오프 체인에서 실행 후 결과만 메인 체인으로 올리게 됩니다.
- 메인 체인이 아닌 L2 계층에서 트랜잭션을 처리할 경우 이더리움과 같은 L1 계층의 부담이 적어지고, 트랜잭션 처리 속도 측면에서 빨라지게 됩니다.
- `Rollup`의 종류에는 `Optimistic Rollup`과 `ZK Rollup`이 있습니다.
# Optimistic Rollup
`Optimistic Rollup`은 사용자의 트랜잭션을 받고 여러 트랜잭션을 `Sequencer`를 통해 순차적으로 정리하여 묶은 후 블록으로 생성하게 됩니다. 이렇게 생성된 블록을 문제가 없다고 가정하고 L1 메인 체인으로 올리게 됩니다. 

메인 체인에 올린 후 이의 제기 기간을 가지게 됩니다. 올린 블록에 문제가 있다면 이의를 제기할 수 있습니다.
이의를 제기하게 될 경우 사기 증명(Fraud Proof)를 통해서 검증하게 됩니다.

이렇게 `Optimistic Rollup`은 트랜잭션의 문제가 없다면 매우 빠르지만, 문제가 있다면 이의 제기로 인해 처리가 오래 걸리게 됩니다.
# ZK Rollup(Zero-Knowledge Rollup)
`ZK Rollup`은 사용자의 트랜잭션을 받고 `Optimistic Rollup`과 마찬가지로 여러 트랜잭션을 `Sequencer`를 통해서 순차적으로 정리한 후 블록을 생성합니다. 

`Optimistic Rollup`이였다면 올바르다고 가정하고 메인 체인에 올렸겠지만 `ZK Rollup`은 `ZK Prover`를 통해서 해당 트랜잭션이 올바르다는 것을 의미하는 증명을 생성하게 됩니다. 생성된 증명을 L1 메인 체인으로 올리고, 메인 체인에서는 해당 증명을 검증하여 확정 짓게 됩니다.

이렇게 `ZK Rollup`은 `ZK Prover`로 인해 증명을 생성하는 과정을 거치기 때문에 구현이 복잡하고, 비용 측면에서 비쌉니다. 하지만 트랜잭션이 올바르다는 가정이 아닌, 확실한 증명을 메인 체인에 올리기 전에 생성하기 때문에 보안성이 좋습니다.

## 참고 자료
- https://www.ledger.com/ko/academy/%EC%A3%BC%EC%A0%9C/blockchain/%EB%B8%94%EB%A1%9D%EC%B2%B4%EC%9D%B8-%EB%A1%A4%EC%97%85%EC%9D%B4%EB%9E%80
- https://onekey.so/blog/ko/ecosystem/what-are-blockchain-rollups/?srsltid=AfmBOorffkS_XINj6zlWcMZ_kUqrZrtSkYOYewqtn4eM9iNETtq-bNjj