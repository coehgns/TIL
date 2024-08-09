# Access Token과 Refresh Token
- Access Token : Refresh Token에 비해 만료 기간이 짧습니다.
- Refresh Token : Access Token에 비해 만료 기간이 깁니다.

그 이유는 평소에 API 통신할 때에는 Access Token을 사용하여 통신합니다. 이 때 Access Token이 만료되었을 때 Refresh Token을 사용하여 서버에 재발급 요청을 하여 통신합니다.

### Access Token과 Refresh Token을 이용한 통신 과정
1. 클라이언트가 서버에 로그인 요청을 보냅니다.
2. 서버는 클라이언트의 요청을 받고 클라이언트에게 Access Token을 발급해줍니다.
3. 클라이언트는 발급 받은 Access Token을 저장하고, 다음 요청시에 HTTP 헤더에 Access Token을 포함하여 서버에 요청합니다.
4. 서버는 클라이언트의 Access Token을 이용하여 유효성 검증 뒤, 해당 토큰이 유효하다면 인증을 완료합니다.

이 때 만약 Access token이 만료되었다면 클라이언트는 HTTP 헤더에 Refresh Token을 포함하여 서버에 요청하여 Access token을 재발급 받습니다.

하지만 이렇게 통신을 하게 되면 만료 기간이 비교적 긴 Refresh Token이 탈취 당했을 때 보안적으로 문제가 됩니다. 이러한 단점을 보안하기 위해 RTR을 사용합니다.

### RTR(Refresh Token Rotation) 
- RTR이란 access Token이 만료되었을 때 Refresh Token도 함께 만료 시켜버리는 것이다.
이렇게 Refresh Token을 재사용 불가능하게 만들어 보안을 최적화할 수 있습니다.

## 참고 자료
- https://velog.io/@chuu1019/Access-Token%EA%B3%BC-Refresh-Token%EC%9D%B4%EB%9E%80-%EB%AC%B4%EC%97%87%EC%9D%B4%EA%B3%A0-%EC%99%9C-%ED%95%84%EC%9A%94%ED%95%A0%EA%B9%8C