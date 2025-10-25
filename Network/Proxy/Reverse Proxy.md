# Reverse Proxy
- Reverse Proxy는 클라이언트의 요청을 서버로 전달하고, 서버의 응답을 클라이언트에게 응답해주는 중개자 역할을 합니다.
- Reverse Proxy가 중개자 역할을 함으로써 웹 서버의 부하를 줄여주고, 보안을 강화해주는 다양한 기능을 합니다.
<img width="1239" height="690" alt="Image" src="https://github.com/user-attachments/assets/abd10904-3382-4ce9-9678-149658111efc" />

## Reverse Proxy 동작 방식
1. 클라이언트는 Reverse Proxy로 요청을 보냅니다.
2. 클라이언트의 요청을 받은 Reverse Proxy는 웹 서버에게 요청을 전달합니다.
3. Reverse Proxy로부터 요청을 받은 웹 서버는 요청에 대한 데이터를 처리합니다.
4. 웹 서버가 처리한 데이터를 Reverse Proxy에게 응답해줍니다.
5. 웹 서버의 응답을 받은 Reverse Proxy는 클라이언트에게 응답을 전달합니다.

## Reverse Proxy 필요성
### 1. 로드 밸런싱
- 사용자가 많아지면 트래픽이 많아지면서 서버의 부하가 많이 가게되는데 이를 Reverse Proxy가 여러 웹 서버로 트래픽을 로드밸런싱하여 서버의 부하를 줄여주는 역할을 합니다.
### 2. 보안 강화
- Reverse Proxy는 외부에서 서버에 접근하지 못하도록 되어있어 서버의 보안을 강화해줍니다.
- 클라이언트의 요청이 웹 서버로 바로 가는 것이 아닌, Reverse Proxy를 한 번 거쳐가기 때문에 악성 요청 필터링, 접근 제한 등을 수행하여 보안을 강화합니다.
### 3. 캐싱 및 가속화
- Reverse Proxy는 정적 파일을 캐시에 저장하여 빠르게 제공할 수 있습니다. 이로 인해 응답 시간을 단축하여 서버 성능을 향상할 수 있습니다.

## Reverse Proxy 장점
- 로드 밸런싱
- 보안 강화
- 캐싱
- 웹 서버 최적화

## Reverse Proxy 단점
- 추가적인 서버 설정 및 관리: Reverse Proxy를 사용하면 추가적으로 Proxy 서버에 대해 설정이 필요합니다.
- 네트워크 지연: Reverse Proxy가 클라이언트와 서버 간 중개자 역할을 해주기 때문에 요청에 대한 네트워크 지연이 발생할 수 있습니다.
- 복잡성 증가

## 참고 자료
- https://aday7.tistory.com/entry/%EB%A6%AC%EB%B2%84%EC%8A%A4-%ED%94%84%EB%A1%9D%EC%8B%9CReverse-Proxy-%EC%89%BD%EA%B2%8C-%EC%9D%B4%ED%95%B4%ED%95%98%EA%B8%B0-%EA%B0%9C%EB%85%90%EB%B6%80%ED%84%B0-%ED%95%84%EC%9A%94%EC%84%B1-%EC%98%A4%ED%94%88-%EC%86%8C%EC%8A%A4-%EC%86%94%EB%A3%A8%EC%85%98%EA%B9%8C%EC%A7%80
- https://losskatsu.github.io/it-infra/reverse-proxy/
