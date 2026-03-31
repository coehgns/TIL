# TCC(Try Confirm Cancel)
`TCC 패턴`은 분산되어있는 마이크로서비스에서 `데이터의 일관성`을 지키기 위한 패턴 중 하나입니다.

<img width="797" height="369" alt="Image" src="https://github.com/user-attachments/assets/c3625c19-fb70-4831-9cd9-b403604eddb6" />

위 이미지처럼 `Try`로 사용할 자원을 예약하고, 오류가 없다면 `Confirm`(`커밋`)하게 됩니다.
이 때 만약 오류가 있거나 `Confirm` 과정에서 오류가 발생하면 `Cancel`(`롤백`)하거나 `Timeout`하여 예약한 자원을 해제합니다.

원서를 생성 하는 마이크로 서비스와 원서 생성 서비스에서 이벤트를 받아 원서 상태를 생성하는 마이크로 서비스가 있다고 가정할 때, 원서 생성 서비스의 `Try` 시점에서 자원을 예약하고 예외가 발생하지 않으면 `Confirm`(`커밋` 혹은 `원서 상태 서비스로 이벤트 발행`)하고, 예외가 발생하면 `Cancel`(`롤백`)합니다.

## 장점
### 1. 강한 일관성
- `Try` 단계에서 자원에 대해 예약이 가능한지 검증 후 예약하므로 데이터 일관성이 강합니다.
### 2. 단위 제어
- `Try는` `자원 예약`, `Confirm`은 `커밋`, `Cancel`은 `롤백`으로 해당 시점에서 행위가 명확합니다.
## 단점
### 1. 구현 복잡도
- 모든 서비스가 `Try`, `Confirm`, `Cancel` 3단계를 모두 각각 구현해야하므로 구현 난이도가 증가합니다.
### 2. 리소스 점유
- `Try` 단계에서 자원을 예약(`락`)해두기 때문에 `Confirm` 혹은 `Cancel`이 늦어질 경우 다른 요청이 해당 자원에 접근하지 못하게 됩니다.
### 3. 성능 저하
- `Try`, `Confirm`, `Cancel` 3단계이므로 호출 횟수가 많아져 `Latency` 증가합니다.

## 참고 자료
- https://khjk.tistory.com/268
- https://velog.io/@shlee327/%EB%B6%84%EC%82%B0-%ED%8A%B8%EB%9E%9C%EC%9E%AD%EC%85%98-%ED%8C%A8%ED%84%B4%EB%93%A4-SAGA-TCC-2PC3PC-MSA%EC%97%90%EC%84%9C%EC%9D%98-%EB%8D%B0%EC%9D%B4%ED%84%B0-%EC%9D%BC%EA%B4%80%EC%84%B1