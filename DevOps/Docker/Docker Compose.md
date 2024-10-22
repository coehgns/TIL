# Docker Compose
- 하나의 서버에서 여러 개의 `컨테이너`를 실행시키고 관리할 수 있는 환경을 제공해주는 도구입니다.
- 애플리케이션을 구축하는데 필요한 명령어를 하나의 텍스트 파일로 정의하여 명령어를 한 번에 전체를 실행하고 종료할 수 있습니다.
- 이렇게 정의된 파일에서는 `컨테이너`나 `볼륨`을 어떠한 방식으로 만들지 설정할 수 있습니다.
## Docker Compose 구조
- `도커 컴포즈`는 애플리케이션을 구축하는데 필요한 명령어들을 하나의 `YAML`파일로 정의하고, 애플리케이션 전체를 실행(`run`)하거나 전체를 종료(`down`)할 수 있습니다.
- 여러 개의 `컨테이너`의 옵션과 환경을 정의한 파일을 읽어 순차적으로 `컨테이너`를 생성하는 방식으로 동작합니다.
- `컨테이너`를 생성하는 파일을 정의할 때 `컨테이너`의 `의존성`, `네트워크`, `볼륨`들을 추가적으로 정의할 수 있습니다.
### Docker Compose yaml 파일 옵션
```yml
version: '3'

services:
  app:
    image: 'openjdk:17-jdk-slim'
    container_name: spring_app
    build:
      context: .
      dockerfile: Dockerfile
    ports:
      - "8080:8080"
    environment:
      SPRING_DATASOURCE_URL: jdbc:mariadb://db:3306/springdb
      SPRING_DATASOURCE_USERNAME: root
      SPRING_DATASOURCE_PASSWORD: password
    depends_on:
      - db
    networks:
      - spring-network

  db:
    image: mariadb:latest
    container_name: spring_db
    environment:
      MYSQL_ROOT_PASSWORD: password
      MYSQL_DATABASE: springdb
    ports:
      - "3306:3306"
    volumes:
      - db_data:/var/lib/mysql
    networks:
      - spring-network

networks:
  spring-network:
    driver: bridge

volumes:
  db_data:
```
- `version` : `YAML`파일의 포맷 버전을 의미합니다.
- `services` : 생성할 컨테이너들을 묶어 놓은 단위입니다. 서비스 항목 아래에 `도커 컴포즈`로 생성할 컨테이너 옵션을 정의합니다.
- `image` : 컨테이너에서 사용될 `이미지`를 정의합니다.
- `environment` : 컨테이너 내부에서 사용될 `환경변수`를 지정하며, `딕셔너리` 또는 `배열`형태로 사용됩니다.
- `depends_on` : 해당 컨테이너의 `의존 관계`를 나타냅니다.
- `ports` : 컨테이너를 개방할 `포트`를 설정합니다.
- `build` : 해당 `build` 옵션에 설정된 `Dockerfile`을 바탕으로 이미지를 빌드하여 컨테이너를 생성합니다.
- `driver` : 생성된 컨테이너에 기본적으로 `bridge` 타입의 네트워크를 생성합니다.
### Docker Compose 명령어
- `docker-compose up` : 도커 컴포즈 프로젝트를 실행합니다.
- `docker-compose up -d` : 도커 컴포즈 프로젝트를 `백그라운드` 환경에서 실행합니다.
- `docker-compose -p 프로젝트이름 up -d` : 프로젝트 이름을 명령어에서 작성한 프로젝트 이름으로 `변경`하여 프로젝트를 실행합니다.
- `docker-compose down` : 도커 컴포즈 프로젝트 내의 `컨테이너`와 `네트워크`를 종료합니다.
- `docker-compose down -v` : 도커 컴포즈 프로젝트 내의 `컨테이너`와 `네트워크`, `볼륨`을 종료합니다.
- `docker-compose ps` : 현재 도커 컴포즈 프로젝트 `목록`을 확인합니다.
## 참고 자료
- https://velog.io/@sorzzzzy/Docker-9.-%EB%8F%84%EC%BB%A4-%EC%BB%B4%ED%8F%AC%EC%A6%88%EB%9E%80
- https://seosh817.tistory.com/387