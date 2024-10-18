# Docker 아키텍처
- 도커 아키텍처는 내부적으로 클라이언트와 서버의 구조를 지니고 있습니다.
- 도커를 이용하여 클라이언트-서버 구조를 구성하는 아키텍처라고 볼 수 있습니다.
![image](https://github.com/user-attachments/assets/2333f8d9-b911-4fa1-a1bd-379f83a15b57)
### Client
- Docker 아키텍처에서 `Client`는 컨테이너를 관리하거나 실행, 모니터링하고, 이미지를 빌드하고 pull 받을 수 있는 명령어들을 사용하여 `Docker Host`와 상호작용합니다.
- 이러한 명령어들을 실행하면 `Client`가 해당 명령어를 `REST API Call`로 변환 시켜 `Docker Daemon`에게 수신합니다.
- `docker run`, `docker build`, `docker pull`과 같은 명령어들을 사용할 수 있습니다.
### Docker Daemon
- `Clinet`에서 요청한 도커 명령어를 처리하고 컨테이너를 관리하는 백그라운드 프로세스입니다.
- 컨테이너의 생명 주기를 관리하거나 리소스 할당을 합니다.
### Docker Host
- 도커 컨테이너를 실행 시키는데 필요한 가상 머신을 말합니다.
- 컨테이너가 실행되는 환경을 제공합니다.
- `Docker Daemon`을 실행하여 데몬의 역할을 합니다.
- `Client`의 요청을 받아들이고 해당 요청에 맞는 작업을 수행합니다.
### Docker Registry
- `Docker Registry`는 도커 이미지를 저장하고 관리하는 저장소 역할을 합니다.
- 대표적인 `Docker Registry`로 `Docker Hub`가 있습니다. 하지만 규모가 있는 회사에서는 각 회사에서 `Docker Registry`를 직접 구축하여 이미지를 사용하는 경우도 있습니다. 직접 구축하여 이미지를 사용하게 되면 좀 더 안전하게 사용할 수 있습니다.

### 아키텍처 흐름
1. `Client` -> `Docker Host`
	- `Client`에서 컨테이너를 생성, 제거 등 관리하기 위해 `Docker Host`에게 요청을 보냅니다.
2. `Docker Host`
	- `Client`에게로부터 온 요청을 받고 해당 요청에 맞는 작업을 수행합니다.
3.  `Docker Host` -> `Docker Registry`
	- `Client`가 만약 이미지를 생성하거나 업로드를 하려면 `Docker Host`가 해당 이미지를 `Docker Hub`와 같은 `Docker Registry`에 업로드합니다.
4.  `Docker Registry`
	 - 이미지를 저장하고 관리합니다.
5.  `Docker Host` -> `Client`
	- 컨테이너가 종료되면 `Docker Host`는 해당 컨테이너의 결과물을 `Client`에게 반환합니다.
## 참고 자료
- https://velog.io/@koo8624/Docker-%EB%B2%88%EC%97%AD-%EB%8F%84%EC%BB%A4-%EC%95%84%ED%82%A4%ED%85%8D%EC%B2%98-Docker-Architecture-Overview
- https://adjh54.tistory.com/352#3.%20Docker%20%EC%95%84%ED%82%A4%ED%85%8D%EC%B2%98%20%EB%B0%8F%20%ED%9D%90%EB%A6%84-1