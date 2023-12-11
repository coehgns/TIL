# JS Hello world

## 1.개발자 도구

| 패널        | 설명                                                         |
| ----------- | ------------------------------------------------------------ |
| Elements    | 로딩된 웹 페이지의 DOM과 CSS를 편집하여 렌더링된 뷰를 확인해 볼 수 있다. 단, 편집한 내용이 저장되지는 않는다. 웹 페이지가 의도된 대로 렌더링되지 않았다면 이 패널을 확인하여 유용한 힌트를 얻을 수 있다. |
| Console     | 로딩된 웹 페이지의 에러를 확인하거나 자바스크립트 소스코드에 포함시킨 console.log 메소드의 결과를 확인해 볼 수 있다. |
| Sources     | 로딩된 웹 페이지의 자바스크립트 코드를 디버깅할 수 있다.     |
| Network     | 로딩된 웹 페이지에 관련한 네트워크 요청(request) 정보와 퍼포먼스를 확인할 수 있다. |
| Application | 웹 스토리지, 세션, 쿠키를 확인하고 관리할 수 있다.           |

## 2. 콘솔

- 개발자 도구의 Console(콘솔) 패널은 자바스크립트 코드에서 에러가 발생하여 애플리케이션이 정상적으로 동작하지 않을 때 가장 우선적으로 살펴보아야 할 곳임.
- 구현 단계에서 디버깅을 실행하는 것보다 간편하게 값을 확인하며 개발을 진행하기 위해 console.log 함수를 사용하는 경우가 많음.
- 콘솔은 자바스크립트 코드를 직접 입력하여 그 결과를 확인할 수 있는 REPL 환경으로 사용할 수도 있음.

```html
<!DOCTYPE html>
<html>
<head>
  <meta charset="UTF-8">
  <title>Counter</title>
</head>
<body>
  <div id="counter">0</div>
  <button id="increase">+</button>
  <button id="decrease">-</button>
  <script>
    // 에러를 발생시키는 코드
    const $counter = document.getElementById('counter-x');
    const $increase = document.getElementById('increase');
    const $decrease = document.getElementById('decrease');

    let num = 0;
    const render = function () { $counter.innerHTML = num; };

    $increase.onclick = function () {
      num++;
      console.log('increase 버튼 클릭', num);
      render();
    };

    $decrease.onclick = function () {
      num--;
      console.log('decrease 버튼 클릭', num);
      render();
    };
  </script>
</body>
</html>
```

- +또는 -버튼을 클릭하면 에러가 발생함.

  ![DevTools-console-4.png](https://prod-files-secure.s3.us-west-2.amazonaws.com/510cd684-c9a0-45bd-b45d-b35ad6027628/ce41b0d7-4291-4c93-8546-3e312b1a2863/DevTools-console-4.png)

### 디버깅

![DevTools-console-5.png](https://prod-files-secure.s3.us-west-2.amazonaws.com/510cd684-c9a0-45bd-b45d-b35ad6027628/f8f0192e-777a-491d-bc05-6045087201e9/DevTools-console-5.png)

- 에러가 발생한 위치에 빨간 밑줄이 표시되고 그 위에 마우스를 올려 보면 Uncauht TypeError: Cannot set property ‘innerHTML’ of null이라는 에러 정보가 표시되는데 이 에러는 innerHTML 프로퍼티에 값을 할당하기 위해 객체 $conter를 참조했으나 그 객체가 null이기 때문에 발생한 에러임.

- 에러가 발생한 코드 왼쪽의 라인 번호를 클릭하여 브레이크 포인트를 걸고 다시 버튼을 클릭하면 디버깅 모드로 들어가게 됨.

  ![DevTools-console-6.png](https://prod-files-secure.s3.us-west-2.amazonaws.com/510cd684-c9a0-45bd-b45d-b35ad6027628/ad77ad1f-37f3-4947-a71e-e941869ebbe2/DevTools-console-6.png)

- $conter의 값이 null인 것을 확인. 그 원인은 13 라인에서 $conter에 값을 할당할 때, HTML 요소의 아이디를 ‘counter-x’로 잘못 지정하여서 임. 소스코드로 돌아가 HTML 요소의 아이디를 ‘counter’로 정확히 지정하면 에러가 제거될 것임.

# 3. Node.js

- 웹 브라우저에서 동작하는 간단한 웹 애플리케이션은 브라우저만으로도 개발을 할 수 있음.

### 3.1 Node.js와 npm 소개

- 브라우저에서만 동작하던 자바스크립트를 브라우저 이외의 환경에서 동작시킬 수 있는 자바스크립트 실행 환경이 Node.js임.
- Node.js는 주로 서버 사이드 애플리케이션 개발에 사용되며 이에 필요한 모듈, 파일 시스템, HTTP 등 빌트인 APT를 제공함.
- Node.js는 데이터를 실시간 처리하여 빈번한 I/O가 발생하는 SPA에 적합함.
- Node.js는 백엔드 영역의 서버 애플리케이션 개발뿐만 아니라 프런트엔드 영역의 다양한 도구나 라이버러리도 Node.js 환경에서 동작함.(Node.js는 프런트엔드 모던 자바스크립트 개발에 필수적인 환경이라고 할 수 있음.)