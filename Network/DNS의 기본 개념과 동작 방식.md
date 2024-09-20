# Internet - DNS의 기본 개념과 동작 방식

------

# DNS(Domain Name System) 기본 개념

- 도메인 네임 시스템은 도메인을 IP주소로 변환해주거나 IP주소를 도메인으로 변환하는 작업을 함.
- 사용자가 이해할 수 있는 문자열 형태인 도메인 네임을 사용함.
- DNS는 도메인 네임 스페이스 구조로 계층적 데이터 베이스의 실체임.
- DNS가 도메인 네임을 IP주소로 변경하기 위해서 내부적 DNS 서버가 동작함.
- DNS 서버 요청/응답의 매개체로 DNS query를 사용함.
- 매번 도메인 주소를 IP 주소로 바꾸는 작업은 과도한 리소스 낭비일 수 있어서 DNS cache를 사용해서 리소스 낭비를 방치할 수 있음.

------

# Domain Name Space

- DNS 구조는 분산 시스템과 계층적 구조로 이루어져 있음.
- 분산 시스템을 통해 레이블을 dot(.)으로 구분해서 각 기관에서 관리함.
  - 레이블은 도메인을 나누는 최소 단위인 데이터로 문자열과 레이블 길이로 이루어져 있음.
  - 레이블은 고유해야 함. 그렇지 않으면 도메인 네임을 탐색한 과정에서 충돌이 발생할 수 있음.
- 분산 시스템을 통해 나누어진 레이블은 트리 자료 구조로 이루어진 계층적 구조로 IP 주소를 매핑함.
  - 계층 구조로 이루어진 Domain Name Space는 최상위 계층으로 시작해서 하위 계층으로 순차적으로 탐색해서 IP 주소를 반환함.
- 분산 시스템과 계층적 구조를 통해 효율적으로 도메인을 관리할 수 있음.

------

# DNS 서버

## DNS 서버 기본 개념

- 모든 DNS 서버는 DNS recursor, Root Name Server, TLD Name Server, Autoritative Name Server(SLD Name Server)로 분류됨.
- DNS cache가 존재하지 않는다면 4개의 DNS 서버를 순차적으로 작동하여 요청한 도메인 주소를 IP  주소로 변환해서 Client에 전달하는 작업을 함.
- DNS 서버는 Domain Name Space의 계층적 구조에 대한 정보를 저장하고 있는 서버임.

### Root Name Server

- Root Name Server는 계층 구조 트리에서의 최상위 경로를 담당하고 있음.
- 도메인 주소 맨 뒤에는 대부분 dot이 생략되어 있고, 생략된 dot이 Root Name Server임.
- 사람이 이해할 수 있는 도메인 네임을 IP 주소로 변환하는 첫 번째 단계로 ICANN(국제인터넷주소관리기구)이 직접 관리하는 절대 존엄 서버임.
  - 패킷의 실질적인 크기 제한으로 인해 루트 서버 수를 13개 서버 주소로 제한하도록 결정됨.
  - 갯수가 13가지가 아닌 13가지 유형의 루트 이름 서버가 있으며 전 세계에 각각의 사본이 다수 있음.
- 도메인 확장자( .kr , .com) 레이블을 구분해서 TLD Name Server로 안내함.

### TLD(Top-Level Domain) Name Server

- Authoritative DNS 서버의 주소를 저장하고 안내하는 역할을 함.
- 만약 [naver.com](http://naver.com) 으로 DNS에 요청을 보내게 되며 Root Name Server를 통해 .com 도메인 확장자를 반환 받아서 .com을 관리하는 기관에 [naver.com](http://naver.com) 도메인 주소가 존재하는지 확인하여 Authoritative DNS로 안내함.
- TLD Name Server는 ICANN의 지사인 IANA(최상위 도메인을 관리하는 단체.)가 관리하며, 두 가지 서버로 구분함.
  - 일반 최상위 도메인 : 가별로 고유하지 않은 도메인.( .com , .net)
  - 국가 코드 최상위 도메인 : 국가 또는 주와 관련된 모든 도메인이 포함됨.( .kr , .us)

### Authoritative Name Server(SLD Name Server)

- 일반적으로 DNS 서버에서 가장 마지막 단계로 실제로 DNS 리소스 레코드를 보유하고 담당하는 서버임.
- 실제 도메인과 IP 주소의 관계가 기록, 저장, 변경되는 서버임.

### DNS recursor

- Client 요청을 받아 Name Server로 전달하고 반환 받은 정보(IP 주소)를 Client에게 알려주는 중계자 역할을 함.
- 이 과정에서 계층적 구조 트리에서 순차적으로 반환하는 결과를 재귀적으로 탐색함.
- 재귀적으로 탐색해서 최종 결과를 DNS cache에 저장해 동일한 도메인 주소로 요청을 보내면 재귀적으로 탐색하는 작업을 하지 않고 즉시 Client에게 IP 주소를 반환해서 불필요한 리소스가 발생하지 않게 할 수 있음.
- Resolver, Recursive DNS Server, Local Server, ISP Server라고 부르기도 함.

------

# DNS query

- DNS 클라이언트와 DNS 서버는 DNS 쿼리를 교환하며, 요청과 응답의 사용되는 매개체임.
- 쿼리를 통해 조합을 사용하면 DNS 확인을 위한 최적화된 프로세스가 되어 이동 거리를 줄일 수 있음.

## Recursive Query

- Client와 DNS recursor 통신에 사용되는 쿼리임.
- 실제 IP 주소를 반환함.
- Recursive Query는 요청과 응답하는 과정을 포함하는 실제 반호나 결과 값임.

## Iterative Query

- DNS recursor와 Name Server 통신에 사용되는 쿼리임.
- 반복적으로 쿼리를 보내서 결과물(IP 주소)를 알아내서 DNS recursor에게 IP 주소를 보냄.
- DNS recursor에 이미 IP 주소가 캐시 되어있다면 이 과정을 생략함.

------

# DNS 동작 과정

1. 브라우저(Client)에 [naver.com](http://naver.com) 입력하면 Recursive Query가 DNS Recursor로 요청을 보냄.
2. DNS recursor에서 DNS cache 유무를 확인함.
3. 만약 DNS cache가 존재하지 않는다면 DNS recursor에서 Iterative Query가 Root Name Server로 요청을 보냄.
4. Root Name Server에서 DNS Recursor로 도메인 확장자 .com 을 반환함.
5. 반환 받은 쿼리를 DNS recursor는 Iterative Query 형태로 TLS Name Server로 보내서 .com을 관리하는 기관에서 [naver.com](http://naver.com) 이 존재하는지 확인 후 쿼리르 DNS recursot로 보냄.
6. DNS recursor는 Authoraitative Name Server에 실제 도메인 주소와 동일한 주소가 있는지 확인하기 위해 Iterative Query를 보내서 IP 주소를 반환함.
7. 6번 과정에서 DNS cache를 저장해서 불필요한 리소스가 발생하는 문제를 예방함.
8. DNS recursor는 처음 요청한 도메인과 매핑된 IP 주소로 웹 브라우저에게 응답함.
9. 브라우저가 IP 주소로 HTTP 요청을 보냄.
10. IP 주소의 서버가 브라우저에서 렌더링할 웹 페이지를 반환함.

------

## 참고 자료

- https://velog.io/@park-moen/devcourse-study01