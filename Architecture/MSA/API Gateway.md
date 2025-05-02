# API Gateway
- `API` 서버 앞단에서 모든 `API`서버의 엔드포인트를 단일화해주는 **서버**입니다.
## 주요 기능
### 1. 인증 및 인가
- 분산되어있는 각 서비스에서 인증 및 인가를 진행하게 되면 중복 로직이 발생하고 유지 보수가 어려워집니다. 그렇기 때문에 `MSA`에서 인증 및 인가는 `API Gateway`에서 진행됩니다.
- `API Gateway`에서 인증 및 인가를 처리하게 되면 서비스에서는 순수 비즈니스 로직만을 구현할 수 있어 단일 책임 원칙을 지킬 수 있습니다.

`API Gateway`에서 인증 및 인가를 처리해줌으로써 각 서비스의 부담을 줄여주고, 유지 관리가 쉬워집니다.
### 2. 요청 절차의 단순화
- 여러 클라이언트의 요청이 `API Gateway`를 통해 들어올 때, 여러 요청이 단일화되어 클라이언트와 서버간 통신량을 줄여주어 대기시간이 줄어들고 효율성이 좋아집니다.
### 3. 라우팅 및 로드밸런싱
- `API Gateway`는 클라이언트의 요청 별로 서버에 `로드밸런싱`하고 `라우팅`합니다.
### 4. 서비스 오케스트레이션
- 여러 개의 서비스를 묶어서 새로운 하나의 서비스를 만드는 것을 말합니다. 하지만 오케스트레이션 로직을 과도하게 넣는 것은 `API Gateway`서버의 부담이 늘어 성능을 저하시킬 수 있습니다.
### 5. 서비스 디스커버리
- `API Gateway`에서 서비스를 호출하기 위해서는 각 서비스의 `IP 주소`와 `포트 번호`를 알고 있어야 합니다. 서비스의 `IP 주소`와 `포트 번호`를 알아내는 것을 **서비스 디스커버리**라고합니다.
## 주의 사항
`API Gateway`를 사용할 때 주의할 점이 존재하는데 바로 `병목 현상`과 `네트워크 Latency`입니다.
#### 병목 현상
`마이크로 서비스`에 대해서 많은 양의 요청이 모두 `API Gateway`로 모이면 `병목 현상`이 발생하여 시스템 통신에 문제가 될 수 있습니다. 이를 해결하기 위해서 `API Gateway`에서는 `Scale-Out`을 적절히 수행해야 합니다.

`Scale-Out`: 사용자의 트래픽이 증가함에 따라 서버를 여러 대 추가하여 확장하는 것을 말합니다.

#### 네트워크 Latency
네트워크 상에서 하나의 데이터 패킷이 출발 지점에서 도착 지점으로 이동하는데 걸리는 시간을 `네트워크 Latency`라고 합니다. `MSA`에서 서비스들은 분산 되어있기 때문에 네트워크 상에서 통신을 하게되는데 이 때`네트워크 Latency`가 증가하게 됩니다.
## 참고 자료
- https://velog.io/@tkaqhcjstk/%EC%8A%A4%ED%94%84%EB%A7%81-%ED%81%B4%EB%9D%BC%EC%9A%B0%EB%93%9C-Netflix-Zuul
- https://toss.tech/article/slash23-server
- https://blog.kyobodts.co.kr/2024/01/24/msa-%EC%A7%80%EC%9B%90-%EA%B8%B0%EC%88%A0-rest-api%EC%99%80-api-gateway%EB%9E%80/
- https://velog.io/@tedigom/MSA-%EC%A0%9C%EB%8C%80%EB%A1%9C-%EC%9D%B4%ED%95%B4%ED%95%98%EA%B8%B0-3API-Gateway-nvk2kf0zbj
- https://jizero.github.io/msa1/
- https://wonit.tistory.com/489
- https://dev-coco.tistory.com/143
- https://developer.mozilla.org/ko/docs/Web/Performance/Guides/Understanding_latency