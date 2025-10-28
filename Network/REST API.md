# REST API

# 1. REST API 중심 규칙

- REST에서 가장 중요한 기본적인 규칙은 URI는 자원을 표현하는 데에 집중하고 행위에 대한 정의 HTPP Method를 통해 하는 것이 REST한 API를 설계하는 중심 규칙임.

1. URI는 정보의 자원을 표현해야함.
   - 리소스명은 동사보다 명사를 사용.
   - URI는 자원을 표현하는데 중점을 두어야 함. get 같은 행위에 대한 표현이 들어가서는 안됨.
2. 자원에 대한 행위는 HTTP Method(GET, POST, PUT, DELETE 등)으로 표현함.

# 2. HTTP Method

- 주로 5가지의 Method(GET, POST, PUT, PATCH, DELETE)를 사용하여 CRUD를 구현함.

| Method | Action         | 역할                    | 페이로드 |
| ------ | -------------- | ----------------------- | -------- |
| GET    | index/retrieve | 모든/특정 리소스를 조회 | x        |
| POST   | create         | 리소스를 생성           | ○        |
| PUT    | replace        | 리소스의 전체를 교체    | ○        |
| PATCH  | modify         | 리소스의 일부를 수정    | ○        |
| DELETE | delete         | 모든/특정 리소스를 삭제 | x        |

# 3. REST API의 구성

- REST API는 자원, 행위, 표현의 3가지 요소로 구성됨.
- REST는 자체 표현구조로 구성되어 REST API만으로 요청을 이해할  없음.

| 구성 요소       | 내용                    | 표현 방법             |
| --------------- | ----------------------- | --------------------- |
| Resource        | 자원                    | HTTP URI              |
| Verb            | 자원에 대한 행위        | HTTP Method           |
| Representations | 자원에 대한 행위의 내용 | HTTP Message Pay Load |

# 4. RSET API Example

- GET
- POST
- PUT
- PATCH
- DELETE
