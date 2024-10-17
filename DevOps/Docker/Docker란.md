# 도커
- Go로 작성된 리눅스 컨테이너 기반의 가상화 플랫폼입니다.
- 도커를 사용하면 애플리케이션을 신속하게 구축, 테스트하고 배포할 수 있습니다.
## 컨테이너
- 컨테이너는 가상화 기술 중 하나입니다.
- 이러한 컨테이너는 가상화로 프로세스를 격리된 환경에서 동작하는 방식을 말합니다.
- 컨테이너 안에는 프로세스를 실행시키는데 필요한 `소스 코드`, `라이브러리`, `런타임` 등이 포함되어있습니다.
## Docker Image
- 도커 이미지란 컨테이너를 실행 시킬 수 있는 실행 파일과 설정 값들을 가지고 있습니다.
- 이러한 도커 이미지를 컨테이너에 담고 run을 하게 되면 프로세스가 동작하게 됩니다.
![image](https://github.com/user-attachments/assets/70d0e8cb-e723-4aec-9549-2e9791171437)
위 그림에서 ubuntu 이미지를 만들기 위해 Layer A, B, C가 들어갑니다. 그리고 nginx 이미지를 만들려고 하는데 이 때, 기존에 있던 ubuntu 이미지 Layer들 위에 쌓이게 됩니다. 그 후 web app 이미지를 만들기 위해 마찬가지로 기존에 있던 요소들 위에 web app source가 쌓이게 됩니다. 이렇게 만들어진 `web app image layers 이미지`를 `Docker Container`에 포함하여 run을 시키면 해당 프로세스가 동작하게 됩니다.
## Docker File
- Docker File은 Docker image를 구성하기 위한 명령어들을 작성하여 이미지를 구성할 수 있습니다.
```Dockerfile
FROM openjdk:17
ARG JAR_FILE=/build/libs/*.jar
EXPOSE 8080
COPY build/libs/SpringJWT-0.0.1-SNAPSHOT.jar app.jar
ENTRYPOINT ["java","-jar","/app.jar"]
```
위처럼 작성한 도커 파일을 빌드하게 되면 도커 이미지가 생성됩니다!
![image](https://github.com/user-attachments/assets/0274d612-0876-4aac-9dc3-47ee3119bfa1)
## 참고 자료
- https://fastcampus.co.kr/courses/211368/clips/
- https://aws.amazon.com/ko/docker/
- https://khj93.tistory.com/entry/Docker-Docker-%EA%B0%9C%EB%85%90