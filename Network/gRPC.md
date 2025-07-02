# RPC(Remote Procedure Call)
- 연결된 서버 간의 프로시저를 원격으로 호출할 수 있는 기능임.

# gRPC(Gogole Remote Procedure Call)
- 구글에서 개발한 `RPC` 시스템임.
- 원격에 있는 애플리케이션의 메서드를 로컬 메서드인 것처럼 직접 호출 → 분산 애플리케이션, 서비스를 쉽게 만들 수 있음.
- `HTTP/2`와 `ProtoBuf`를 사용함.

## gRPC - 특징
- HTTP/2를 기반으로 하는 RPC 프레임워크임.
- 서버 간 내부 통신을 빠르게 하기 위하여 사용함.
- 프로토콜 버퍼를 직렬화/역질렬화를 활용하여 데이터를 통신하기 때문에 빠름.
- `IDL`(Interface Definicatoin Language) 기반으로 다양한 언어를 가진 환경에서도 쉽게 확장 가능함.

### HTTP/2
- HTTP/1.1과는 다르게 한 connection으로 동시에 여러 메시지를 주고 받음.
- header를 압축하여 중복 제거 후, 전달하여 효율적임.
- 클라이언트의 요청 없이도 서버가 리소스를 전달 → 클라이언트 요청 최소화 → 서버 과부하가 줄고, 성능 향상

### ProtoBuf(Protocol Buffer)
- 구글에서 개발한 구조화된 데이터 직렬화 기법
- `XML`이나 `JSON`과 같은 텍스트가 아닌 `Binary`로 전송되기 때문에 빠름.
- `Protocol Buffer`로 작업할 때 `proto file`에서 직렬화하려는 데이터 구조를 정의해야 함.

### Proto File
- 사용할 데이터 구조를 `.proto` 파일에 작성하면 프로토콜 버퍼 컴파일러인 `protoc`가 컴파일하여 해당 프로그래밍 언어의 소스 코드와 `Stub` 을 생성함.

## 장점
- 많은 서비스 간의 API 호출로 인한 성능 저하를 개선하여 MSA에 가장 적합한 기술임.

## 단점
- 기존 데이터 통신에 사용했던 `XML`, `JSON`과는 다르게 `Binary`로 직렬화 되어있기 때문에 사람이 해석하기 힘듦.
- 브라우저에서 직접 `gRPC`를 호출하는 것이 불가능함.

## Stub
- 클라이언트에서 서버와 통신할 수 있도록 도와주는 객체를 말함.
- 서버의 메서드를 호출하고 요청 및 응답을 처리하는 역할을 함.

## 과정
![Image](https://github.com/user-attachments/assets/99bd8cfa-9b7d-4b29-a247-90be9a4f3a0a)

## Blocking Stub
- 동기 방식으로 RPC 호출을 함.
- 호출이 완료될 때까지 대기하고, 서버의 응답을 받은 후 다음 동작을 수행함.

## Async Stub
- 비동기 방식으로 RPC 호출을 함.
- 호출이 완료될 때까지 대기하지 않고, 콜백을 통해 다음 동작을 수행함.

## 참고 자료
- [https://velog.io/@letsdev/이-얼마나-쉽고-빠른-gRPC-1-Concept](https://velog.io/@letsdev/%EC%9D%B4-%EC%96%BC%EB%A7%88%EB%82%98-%EC%89%BD%EA%B3%A0-%EB%B9%A0%EB%A5%B8-gRPC-1-Concept)
- [https://velog.io/@qmflf556/gRPC](https://velog.io/@qmflf556/gRPC)
- [https://sh970901.tistory.com/142](https://sh970901.tistory.com/142)
- [https://bcho.tistory.com/1182](https://bcho.tistory.com/1182)
- [https://jammdev.tistory.com/233](https://jammdev.tistory.com/233)
- [https://etloveguitar.tistory.com/107](https://etloveguitar.tistory.com/107)