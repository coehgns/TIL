# Resilience4j
- `Resilience4j`는 `Circuit Breaker`를 지원하는 라이브러리입니다.
# Circuit Breaker
`MSA`와 같은 여러 서비스 간의 통신이 이루어지는 경우 한 서버에서 장애가 발생하면 다른 서버로 장애가 전파될 가능성이 있는데 `circuit breaker`는 서버에 장애가 지속적으로 발생할 경우 호출을 차단하여 장애가 전파되지 않도록 하는 역할을 합니다.

서버에 요청이 실패하면 재시도를 하는 `retry`와는 다르게 `circuit break`는 요청을 차단합니다.

## 과정
사용자와 요청처리 서버, 데이터 저장 서버로 이루어져 있을 때,

1. 사용자는 요청 처리 서버로 데이터를 요청합니다.
2. 요청을 받은 요청처리 서버는 데이터 저장 서버로부터 `circuit breaker`를 사용하여 데이터를 요청합니다. 이 때, 데이터 저장 서버에서 다른 작업으로 인해 지연되어 응답을 받지 못합니다.
3. 데이터 저장 서버가 지연되니 요청처리 서버 또한 지연되어 다른 요청들도 지연되게 됩니다.
4. 이럴 떄 `circuit breaker`를 통해 데이터 저장 서버로 들어오는 요청을 차단하고 미리 저장해둔 `fall back` 응답을 사용하여 사용자에게 장애 상황임을 노출시키지 않고 요청처리 서버의 지연도 방지할 수 있습니다.
## 장점
- 장애 감지 및 격리
- 자동 시스템 복구
- 장애 대안 커스터마이징
- 빠른 실패 및 응답
- 장애 서비스로의 부하 감소
### FSM 기반으로 동작하는 Circuit Breaker
![Image](https://github.com/user-attachments/assets/0b1f1a14-d5ad-41f1-b64c-3b90f6b2ba03)
#### metric 수집 O
 - `CLOSED`: `circuit breaker`를 사용하는 프로세스 간 통신을 할 수 있는 상태를 말합니다.
 - `OPEN`: `circuit breaker`를 사용하는 프로세스 간 통신을 정상적으로 주고 받지 못하는 상태를 말합니다. -> `circuit breaker`는 미리 저장해둔 `fall back`을 응답하거나, `event publisher`를 이용해 이벤트를 발생시킵니다.
 - `HALF_OPEN`: `fall back` 응답을 수행하고 있지만 실패율을 측정하여 `OPEN` 또는 `CLOSED`로 변경할 수 있는 상태를 말합니다.
#### metric 수집 X
 - `DISABLED`: `circuit breaker`를 강제로 `CLOSED` 한 상태를 말합니다.
 - `FORCED_OPEN`: `circuit breaker`를 강제로 `OPEN` 한 상태를 말합니다.

`metric`: 시간이 지남에 따라 변환하는 데이터를 말합니다.(ex. 메모리 사용률, CPU 사용률, 스레드 사용률 등)

`circuit breaker`는 `metric`을 수집하고 분석합니다.
# Sliding window
- `circuit breaker`는 서비스의 호출 결과를 `Sliding window` 형태로 저장합니다.
## Count-based sliding window
- N개 만큼의 측정 결과를 저장합니다.
- N개의 요청 중 요청 1개마다 실패율을 계산합니다.
## Time-based sliding window
- 최근 N초의 실패율을 계산합니다.

전체 대비 실패율을 `failure rate`라고 하고, `failure rate`가 설정된 임계치를 넘어가면 상태가 `OPEN`으로 변경됩니다.
## 참고 자료
- https://hyeon9mak.github.io/spring-circuit-breaker/
- https://lordofkangs.tistory.com/326
- https://mangkyu.tistory.com/261
- https://jaehoney.tistory.com/429
