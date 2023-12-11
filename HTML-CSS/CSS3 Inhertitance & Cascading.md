# CSS3 Inheritance & Cascading

## 1. 상속(inheritance)

- 상속리안 상위(부모, 조상) 요소에 적용된 프로퍼티를 하위(자식, 자손) 요소가 물려 받는 것을 의미함.

- 상속 기능이 없다면 각 요소의 Rule set에 프로퍼티를 매번 각각 지정해야함.

- 프로퍼티 중에 상속이 되는 것과 되지 않는 것.

  | property              | Inherit |
  | --------------------- | ------- |
  | width/height          | no      |
  | margin                | no      |
  | padding               | no      |
  | border                | no      |
  | box-sizing            | no      |
  | display               | no      |
  | visibility            | yes     |
  | opacity               | yes     |
  | background            | no      |
  | font                  | yes     |
  | color                 | yes     |
  | line-height           | yes     |
  | text-align            | yes     |
  | vertical-align        | no      |
  | text-decoration       | no      |
  | white-space           | yes     |
  | position              | no      |
  | top/right/bottom/left | no      |
  | z-index               | no      |
  | overflow              | no      |
  | float                 | no      |

```html
<!DOCTYPE html>
<html>
<head>
  <meta charset="utf-8">
  <style>
    .text-red {
      color: red;
      border: 1px solid #bcbcbc;
      padding: 10px;
    }
  </style>
</head>
<body>
  <div class="text-red">
    <h1>Heading</h1>
    <p>Paragraph<strong>strong</strong></p>
    <button>Button</button>
  </div>
</body>
</html>
```

- result

  ![inheritance.png](https://prod-files-secure.s3.us-west-2.amazonaws.com/510cd684-c9a0-45bd-b45d-b35ad6027628/a8694f58-ddb3-4366-a16d-acad33b1bc68/inheritance.png)

- color는 상속되는 프로퍼티로서 자식 요소는 물론 자손 요소까지 적용됨. button 처럼 요소에 따라 상속 받지 않는 경우도 존재함.

- border, padding은 상속되지 않는 요소로 하위 요소에 적용되지 않음.

- 상속되지 않는 경우 inherit 키워드를 사용하여 명시적으로 상속받게 할 수 있음.

```html
<!DOCTYPE html>
<html>
<head>
  <meta charset="utf-8">
  <style>
    .text-red {
      color: red;
      border: 1px solid #bcbcbc;
      padding: 10px;
    }
    .text-red button {
      color: inherit;
    }
    .text-red p {
      border: inherit;
      padding: inherit;
    }
  </style>
</head>
<body>
  <div class="text-red">
    <h1>Heading</h1>
    <p>Paragraph<strong>strong</strong></p>
    <button>Button</button>
  </div>
</body>
</html>
```

- result

  ![inherit.png](https://prod-files-secure.s3.us-west-2.amazonaws.com/510cd684-c9a0-45bd-b45d-b35ad6027628/4dd72bd4-0d68-47f1-9312-0434dbfe1816/inherit.png)

## 2. 캐스캐이등(Cascading)

- 요소는 하나 이상의 CSS 선언에 영향을 받을 수 있는데 이 때 충돌을 피하기 위해 CSS 적용 우선순위가 필요함. 이를 캐스캐이딩이라고 함.
- 캐스캐이딩 세가지 규칙.
  - 중요도
    - CSS가 어디에 선언 되었는지에 따라서 우선순위가 달라짐.
  - 명시도
    - 대상을 명확하게 특정할 수록 명시도가 높아지고 우선순위가 높아짐.
  - 선언순서
    - 선언된 순서에 따라 우선 순위가 적용됨.(나중에 선언된 스타일이 우선 적용됨.)

### 2.1 중요도

- CSS가 어디에 선언 되었는지에 따라서 우선순위가 달라짐.

1. head 요소 내의 style 요소
2. head 요소 내의 style 요소 내의 @import 문
3. <link>로 연결된 CSS 파일
4. <link>로 연결된 CSS 파일 내의 @import 문
5. 브라우저 디폴트 스타일시트

```css
/* style.css */
body {
  background-color: red;
  color: white;
}
<!DOCTYPE html>
<html>
<head>
  <link rel="stylesheet" href="style.css">
  <style>
    body {
      background-color: beige;
      color: navy;
    }
  </style>
</head>
<body>
  Lorem ipsum dolor sit amet, consectetur adipisicing elit, sed do eiusmod tempor incididunt ut labore et dolore magna aliqua.
</body>
</html>
```

### 2.2 명시도

- 대상을 명확하게 특정할수록 명시도가 높아지고 우선순위가 높아짐.

```html
CODE
!important > 인라인 스타일 > 아이디 선택자 > 클래스/어트리뷰트/가상 선택자 > 태그 선택자
> 전체 선택자 > 상위 요소에 의해 상속된 속성
<!DOCTYPE html>
<html>
<head>
  <style>
    p        { color: red !important; }
    #thing   { color: blue; }

    div.food { color: chocolate; }
    .food    { color: green; }
    div      { color: orange; }
  </style>
</head>
<body>
  <p id="thing">Will be Red.</p>
  <div class="food">Will be Chocolate.</div>
</body>
</html>
```

- result

  ![화면 캡처 2023-12-03 184134.png](https://prod-files-secure.s3.us-west-2.amazonaws.com/510cd684-c9a0-45bd-b45d-b35ad6027628/aef7e445-fde1-4e3e-8efd-981c70f122ce/%ED%99%94%EB%A9%B4_%EC%BA%A1%EC%B2%98_2023-12-03_184134.png)

### 2.3 선언 순서

- 선언된 순서에 따라 우선 순위가 적용됨.(나중에 선언되 스타일이 우선 적용됨.)

```html
<!DOCTYPE html>
<html>
<head>
  <style>
    p { color: blue; }
    p { color: red; }

    .red { color: red; }
    .blue { color: blue; }
  </style>
</head>
<body>
  <p>Will be RED.</p>
  <p class="blue red">Will be BLUE.</p>
</body>
</html>
```

- result

![화면 캡처 2023-12-03 184222.png](https://prod-files-secure.s3.us-west-2.amazonaws.com/510cd684-c9a0-45bd-b45d-b35ad6027628/f388b075-2553-4ddd-9084-6bf530086059/%ED%99%94%EB%A9%B4_%EC%BA%A1%EC%B2%98_2023-12-03_184222.png)