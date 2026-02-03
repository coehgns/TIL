# HTTP 2.0
`HTTP 2.0`은 `HTTP 1.0`의 성능을 향상 시키기 위해 탄생한 프로토콜입니다.

`HTTP 1.0`에서는 한 번에 하나의 파일만 전송이 가능했지만 `HTTP 2.0`은 파일 전송이 병렬적으로 이루어져 한 번에 여러 파일을 전송할 수 있습니다.

이렇게 `HTTP 1.0`의 비효율적인 부분과 성능 저하되는 부분들을 `HTTP 2.0`에서 개선되었습니다.
## Binay Framing Layer
- 바이너리 프레이밍이라는 기술은 데이터를 프레임 단위로 쪼개고 `Binary` 형태로 인코딩하는 방법을 말합니다.
- `HTTP/1.0`에서는 `text` 형태로 `Message`가 전송되었지만 `HTTP/2.0`에서는 `Binary` 형태로 인코딩되어 전송되기 때문에 0과 1로 이루어져있어 컴퓨터가 더 빠르게 파싱할 수 있습니다.
- `HTTP/1.1`에서는 `HTTP` 요청과 응답이 하나의 `Message` 단위로 이루어져있었지만 `HTTP/2.0`에서는 `Message` 외에 `Frame`(`Headers Frame`, `Data Frame`)과 `Stream`이라는 데이터의 단위가 추가되었습니다. 이 때 다수의 `Frame`이 하나의 `Message`를 이루게 됩니다.
	- `Stream`은 하나의 `Connection`에서 양방향으로 `Message`를 주고 받는 흐름입니다.

<img width="800" height="452" alt="Image" src="https://github.com/user-attachments/assets/4a478ee7-ba78-4f52-8675-fa40591e2bde" />

정리하면 위 이미지처럼 `HTTP/2.0`은 여러 개의 데이터 `Frame`들이 하나의 `Message`를 이루고, 이러한 `Message`는 하나의 `Stream`에 속하게 됩니다. 그리고 여러 `Stream`이 모여 하나의 `Connection`을 이루게됩니다.

이런식으로 `Message`가 하나의 `Stream`으로 통신하게 되고 이러한 `Stream`이 하나의 `Connection` 안에서 병렬적으로 처리되어 속도가 빠릅니다.

## Multiplexing
위에서 설명한 내용인 `HTTP Message`를 바이너리 형태의 `Frame`으로 나누고 하나의 `Connection` 안에 여러 `Stream`이 순서에 상관 없이 요청과 응답을 주고 받는 것을 `Multiplexing`이라고 합니다.

## Stream Prioritization
이렇게 `Multiplexing`하여 속도 측면에서 확실한 향상이 있었지만 하나의 `Connection`에서 여러 요청과 응답이 뒤섞여버려 패킷 순서가 비순차적인 문제가 발생합니다. 

이 문제를 해결하기 위해 클라이언트는 우선순위 지정 트리를 사용하여 스트림에 식별자를 설정하여 해결하였습니다.
## 참고 자료
- https://inpa.tistory.com/entry/WEB-%F0%9F%8C%90-HTTP-20-%ED%86%B5%EC%8B%A0-%EA%B8%B0%EC%88%A0-%EC%9D%B4%EC%A0%9C%EB%8A%94-%ED%99%95%EC%8B%A4%ED%9E%88-%EC%9D%B4%ED%95%B4%ED%95%98%EC%9E%90
- https://medium.com/@devfallingstar/network-http-2%EC%97%90%EC%84%9C-multiplexing%EC%9D%B4%EB%9E%80-565a7b184c