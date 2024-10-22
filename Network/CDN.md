# CDN(Content Delivery Network)
- 지리적인 제약 없이 전세계 사용자들에게 컨텐츠를 **빠르고 안전하게** 보낼 수 있는 네트워크 기술입니다. 이로 인해 컨텐츠의 병목 현상을 피할 수 있습니다.
## CDN의 원리
대한민국 반대편의 있는 나라는 대한민국의 컨텐츠를 이용하려면 오랜 시간이 걸릴 것 입니다. 이러한 불편한 문제로 `CDN`이 고안되었습니다.  `CDN`은 서버를 분산 시켜 `캐싱` 해두고, 사용자가 어떠한 `컨텐츠`를 요청하면 사용자에게서 가장 가까운 서버에 연결하여 요청에 해당하는 `캐싱된 컨텐츠`를 사용자에게 제공해주는 원리입니다.
![image](https://github.com/user-attachments/assets/d58f1977-577a-4b51-aef1-225bce31fd9a)
## CDN 캐싱 방식
### Static Caching
- `Origin Server`에 있는 컨텐츠를 운영자가 미리 복사하여 `Cache Server`에 저장해두었다가, 사용자가 해당 컨텐츠를 요청하게 되면 사용자가 요청한 컨텐츠는 무조건적으로 `Cache Server`에 있어 사용자에게 응답해주는 방식입니다.
### Dynamic Caching
- `Origin Server`에 있는 컨텐츠를 미리 복사해두지 않는 방식입니다.
- 사용자의 요청이 들어오면 해당 컨텐츠 유무를 확인한 뒤, 없다면 `Origin Server`에서 다운로드 받아 컨텐츠를 응답하는 방식입니다.
## CDN의 장점
#### 빠른 전송 속도
- `CDN`은 전 세계에 서버를 분산 시켜 동작하므로 사용자가 요청한 컨텐츠를 빠르게 응답할 수 있습니다.
#### 비용 절감
- `CDN`은 `Origin Server`가 제공해야 하는 컨텐츠들을 줄여주므로 비용을 절감할 수 있습니다.
#### 웹 사이트 보안 강화
- `CDN`은 최신의 검증받은 인증 방식들을 사용하고 있습니다.
- 이 때, 비정상적인 요청이 들어오게 되면 `Origin Server`에 전달되기 전에 `edge`에서 먼저 거쳐지기 때문에 여러 `edge`로 트래픽을 분산 시켜 공격을 방어할 수 있습니다.
#### 서버 부하 막음
- `CDN`은 여러 곳으로 분산 시킨 서버인 `edge`가 사용됩니다. 이렇게 분산된 `edge`에 `Origin Server`로 몰린 트래픽을  분산 시키기 때문에 서버의 부하를 막을 수 있습니다.
![image](https://github.com/user-attachments/assets/266678d2-a5fa-487b-ba1b-ca2508ce3e90)
## 참고 자료
- https://velog.io/@youngblue/CDN%EC%9D%B4%EB%9E%80-%EB%AC%B4%EC%97%87%EC%9D%B8%EA%B0%80
- https://aws.amazon.com/ko/what-is/cdn/
- https://www.cdnetworks.com/ko/blog/web-performance/cdn-benefits/
- https://sunrise0.tistory.com/5
- https://www.akamai.com/ko/glossary/what-is-a-cdn