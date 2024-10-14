# HTML5

## 1. HTML 5

- HTML은 웹페이지를 기술하기 위한 마크업 언어이다. 웹페이지의 내용과 구조를 담당하는 언어로써 HTML 태그를 통해 정보를 구조화하는 것이다.

## 2. HELLO HTML5

- HTML5 문서는 반드시 <!DOCTYPE html>으로 시작하여 문서 형식(document type)을 HTML5로 지정한다.
- 실제적인 HTML document는 <html>과 </html> 사이에 기술한다.
- <head>와 </head> 사이에는 document title, 외부 파일의 참조, 메타데이터의 설정 등이 위치하며 이 정보들은 브라우저에 표시되지 않는다.
- 웹브라우저에 출력되는 모든 요소는 <body>와 </body> 사이에 위치한다.

```html
<!DOCTYPE html>
<html>
    <head>
        <meta charset="utf-8">
        <title>Hello World</title>
    </head>
    <body>
        <h1>Hello World</h1>
        <p>안녕하세요! HTML5</p>
    </body>
</html>
```

- result

# Hello World

안녕하세요! HTML5

## 3. HTML5의 기본 문법

### 3.1 요소 (Element)

- HTML 요소는 시작 태그(start tag)와 종료 태그 (end tag) 그리고 태그 사이에 위치한 content로 구성된다.

  ![tag.png](https://prod-files-secure.s3.us-west-2.amazonaws.com/510cd684-c9a0-45bd-b45d-b35ad6027628/6bbbafa3-a075-4b8d-b9d2-f9a98dcf97ca/tag.png)

- HTML document는 요소(Element)들의 집합으로 이루어진다.

### 3.1.1 요소의 중첩(Nested Element)

- 요소는 중첩이 되며 다른 요소를 포함할 수 있다. 이때 부자관계가 성립된다. 이러한 부자관계로 정보를 구조화하는 것이다.

```html
<!DOCTYPE html>
<html>
    <head>
        <meta charset="utf-8">
        <title>Hello World</title>
    </head>
    <body>
        <h1>안녕하세요</h1>
        <p>반갑습니다!</p>
    </body>
</html>
```

- result

# 안녕하세요

반갑습니다!

- html 요소는 웹페이지를 구성하는 모든 요소들을 포함한다. 위 예제를 보연 html 요소는 body 요소를 포함하며 body 요소는 h1, p 요소를 포함한다.
- 이런 중첩 관계(부자 관계)를 시각적으로 파악하기 쉽게 indent(들여쓰기)를 활용한다.

## 3.1.2 빈 요소(Empty Element)

- content를 가질 수 없는 요소를 빈 요소라고 한다. 아래의 예와 같이 빈 요소는 content가 없으며 어트리뷰트(Attribute)만을 가질 수 있다.

```html
<meta cahrset="utf-8">
```

- 빈 요소 중 대표적인 요소
  - br
  - hr
  - img
  - input
  - link
  - meta

## 3.2 어트리뷰트 (Attribute)

- 어트리뷰트(Attribute 속성)이란 요소의 성질, 특징을 정희하는 명세이다.

- 요소는 어트리뷰트를 가질 수 있고 어트리뷰트는 요소에 추가적인 정보(이미지 파일의 경로, 크기 등)를 제공한다.

  ![html-attribute.png](https://prod-files-secure.s3.us-west-2.amazonaws.com/510cd684-c9a0-45bd-b45d-b35ad6027628/28fff51f-d7bc-4b09-baf6-9520ab8b9092/html-attribute.png)

  ```html
  	<img src="html.jpg" width="104", height="142">
  ```

- 위에 예에서 어트리뷰트 src는 이미지 파일의 경로와 파일명, width는 파일의 너비, height는 이미지의 높이 정보를 브라우저에 알려주고, 이러한 정보들을 사용하여 브라우저는 img 요소를 화면에 출력한다.

## 3.2.1 글로버 어트리뷰트(HTML Global Attribute)

- 글로버 어트리뷰트는 모든 HTML 요소가 공통으로 사용할 수 있는 어트리뷰트이다.

| Attribute | Description                                                  |
| --------- | ------------------------------------------------------------ |
| id        | 유일한 식별자(id)를 요소에 지정한다. 중복 지정이 불가하다.   |
| class     | 스타일시트에 정의된 class를 요소에 지정한다. 중복 지정이 가능하다. |
| hidden    | css의 hidden과는 다르게 의미상으로도 브라우저에 노출되지 않게 된다. |
| lang      | 지정된 요소의 언어를 지정한다. 검색엔진의 크롤링 시 웹페이지의 언어를 인식할 수 있게 한다. |
| style     | 요소에 인라인 스타일을 지정한다.                             |
| tabindex  | 사용자가 키보드로 페이지를 내비게이션 시 이동 순서를 지정한다. |
| title     | 요소에 관한 제목을 지정한다                                  |

## 3.3 주석 (Comments)

- 주석(comment)는 주로 개발자에게 코드를 설명하기 위해 사용되며 브라우저는 주석을 화면에 표시하지 않는다.

```html
<!--주석은 화면에 표시되지 않는다.-->
<p>Lorem ipsum dolor sit amet</p>
```

- result

Lorem ipsum dolor sit amet