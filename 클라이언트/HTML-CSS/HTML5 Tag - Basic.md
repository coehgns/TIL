# HTML5 Tag - Basic

## 웹페이지의 구성하는 기본 태그

## 1. 문서 형식 정의 tag

- 문서 형식 정의 태그는 출력할 웹 페이지의 형식을 브라우저에게 전달한다. 문서의 최상위에 위치해야 함. 대소문자 구별 X

```html
HTML 5 
<!DOCTYPE html>
```

## 2. html tag

- html 태그는 모든 HTML 요소의 부모 요소이며 웹 페이지에 단 하나만 존재한다. 즉, 모든 요소는 html 요소의 자식 요소이며 html 요소 내부에 기술해야 한다. <!DOCTYPE>는 예외.

```html
<!DOCTYPE html>
<html>
    <head>
        <meta charset="utf-8">
        <title>문서 제목</title>
    </head>
    <body>
        화면에 표시할 모든 콘텐츠는 이곳에 기술한다.
    </body>
</html>
```

- html은 글로버 어트리뷰트를 지원함. 특히 lang 어트리뷰트를 사용하는 경우가 많다.

```html
<html lang="ko">
```

## 3. head tag

- head 요소는 메타데이터를 포함하기 위한 요소이며 웹페이지에 단 하나만 존재함.
- 메타데이터는 HTML 문서의 title, style, link, script에 대한 데이터로 화면에 표시되지 않음.
- head 요소에는 메타데이터 이외의 화면에 표시되는 일체의 요소를 포함 시킬 수 없음.

## 3.1 title tag

- title 요소는 문서의 제목을 정의함. 정의된 제목은 브라우저 탭에 표시됨.

```html
<!DOCTYPE html>
<html>
    <head>
        <meta charset="utf-8">
        <title>문서 제목</title>
    </head>
    <body>
        Lorem ipsum doldr sit amet, consectetur adipisincing elit, 
        sed do eiusmod tempor incididunt ut labore et dolore magna aliqua.
    </body>
</html>
```

## 3.2 style tag

- style 요소에는 HTML 문서를 위한 style 정보를 정의함.

```html
<!DOCTYPE html>
<html>
    <head>
        <meta charset="utf-8">
        <title>문서 제목</title>
        <style>
            body {
                background-color: yellow;
                color: blue;
            }
        </style>
    </head>
    <body>
        Lorem ipsum doldr sit amet, consectetur adipisincing elit, sed do eiusmod tempor incididunt ut labore et dolore mag
        na aliqua.
    </body>
</html>
```

- result

  ![화면 캡처 2023-11-29 190533.png](https://prod-files-secure.s3.us-west-2.amazonaws.com/510cd684-c9a0-45bd-b45d-b35ad6027628/8e0c97d2-6e93-45ff-84fe-273e5e6d3e1c/%ED%99%94%EB%A9%B4_%EC%BA%A1%EC%B2%98_2023-11-29_190533.png)

## 3.3 link tag

- link 요소에는 외부 리소스와의 연계 정보를 정의함.
- 주로 HTML과 외부 CSS 파일을 연계에 사용됨.

```html
<!DOCTYPE html>
<html>
    <head>
        <meta charset="utf-8">
        <title>문서 제목</title>
        <link rel="stylesheet" href="style.css">
    </head>
    <body>
        Lorem ipsum doldr sit amet, consectetur adipisincing elit, sed do eiusmod tempor incididunt ut labore et dolore mag
        na aliqua.
    </body>
</html>
```

## 3.4 script tag

- script 요소에는 client-side JavaScript를 정의함.

```html
<!DOCTYPE html>
<html>
    <head>
        <meta charset="utf-8">
        <script>
            document.addEventListener('click',function() {
                alert('Clicked!');
            });
        </script>
    </head>
    <body>
        Lorem ipsum doldr sit amet, consectetur adipisincing elit, sed do eiusmod tempor incididunt ut labore et dolore mag
        na aliqua.
    </body>
</html>
```

- result
  - Lorem ipsum doldr sit amet, consectetur adipisincing elit, sed do eiusmod tempor incididunt ut labore et dolore magna aliqua.
- src 어트리뷰트를 사용하면 외부 JavaScript 파일을 로드할 수 있다.

```html
<!DOCTYPE html>
<html>
    <head>
        <meta charset="utf-8">
        <script src="main.js"></script>
    </head>
    <body>
        Lorem ipsum doldr sit amet, consectetur adipisincing elit, sed do eiusmod tempor incididunt ut labore et dolore mag
        na aliqua.
    </body>
</html>
```

## 3.5 meta tag

- meta 요소는 description, keywords, author, 기타 메타데이터 정의에 사용됨.
- 메타디에터는 브라우저, 검색엔진(keywords) 등에 의해 사용됨.
- charset 어트리뷰트는 브라우저가 사용할 문자셋을 정의함.

```html
<!DOCTYPE html>
<html>
    <head>
        <meta charset="utf-8">
        <script src="main.js"></script>
    </head>
    <body>
        <p>안녕하세요</p>
        <p>Hello</p>
        <p>こんにちは</p>
        <p>你好</p>
        <p>שלום</p>
        <p>สวัสดี</p>
    </body>
</html>
```

- result
  - 안녕하세요
  - Hello
  - こんにちは
  - 你好
  - שלום
  - สวัสดี

```html
SEO(검색엔진 최적화)를 위해 검색엔진이 사용할 keywords을 정의.
<meta name="keywords" content="HTML, CSS, XML, XHTML, JavaScript">
웹페이지의 설명을 정의.
<meta name="description" content="Web tutorials on HTML and CSS">
웹페이지의 저자를 명기.
<meta name="author" content="John Doe">
웹페이지를 30초 마다 Refresh.
<meta http-equiv="refresh" content="30">
```

## 4. body tag

- body tag는 HTML 문서의 내용을 나타내며 웹페이지에 단 하나만 존재함.
- 메타데이터를 제외한 웹페이지를 구성하는 대부분의 요소가 body 요소 내에 기술됨.