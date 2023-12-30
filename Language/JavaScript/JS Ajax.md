# JS Ajax

# 1. Ajax (***\*Asynchronous JavaScript and XML)\****

- 브라우저에서 웹페이지를 요청하거나 링크를 클릭하면 화면 갱신이 발생함.(브라우저와 서버와의 통신에 의한 것.)
- 서버는 요청받은 페이지를 반환하는데 이때 HTML에서 로드하는 CSS나 JavaScript 파일들도 같이 반환됨.
- 클라이언트의 요청에 따라 서버는 정적인 파일을 반환할 수도 있고 서버 사이드 프로그램이 만들어낸 파일이나 데이터를 반환할 수도 있음.

------

- Ajax는 비동기적으로 서버와 브라우저가 데이터를 교호나할 수 있는 통신 방식을 의미함.
- 페이지 전체를 로드하여 렌더링할 필요가 없고 갱신이 필요한 일부만 로드하여 갱신하면 됨.

------

# 2. JSOM (***\*JavaScript Object Notation)\****

- JSON은 클라이언트와 서버 간 데이터 교환을 위한 규칙 즉 데이터 포맷을 말함.
- JSON은 일반 텍스트 포맷보다 효과적인 데이터 구조화가 가능함.
- JSON은 순수한 텍스트로 구성된 규칙이 있는 데이터 구조임.

```json
{
  "name": "Lee",
  "gender": "male",
  "age": 20,
  "alive": true
}
```

- 키는 반드시 큰따옴표(작은따옴표 사용불가)로 둘러싸야 함.

## 2.1 JSON.stringify

- JSON.stringify 메소드는 객체를 JSON 형식의 문자열로 변환함.

## 2.2 JSON.parse

- JSON.parse 메소드는 JSON 데이터를 가진 문자열을 객체로 변환함.
- 서버로부터 브라우저로 전송된 JSON 데이터는 문자열임. 이 문자열을 객체로서 사용하려면 객체화하여야하는데 이를 역직렬화라고 함.

------

# 3. XMLHttpRequest

- 브라우저는 XMLHttpRequest 객체를 이용하여 Ajax 요청을 생성하고 전송함.
- 서버가 브라우저의 요청에 대해 응답을 반환하면 같은 XMLHttpRequest 객체가 그 결과를 처리함.

## 3.1 Ajax request

- Ajax 요청 처리의 예

```jsx
// XMLHttpRequest 객체의 생성
const xhr = new XMLHttpRequest();
// 비동기 방식으로 Request를 오픈한다
xhr.open('GET', '/users');
// Request를 전송한다
xhr.send()
```

### ***\*3.1.1 XMLHttpRequest.open\****

