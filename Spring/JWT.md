# JWT(Json Web Token)
JWT 토큰이란 Json 객체를 이용하여 전송하는 토큰입니다.
주로 클라이언트의 사용자가 인증을 요청할 때 사용됩니다.


```Json
// Json 객체
{
	"students" : [
		{"name" : "Injun"},
		{"name" : "Dohyun"},
		{"name" : "Minsu"}
	]
}
```

## JWT 토큰의 구조
### Header
```Json
{
	"alg" : "HS256",
	"typ" : "JWT"
}
```
Header 부분에는 해당 토큰의 타입을 명시할 수 있고, 정의한 알고리즘을 나타냅니다.
이 때 Base64로 인코딩되어 있습니다.
### Payload
```Json
{
	"iss" : "github.com/coehgns",
	"sub" : 1234567890,
	"exp" : 1385066178,
	"iat" : 1516239022
}
```
Payload 부분에는 claim이 있는데 이 claim은 토큰에 대한 정보가 담겨있습니다.
이 때 Payload는 서명되어 있는게 아닌, Base64로 단순 인코딩되어 있으므로 디코딩하여 정보 확인이 가능합니다. 그러므로 사용자이 중요한 정보는 Payload에 담아두면 안됩니다.

- iss : 토큰의 발급자
- sub : 토큰 제목
- exp : 토큰 만료 시간
- iat : 토큰이 발급된 시간
### Signature
```Json
HMACSHA256(
  base64UrlEncode(header) + "." +
  base64UrlEncode(payload),
  secret)
```
 Signatur 부분에는 Header를 인코딩한 값과 Payload를 인코딩한 값을 합쳐 시크릿 키를 통해 해시를 하여 생성합니다.

## JWT 토큰의 동작 방식
1. 클라이언트가 서버에게 로그인 요청을 보냅니다.
2. 요청을 받은 서버는 클라이언트에게 JWT 토큰을 발급합니다.
3. JWT 토큰을 발급 받은 클라이언트는 JWT 토큰을 저장한 뒤, 다음에 서버에 요청할 때 HTTP 헤더에 JWT 토큰을 넣어 요청을 합니다.
4. 클라이언트의 요청을 받은 서버는 HTTP 헤더에 있는 JWT 토큰을 통해서 유효성을 검증한 뒤, 해당 토큰이 유효하다면 클라이언트의 인증을 완료합니다.

### JWT 토큰의 장단점
### 장점
- 특정 DB에 의존하지 않아도 인증할 수 있습니다.
- 대량의 트래픽이 발생해도 대처할 수 있습니다.
### 단점
- [[세션]] 방식 보다 많은 데이터의 양이 반복적으로 전송되어 네트워크가 저하될 수 있습니다.
- JWT 토큰이 탈취당했을 경우 해당 토큰을 통해 올바르지 않은 사용자가 인증을 할 수 있게 됩니다.

이러한 단점을 보안하기 위해서 [[Access Token과 Refresh Token]]을 사용하기도 합니다.

## 참고 자료
- https://velopert.com/2389
- https://velog.io/@vamos_eon/JWT%EB%9E%80-%EB%AC%B4%EC%97%87%EC%9D%B8%EA%B0%80-%EA%B7%B8%EB%A6%AC%EA%B3%A0-%EC%96%B4%EB%96%BB%EA%B2%8C-%EC%82%AC%EC%9A%A9%ED%95%98%EB%8A%94%EA%B0%80-1
- https://puleugo.tistory.com/138