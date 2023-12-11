- CSS는 HTML 요소의 style을 정의하는데 그리하려면 HTML이 존재하여야 하고 또한 styel을 적용하고자하는 HTML 요소를 특정할 필요가 있음.
- style을 적용하고자하는 HTML 요소를 셀렉터로 특정하고 선택된 요소에 스타일을 정의하는 것임.

![Selector.png](https://prod-files-secure.s3.us-west-2.amazonaws.com/510cd684-c9a0-45bd-b45d-b35ad6027628/7b09e1fb-98ac-4ad9-ab58-5d62d48e0681/Selector.png)

CSS Rule Set

```html
<!DOCTYPE html>
<html>
<head>
  <style>
    h1 { color: red; }
    p  { color: blue; }
  </style>
</head>
<body>
  <h1>Hello World!</h1>
  <p>This paragraph is styled with CSS.</p>
</body>
</html>
```

- result

  ![selector-2.png](https://prod-files-secure.s3.us-west-2.amazonaws.com/510cd684-c9a0-45bd-b45d-b35ad6027628/90a6faaf-4b3f-462d-b744-3209da2ad713/selector-2.png)

- 복수개의 셀렉터를 연속하여 지정할 수 있으며 쉼표(,)로 구분함.

```scss
h1, p { color: red; }
```

## 1. 전체 셀렉터 (Universal Selector)

| 패턴 | Description                                                  |
| ---- | ------------------------------------------------------------ |
| *    | HTML 문서 내의 모든 요소를 선택한다. html 요소를 포함한 모든 요소가 선택된다. (head 요소도 포함된다) |

```scss
<!DOCTYPE html>
<html>
<head>
  <style>
    /* 모든 요소를 선택 */
    * { color: red; }
  </style>
</head>
<body>
  <h1>Heading</h1>
  <div>
    <p>paragraph 1</p>
    <p>paragraph 2</p>
  </div>
  <p>paragraph 3</p>
</body>
</html>
```

- result

  ![전체 셀렉터.png](https://prod-files-secure.s3.us-west-2.amazonaws.com/510cd684-c9a0-45bd-b45d-b35ad6027628/7df470f3-63dc-44db-9c0b-a64ab4408614/%EC%A0%84%EC%B2%B4_%EC%85%80%EB%A0%89%ED%84%B0.png)

## 2. 태그 셀렉터 (Type Selector)

| 패턴   | Description                            |
| ------ | -------------------------------------- |
| 태그명 | 지정된 태그명을 가지는 요소를 선택한다 |

- 지정된 태그명을 가지는 요소를 선택함.

```scss
<!DOCTYPE html>
<html>
<head>
  <style>
    /* 모든 p 태그 요소를 선택 */
    p { color: red; }
  </style>
</head>
<body>
  <h1>Heading</h1>
  <div>
    <p>paragraph 1</p>
    <p>paragraph 2</p>
  </div>
  <p>paragraph 3</p>
</body>
</html>
```

- result

  ![tag selector.png](https://prod-files-secure.s3.us-west-2.amazonaws.com/510cd684-c9a0-45bd-b45d-b35ad6027628/60785332-b813-4e70-ba40-44b08b791396/tag_selector.png)

## 3. ID 셀렉터 (ID Selector)

| 패턴              | Description                                                  |
| ----------------- | ------------------------------------------------------------ |
| #id 어트리뷰트 값 | id 어트리뷰트 값을 지정하여 일치하는 요소를 선택한다. id 어트리뷰트 값은 중복될 수 없는 유일한 값이다. |

```scss
<!DOCTYPE html>
<html>
<head>
  <style>
    /* id 어트리뷰트 값이 p1인 요소를 선택 */
    #p1 { color: red; }
  </style>
</head>
<body>
  <h1>Heading</h1>
  <div class="container">
    <p id="p1">paragraph 1</p>
    <p id="p2">paragraph 2</p>
  </div>
  <p>paragraph 3</p>
</body>
</html>
```

- result

  ![ID selector.png](https://prod-files-secure.s3.us-west-2.amazonaws.com/510cd684-c9a0-45bd-b45d-b35ad6027628/94f0ae5e-ed57-437f-a69e-c5cd9ef2d961/ID_selector.png)

## 4. 클래스 셀렉터 (Class Selector)

| 패턴                 | Description                                                  |
| -------------------- | ------------------------------------------------------------ |
| .class 어트리뷰트 값 | class 어트리뷰트 값을 지정하여 일치하는 요소를 선택한다. class 어트리뷰트 값은 중복될 수 있다. |

```html
<!DOCTYPE html>
<html>
<head>
  <style>
    /* class 어트리뷰트 값이 container인 모든 요소를 선택 */
    /* color 어트리뷰트는 자식 요소에 상속된다. */
    .container { color: red; }
    /* not supported in IE */
    #p2 { color: initial; }
  </style>
</head>
<body>
  <h1>Heading</h1>
  <div class="container">
    <p id="p1">paragraph 1</p>
    <p id="p2">paragraph 2</p>
  </div>
  <p>paragraph 3</p>
</body>
</html>
```

- result

  ![class selector.png](https://prod-files-secure.s3.us-west-2.amazonaws.com/510cd684-c9a0-45bd-b45d-b35ad6027628/288fbf3d-1468-4465-929f-fad97c294de7/class_selector.png)

- HTML 요소에 class 어트리뷰트 값은 공백으로 구분하여 여러 개 지정할 수 있음.

- 아래와 같이 클래스 셀렉터를 사용하여 미리 스타일을 정의해 두고, HTML 요소는 이미 정의되어 이는 클래스를 지정하는 것으로 필요한 스타일을 지정할 수 있음.

```html
<!DOCTYPE html>
<html>
<head>
  <style>
    /* class 어트리뷰트 값이 text-center인 모든 요소를 선택 */
    .text-center { text-align: center; }
    /* class 어트리뷰트 값이 text-large인 모든 요소를 선택 */
    .text-large  { font-size: 200%; }
    /* class 어트리뷰트 값이 text-red인 모든 요소를 선택 */
    .text-red    { color: red; }
    /* class 어트리뷰트 값이 text-blue인 모든 요소를 선택 */
    .text-blue   { color: blue; }
  </style>
</head>
<body>
  <p class="text-center">Center</p>
  <p class="text-large text-red">Large Red</p>
  <p class="text-center text-large text-blue">Center Large Blue</p>
</body>
</html>
```

- result

  ![class selector-2.png](https://prod-files-secure.s3.us-west-2.amazonaws.com/510cd684-c9a0-45bd-b45d-b35ad6027628/65edf732-7c9e-409d-b998-a6b3362d8d0c/class_selector-2.png)

## 5. 어트리뷰트 셀렉터(Attribute Selector)

| 패턴               | Description                                    |
| ------------------ | ---------------------------------------------- |
| 셀렉터[어트리뷰트] | 지정된 어트리뷰트를 갖는 모든 요소를 선택한다. |

```html
<!DOCTYPE html>
<html>
<head>
  <style>
    /* a 요소 중에 href 어트리뷰트를 갖는 모든 요소 */
    a[href] { color: red; }
  </style>
</head>
<body>
  <a href="<http://www.poiemaweb.com>">poiemaweb.com</a><br>
  <a href="<http://www.google.com>" target="_blank">google.com</a><br>
  <a href="<http://www.naver.com>" target="_top">naver.com</a>
</body>
</html>
```

- result

  ![어트리뷰트 셀렉터.png](https://prod-files-secure.s3.us-west-2.amazonaws.com/510cd684-c9a0-45bd-b45d-b35ad6027628/0d2fa299-5760-4818-a6b7-035a0cad0bc4/%EC%96%B4%ED%8A%B8%EB%A6%AC%EB%B7%B0%ED%8A%B8_%EC%85%80%EB%A0%89%ED%84%B0.png)

| 패턴                    | Description                                                  |
| ----------------------- | ------------------------------------------------------------ |
| 셀렉터[어트리뷰트=”값”] | 지정된 어트리뷰트를 가지며 지정된 값과 어트리뷰트의 값이 일치하는 모든 요소를 선택한다. |

```html
<!DOCTYPE html>
<html>
<head>
  <style>
    /* a 요소 중에 target 어트리뷰트의 값이 "_blank"인 모든 요소 */
    a[target="_blank"] { color: red; }
  </style>
</head>
<body>
  <a href="<http://www.poiemaweb.com>">poiemaweb.com</a><br>
  <a href="<http://www.google.com>" target="_blank">google.com</a><br>
  <a href="<http://www.naver.com>" target="_top">naver.com</a>
</body>
</html>
```

- result

  ![셀렉터 어트리뷰트=값.png](https://prod-files-secure.s3.us-west-2.amazonaws.com/510cd684-c9a0-45bd-b45d-b35ad6027628/f8a19285-2ec6-4225-90dc-11179b651b51/%EC%85%80%EB%A0%89%ED%84%B0_%EC%96%B4%ED%8A%B8%EB%A6%AC%EB%B7%B0%ED%8A%B8%EA%B0%92.png)

| 패턴                     | Description                                                  |
| ------------------------ | ------------------------------------------------------------ |
| 셀렉터[어트리뷰트~=”값”] | 지정된 어트리뷰트의 값이 지정된 값을 (공백으로 분리된) 단어로 포함하는 요소를 선택한다. |

```html
<!DOCTYPE html>
<html>
<head>
  <style>
    /* h1 요소 중에 title 어트리뷰트 값에 "first"를 단어로 포함하는 요소 */
    h1[title~="first"] { color: red; }
  </style>
</head>
<body>
  <h1 title="heading first">Heading first</h1>
  <h1 title="heading-first">Heading-first</h1>
  <h1 title="heading second">Heading second</h1>
  <h1 title="heading third">Heading third</h1>
</body>
</html>
```

- result

  ![셀렉터 어트리뷰트 공백 값.png](https://prod-files-secure.s3.us-west-2.amazonaws.com/510cd684-c9a0-45bd-b45d-b35ad6027628/0025d17e-4005-4e84-9f89-138c993c22fc/%EC%85%80%EB%A0%89%ED%84%B0_%EC%96%B4%ED%8A%B8%EB%A6%AC%EB%B7%B0%ED%8A%B8_%EA%B3%B5%EB%B0%B1_%EA%B0%92.png)

| 패턴              | Description |
| ----------------- | ----------- |
| 셀렉터[어트리뷰트 | =”값”]      |

```html
<!DOCTYPE html>
<html>
<head>
  <style>
    /* p 요소 중에 lang 어트리뷰트 값이 "en"과 일치하거나 "en-"로 시작하는 요소 */
    p[lang|="en"] { color: red; }
  </style>
</head>
<body>
  <p lang="en">Hello!</p>
  <p lang="en-us">Hi!</p>
  <p lang="en-gb">Ello!</p>
  <p lang="us">Hi!</p>
  <p lang="no">Hei!</p>
</body>
</html>
```

- result

  ![셀렉터 어트리뷰트 하이픈.png](https://prod-files-secure.s3.us-west-2.amazonaws.com/510cd684-c9a0-45bd-b45d-b35ad6027628/7b3ddc1a-1619-42ab-816f-b61e6135281b/%EC%85%80%EB%A0%89%ED%84%B0_%EC%96%B4%ED%8A%B8%EB%A6%AC%EB%B7%B0%ED%8A%B8_%ED%95%98%EC%9D%B4%ED%94%88.png)

| 패턴                     | Description                                        |
| ------------------------ | -------------------------------------------------- |
| 셀렉터[어트리뷰트^=”값”] | 지정된 어트리뷰트 값으로 시작하는 요소를 선택한다. |

```html
<!DOCTYPE html>
<html>
<head>
  <style>
    /* a 요소 중에 href 어트리뷰트 값이 "https://"로 시작하는 요소 */
    a[href^="https://"] { color: red; }
  </style>
</head>
<body>
  <a href="<https://www.test.com>"><https://www.test.com></a><br>
  <a href="<http://www.test.com>"><http://www.test.com></a>
</body>
</html>
```

- result

  ![셀렉터 어트리뷰트 href.png](https://prod-files-secure.s3.us-west-2.amazonaws.com/510cd684-c9a0-45bd-b45d-b35ad6027628/505fc593-9e5b-4cfd-8b3e-08e9ab7df8fa/%EC%85%80%EB%A0%89%ED%84%B0_%EC%96%B4%ED%8A%B8%EB%A6%AC%EB%B7%B0%ED%8A%B8_href.png)

| 패턴                     | Description                                      |
| ------------------------ | ------------------------------------------------ |
| 셀렉터[어트리뷰트$=”값”] | 지정된 어트리뷰트 값으로 끝나는 요소를 선택한다. |

```html
<!DOCTYPE html>
<html>
<head>
  <style>
    /* a 요소 중에 href 어트리뷰트 값이 ".html"로 끝나는 요소 */
    a[href$=".html"] { color: red; }
  </style>
</head>
<body>
  <a href="test.html">test.html</a><br>
  <a href="test.jsp">test.jsp</a>
</body>
</html>
```

- result

  ![셀렉터 어트리뷰트 .html.png](https://prod-files-secure.s3.us-west-2.amazonaws.com/510cd684-c9a0-45bd-b45d-b35ad6027628/07fd10f7-a856-47fd-ac30-2fc1a057b1ae/%EC%85%80%EB%A0%89%ED%84%B0_%EC%96%B4%ED%8A%B8%EB%A6%AC%EB%B7%B0%ED%8A%B8_.html.png)

| 패턴                     | Description                                      |
| ------------------------ | ------------------------------------------------ |
| 셀렉터[어트리뷰트*=”값”] | 지정된 어트리뷰트 값을 포함하는 요소를 선택한다. |

```html
<!DOCTYPE html>
<html>
<head>
  <style>
    /* div 요소 중에서 class 어트리뷰트 값에 "test"를 포함하는 요소 */
    div[class*="test"] { color: red; }
    /* div 요소 중에서 class 어트리뷰트 값에 "test"를 단어로 포함하는 요소 */
    div[class~="test"] { background-color: yellow; }
  </style>
</head>
<body>
  <div class="first_test">The first div element.</div>
  <div class="second">The second div element.</div>
  <div class="test">The third div element.</div>
  <p class="test">This is some text in a paragraph.</p>
</body>
</html>
```

- result

  ![셀렉터 어트리뷰트 지정된 값을 포함..png](https://prod-files-secure.s3.us-west-2.amazonaws.com/510cd684-c9a0-45bd-b45d-b35ad6027628/30313a04-aabe-4429-bc21-3a1cc8cc0f8b/%EC%85%80%EB%A0%89%ED%84%B0_%EC%96%B4%ED%8A%B8%EB%A6%AC%EB%B7%B0%ED%8A%B8_%EC%A7%80%EC%A0%95%EB%90%9C_%EA%B0%92%EC%9D%84_%ED%8F%AC%ED%95%A8..png)