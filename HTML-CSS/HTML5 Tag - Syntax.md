- CSS는 HTML이나 XML과 같은 구조화 된 문서를 화면, 종이 등에 어떻게 렌더링할 것인지를 정의하기 위한 언어임.
- CSS는 HTML의 각 요소의 style을 정의하여 화면 등에 어떻게 렌더링하면 되는지 브라우저에게 설명하기 위한 언어임.
- HTML과 CSS는 각자의 문법을 갖는 별개의 언어이며 HTML은 CSS를 포함할 수 있음.
- HTML없이 단독으로 존재하는 CSS는 의미가 없음.

## 1. 셀렉터 (Selector, 선택자)

- CSS는 HTML 요소의 style을 정의하는데 사용됨. 이를 위해서 선행되어야하는 것은 스타일을 적용하고자 하는 HTML 요소를 선택할 수 있어야함.
- 셀렉터는 스타일을 적용하고자 하는 HTML 요소를 선택하기 위해 CSS에서 제공하는 수단.

![Selector.png](https://prod-files-secure.s3.us-west-2.amazonaws.com/510cd684-c9a0-45bd-b45d-b35ad6027628/0b0c819e-666a-4684-b904-b5a3f322e1f6/Selector.png)

- 위와 같은 구문을 Rule set(또는 Rule)이라 하며 셀렉터에 의해 선택된 특정 HTML 요소를 어떻게 렌더링할 것인지 브라우저에 지시하는 역할을 함.
- 위의 CSS Rule set은 HTML 문서에 속해 있는 셀렉터를 통해 모든 h1 요소를 선택한 후 선택된 h1 요소의 스타일을 선언 블록에서 정의하고 있음.
- 이와 같은 Rule Set의 집합을 스타일시트(Style Sheet)라고 함.

## 2. 프로퍼티 (Property/속성)

- 셀렉터로 HTML 요소를 선택하고 {} 내에 프로퍼티와 값을 지정하는 것으로 다양한 style을 정의할 수 있음.
- 프로퍼티는 표준 스펙으로 이미 지정되어 있는 것을 사용하여야하며 사용자가 임의로 정의할 수 없음.
- 여러 개의 프로퍼티를 연속해서 지정할 수 있으며 세미콜론(;)으로 구분함.

```css
p {
  color: ...;
  font-size: ...;
}
```

## 3. 값(Value/속성값)

- 셀렉터로 지정한 HTML 요소에 style을 적용하기 위해 프로퍼티를 사용함.
- 프로퍼티의 값은 해당 프로퍼티에 사용할 수 있는 값을 “키워드”나 “크기 단위” 또는 “색상 표현 단위” 등의 특정 단위로 지정하여야 함.

```css
p {
  color: orange;
  font-size: 16px;
}
```

## 4. HTML과 CSS의 연동

- HTML은 CSS를 포함할 수 있음.
- CSS를 가지고 있지 않은 HTML은 브라우저에서 기본으로 적용하는 CSS에 의해 렌더링됨.

## 4.1 Link style

- HTML에서 외부에 있는 CSS 파일을 로드하는 방식. 가장 일반적으로 사용됨.

```html
<!DOCTYPE html>
<html>
  <head>
    <link rel="stylesheet" href="css/style.css">
  </head>
  <body>
    <h1>Hello World</h1>
    <p>This is a web page.</p>
  </body>
</html>
h1 { color: red; }
p  { background: blue; }
```

## 4.2 Embedding style

- HTML 내부에 CSS를 포함시키는 방식.
- HTML과 CSS는 서로 역할이 다르므로 다른 파일로 구분되어 작성하고 관리되는 것이 바람직함.

```html
<!DOCTYPE html>
<html>
  <head>
    <style>
      h1 { color: red; }
      p  { background: aqua; }
    </style>
  </head>
  <body>
    <h1>Hello World</h1>
    <p>This is a web page.</p>
  </body>
</html>
```

- result

  ![embedding style.png](https://prod-files-secure.s3.us-west-2.amazonaws.com/510cd684-c9a0-45bd-b45d-b35ad6027628/ed4cc9ae-e1c2-4620-a72e-4b67e91e612f/embedding_style.png)

## 4.3 Inline style

- HTML 요소의 style 프로퍼티에 CSS를 기술하는 방식.
- JavaScript가 동적으로 CSS를 생성할 때 사용하는 경우가 있음.
- 일반적인 경우 Link style을 사용하는 편이 좋음.

```html
<!DOCTYPE html>
<html>
  <body>
    <h1 style="color: red">Hello World</h1>
    <p style="background: aqua">This is a web page.</p>
  </body>
</html>
```

- result

  ![embedding style.png](https://prod-files-secure.s3.us-west-2.amazonaws.com/510cd684-c9a0-45bd-b45d-b35ad6027628/dac94c39-68bf-4067-ad6f-6330ead2e0bc/embedding_style.png)

## 5. Reset CSS 사용하기

- Reset CSS는 기본적인 HTML 요소의 CSS를 초기화하는 용도로 사용함.
- 브라우저 별로 제각각인 디폴트 스타일을 하나의 스타일로 통일시켜 주는 역할을 함.
- 자주 사용되는 Reset CSS
  - [Eric Meyer’s reset](http://meyerweb.com/eric/tools/css/reset/)
  - [normalize.css](https://necolas.github.io/normalize.css/)