- XMLHttpRequest 객체의 인스턴스를 생성하고 [XMLHttpRequest.open](http://XMLHttpRequest.open) 메소드를 사용하여 서버로의 요청을 준비함.
- [XMLHttpRequest.open](http://XMLHttpRequest.open) 사용법

```jsx
XMLHttpRequest.open(method, url[, async])
```

| 매개변수 | 설명                                                         |
| -------- | ------------------------------------------------------------ |
| method   | HTTP method (“GET”, “POST”, “PUT”, “DELETE” 등)              |
| url      | 요청을 보낼 URL                                              |
| async    | 비동기 조작 여부. 옵션으로 default는 true이며 비동기 방식으로 동작한다. |

### ***\*3.1.2 XMLHttpRequest.send\****

- XMLHttpRequest.send 메소드로 준비된 요청을 서버에 전달함.
- 서버로 전송하는 데이터를 GET, POST 메소드에 따라 그 전송 방식에 차이가 있음.
  - GET 메소드의 경우 URL의 일부분인 쿼리문자열로 데이터를 서버로 전송함.
  - POST 메소드의 경우 데이터를 Rrequest Body에 담아 전송함.
- XMLHttpRequest.send 메소드에는 request body에 담아 전송할 인수를 전달할 수 있음.
- 만약 요청 메소드가 GET인 경우, send 메소드의 인수는 무시되고 request body은 null로 설정됨.

### ***\*3.1.3 XMLHttpRequest.setRequestHeader\****

- XMLHttpRequest.setRequestHeader 메소드는 HTTP Request Header의 값을 설정함.
- setRequestHeader 메소드는 반드시 XMLHttpRequest.open 메소드 호출 이후에 호출함.

------

- Content-type
- Content-type은 request body에 담아 전송할 데이터의 MIME-type의 정보를 표현함.

| 타입                        | 서브타입                                           |
| --------------------------- | -------------------------------------------------- |
| text 타입                   | text/plain, text/html, text/css, text/javascript   |
| Application 타입            | application/json, application/x-www-form-urlencode |
| File을 업로드하기 위한 타입 | multipart/formed-data                              |

- Accept
  - HTTP 클라이언트가 서버에 요철할 때 서버가 센드백할 데이터의 MIME-type을 Accept로 지정할 수 있음.
- 서버가 센드백할 데이터의 MIME-type을 지정하는 예

```jsx
// 서버가 센드백할 데이터의 MIME-type 지정: json
xhr.setRequestHeader('Accept', 'application/json');
```

- 만약 Accept 헤더를 설정하지 않으면 send 메소드가 호출될 때 Accept 헤더가 */* 으로 전송됨.

## 3.2 Ajax response

- XMLHttpRequest.send 메소드를 통해 서버에 Request를 전송하면 서버는 Response를 반환함.
- readXMLHttpRequest.readyState의 값

| Value | State            | Description                                           |
| ----- | ---------------- | ----------------------------------------------------- |
| 0     | UNSENT           | XMLHttpRequest.open() 메소드 호출 이전                |
| 1     | OPENED           | XMLHttpRequest.open() 메소드 호출 완료                |
| 2     | HEADERS_RECEIVED | XMLHttpRequest.send() 메소드 호출 완료                |
| 3     | LOADING          | 서버 응답 중(XMLHttpRequest.responseText 미완성 상태) |
| 4     | DONE             | 서버 응답 완료                                        |

# 4. Web Server

- 웹서버는 브라우저와 같은 클라이언트로부터 HTTP 요청을 받아들이고 HTML 문서와 같은 웹 페이지를 반환하는 컴퓨터 프로그램임.
- Ajax는 웹서버와의 통신이 필요하므로 예제를 실행하기 위해서는 웹서버가 필요함.

# 5. Ajax 예제

## 5.1 Load HTML

- Ajax를 이용하여 웹페이지에 추가하기 가장 손쉬운 데이터 형식은 HTML임.(전송받은 데이터를 DOM에 추가하면 됨.)

## 5.2 Load JSON

- 서버로부터 브라우저로 전송된 JSON 데이터는 문자열임.
- 역직렬화를 위해서 내장 객체 JSON의 static 메소드인 JSON.parse()를 사용함.

## 5.3 Load JSONP

- 요청에 의해 웹페이지가 전달된 서버와 동일한 도메인의 서버로 부터 전달된 데이터는 문제없이 처리할 수 있음. 하지만 보안상의 이유로 다른 도메인으로의 요청은 제한됨.(이것을 동일출처원칙이라고 함.)

------

- 동일출처원칙 우회 방법
  1. 웹서버의 프록시 파일
     - 서버에 원격 서버로부터 데이터를 수집하는 별도의 기능을 추가하는 것.(프록시라고 함.)
  2. JSONP
     - script 태그의 원본 주소에 대한 제약은 존재하지 않는데 이것을 이용하여 다른 도메인의 서버에서 데이터를 수집하는 방법임.
     - 자신의 서버에 함수를 정의하고 다른 도메인의 서버에 얻고자 하는 데이터를 인수로 하는 함수 호출문을 로드하는 것임.
  3. Cross-Origin Resource Sharing
     - HTTP 헤더에 추가적으로 정보를 추가하여 브라우저와 서버가 통신해야 한다는 사실을 알게하는 방법.(최신 브라우저에서만 동작하며 서버에 HTPP 헤더를 설정해 주어야 함.)