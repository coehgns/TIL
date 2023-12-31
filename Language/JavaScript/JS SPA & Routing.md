# JS SPA & Routing

# 1. SPA (***\*Single Page Application)\****

- 단일 페이지 애플리케이션(Single Page Application, SPA)는 모던 웹의 패러다임임.
- SPA는 단일 페이지로 구성되며 기존의 서버 사이드 렌더링과 비교할 때 배포가 간단하며 네이티브 앱과 유사한 사용자 경험을 제공할 수 있다는 장점이 있음.

------

- SPA 구조적인 단점
  - 초기 구동 속도
    - SPA는 웹 애플리케이션에 필요한 모든 정적 리소스를 최초 접근시 단 한번 다운로드하기 때문에 초기 구동 속도가 상대적으로 느림.
  - SEO(검색엔진 최적화) 이슈
    - SPA는 클라이언트 사이드 렌더링을 일반적으로 데이터 패치 요청을 통해 서버로부터 데이터를 응답받아 뷰를 동적으로 생성하는 브라우저 주소창의 URL이 변경되지 않음.

# 2. Routing

- 라우팅이란 출발지에서 목적지까지의 경로를 결정하는 기능임.
- 라우팅은 사용자가 요청한 URL 또는 이벤트를 해석하고 새로운 페이지로 전환하기 위해 필요한 데이터를 서버에 요청하고 페이지를 전환하기 위한 일련의 행위임.

------

- 브라우저가 화면을 전환하는 경우
  1. 브라우저의 주소창에 URL을 입력하면 해당 페이지로 이동함.
  2. 웹페이지의 링크(a 태그)를 클릭하면 해당 페이지로 이동함.
  3. 브라우저의 뒤로가기 또는 앞으로가기 버튼을 클릭하면 사용자 방문 기록(history)의 뒤 또는 앞으로 이동함.
     - history 관리를 위해서는 각 페이지는 브라우저의 주소창에서 구별할 수 있는 유일한 URL을 소유해야 함.

# 3. SPA와 Routing

## 3.1 전통적 링크 방식

- 전통적 링크 방식은 link tag로 동작하는 기본적인 웹페이지의 동작 방식임.

## 3.2 ajx 방식

- ajax는 자바스크립트를 이용해서 비동기적으로 서버와 브라우저가 데이터를 교환할 수 있는 통신 방식을 의미함.
- 서버로부터 웹페이지가 응답되면 화면 전체를 새롭게 렌더링해야 하는데 페이지 일부만 갱신하고도 동일한 효과를 볼 수 있도록 하는 것이 ajax임.

## 3.3 Hash 방식

- ajax의 단점을 보완한 방법은 Hash 방식임.
- Hash 방식은 URI의 fragment identifier(#service)의 고유 기능인 앵커(anchor)를 사용함.
- fragment identifier는 hash mark 또는 hash라고 부르기도 함.

## 3.4 pjax 방식

- hash 방식의 가장 큰 단점인 SEO 이슈를 보완한 방법이 pjax 방식임.
- pjax 방식은 브라우저 주소창의 url이 변경되기 때문에 요청이 서버로 전달됨.
- pjax 방식은 서버 렌더링 방식과 ajax 방식이 혼재되어 있는 방식으로 서버의 지원이 필요함.

# 4. Conclusion

| 구분             | History 관리 | SEO 대응 | 사용자 경험 | 서버 렌더링 | 구현 난이도 | IE 대응 |
| ---------------- | ------------ | -------- | ----------- | ----------- | ----------- | ------- |
| 전통적 링크 방식 | ◯            | ◯        | ✗           | ◯           | 간단        |         |
| ajax 방식        | ✗            | ✗        | ◯           | ✗           | 보통        | 7 이상  |
| hash 방식        | ◯            | ✗        | ◯           | ✗           | 보통        | 8 이상  |
| pjax 방식        | ◯            | ◯        | ◯           | △           | 복잡        | 10 이상 |