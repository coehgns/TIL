# CSS3 Display

## 1. display 프로퍼티

- display 프로퍼티는 layout 정의에 자주 사용되는 중요한 프로퍼티임.

| 프로퍼티값 키워드 | 설명                                                         |
| ----------------- | ------------------------------------------------------------ |
| block             | block 특성을 가지는 요소(block 레벨 요소)로 지정             |
| inline            | inline 특성을 가지는 요소(inline 레벨 요소)로 지정           |
| inline-block      | inline-block 특성을 가지는 요소(inline-block 레벨 요소)로 지정 |
| none              | 해당 요소를 화면에 표시하지 않는다 (공간조차 사라진다)       |

- 모든 HTMl 요소는 아무런 CSS를 적용하지 않아도 기본적으로 브라우저에 표현되는 디폴트 표시값을 가짐.
- HTML 요소는 block 또는 inline 특성을 갖음.

```css
/*p 요소에 대한 크롬 브라우저의 디폴트 CSS*/
p {
  display: block;
  -webkit-margin-before: 1em;
  -webkit-margin-after: 1em;
  -webkit-margin-start: 0px;
  -webkit-margin-end: 0px;
}
```

### 1.1 block 레벨 요소

- block 특성을 가지는 요소(block 레벨 요소 또는 block 요소)는 특징을 갖음.
  - 항상 새로운 라인에서 시작함.
  - 화면 크기 전체의 가록폭을 차지함.
  - width, height, margin, padding 프로퍼티 지정이 가능함.
  - block 레벨 요소 내에 inline 레벨 요소를 포함할 수 있음.
  - block 레벨 오쇼 예
    - div
    - h1~h6
    - p
    - ol
    - ul
    - li
    - hr
    - table
    - form

```html
<!DOCTYPE html>
<html>
<head>
  <style>
    div:nth-of-type(1) {
      background-color: #FFA07A;
      padding: 20px;
    }
    div:nth-of-type(2) {
      background-color: #FF7F50;
      padding: 20px;
      width: 300px;
    }
  </style>
</head>
<body>
  <div>
    <h2>블록 레벨 요소</h2>
    <p>width, height 미지정 → width: 100%; height: auto;</p>
  </div>
  <div>
    <h2>블록 레벨 요소</h2>
    <p>width: 300px → width: 300px; height: auto;</p>
  </div>
</body>
</html>
```

- result

  ![블록 레벨 요소.png](https://prod-files-secure.s3.us-west-2.amazonaws.com/510cd684-c9a0-45bd-b45d-b35ad6027628/addfc495-8f42-4cb4-8710-027594f05b09/%EB%B8%94%EB%A1%9D_%EB%A0%88%EB%B2%A8_%EC%9A%94%EC%86%8C.png)

### 1.2 inline 레벨 요소

- inline 특성을 가지는 요소(inline 레벨 요소 또는 inline 요소)는 특징을 갖음.
  - 새로운 라인에서 시작하지 않으며 문장의 중간에 들어갈 수 있음. ( 줄을 바꾸지 않고 다른 요소와 함께 한 행에 위치함.)
  - content의 너비만큼 가로폭을 차지함.
  - width, height, margin-top, margin-bottom 프로퍼티를 지정할 수 있음. ( 상, 하 여백은 line-height로 지정함.)
  - inline 레벨 요소 뒤에 공백(엔터, 스페이스 등)이 있는 경우, 정의하지 않은 space(4px)가 자동 지정됨.
  - inline 레벨 요소 내에 block 레벨 요소를 포함할 수 없음.(inline 레벨 요소는 일반적으로 block 레벨 요소에 포함되어 사용됨.)
  - inline 레벨 요소 예
    - span
    - a
    - strong
    - img
    - br
    - input
    - select
    - textarea
    - button

```html
<!DOCTYPE html>
<html>
<head>
  <style>
    span {
      background-color: red;
      color: white;
      padding: 10px;
      /* width, height, margin-top, margin-bottom 프로퍼티를 지정할 수 없다. */
      /* width: 200px; */
      /* margin: 10px; */
      /* 상, 하 여백은 line-height로 지정한다. */
      /* line-height: 50px; */
    }
  </style>
</head>
<body>
  <h1>My <span>Important</span> Heading</h1>
  <span>Inline</span>
  <span>Inline</span><span>Inline</span>
</body>
</html>
```

- result

  ![inline 레벨 요소.png](https://prod-files-secure.s3.us-west-2.amazonaws.com/510cd684-c9a0-45bd-b45d-b35ad6027628/a95fa18b-54bf-4f02-a48e-62c5c9bfa855/inline_%EB%A0%88%EB%B2%A8_%EC%9A%94%EC%86%8C.png)

### 1.3 inline-block 레벨 요소

- block과 inline 레벨 요소의 특징을 모두 갖음. inline 레벨 요소와 같이 한 줄에 표현되면서 width, height, margin 프로퍼티를 모두 지정할 수 있음.
- 기본적으로 inline 레벨 요소와 흡사하게 줄을 바꾸지 않고 다른 요소와 함께 한 행에 위치 시킬 수 있음.
- block 레벨 요소처럼 width, height, margin, padding 프로퍼티를 모두 정의할 수 있음. (상, 하 여백을 margin과 line-height 두 가지 프로퍼티 모두를 통해 제어할 수 있음.)
- content의 너비만큼 가로폭을 차지함.
- inline-block 레벨 요소 뒤에 공백(엔터, 스페이스 등)이 있는 경우, 정의하지 않은 space(4px)가 자동 지정됨.

```html
<!DOCTYPE html>
<html>
<head>
  <style>
    .wrapper {
      font-size: 0; /*요소간 간격을 제거*/
    }
    .inline-block {
      display: inline-block;
      vertical-align: middle; /* inline-block 요소 수직 정렬 */
      border: 3px solid #73AD21;
      font-size: 16px;
    }
    .box1 {
      width: 300px;
      height: 70px;
    }
    .box2 {
      width: 300px;
      height: 150px;
    }
  </style>
</head>
<body>
  <div class="inline-block box1">inline-block height 70px</div>
  <div class="inline-block box2">inline-block height 150px</div>

  <div class="wrapper">
    <div class="inline-block box1">inline-block height 70px</div>
    <div class="inline-block box2">inline-block height 150px</div>
  </div>
</body>
</html>
```

- result

  ![inline-block 요소.png](https://prod-files-secure.s3.us-west-2.amazonaws.com/510cd684-c9a0-45bd-b45d-b35ad6027628/f56565b5-71da-433e-9456-ed87e3e4f3de/inline-block_%EC%9A%94%EC%86%8C.png)

## 2. visibility 프로퍼티

- visibility 프로퍼티는 요소를 보이게 할 것인지 보이지 않게 할 것인지를 정의함. (요소의 렌더링 여부를 결정함.)

| 프로퍼티값 키워드 | 설명                                                         |
| ----------------- | ------------------------------------------------------------ |
| visible           | 해당 요소를 보이게 한다 (기본값)                             |
| hidden            | 해당 요소를 보이지 않게 한다. display: none;은 해당 요소의 공간까지 사라지게 하지만 visibility: hidden;은 해당 요소의 공간은 사라지지 않고 남아있게 된다. |
| collapse          | table 요소에 사용하며 행이나 열을 보이지 않게 한다.          |
| none              | table 요소의 row나 column을 보이지 않게 한다. IE, 파이어폭스에서만 동작하며 크롬에서는 hidden과 동일하게 동작한다. |

```html
<!DOCTYPE html>
<html>
<head>
  <style>
    .visible { visibility: visible; }
    .hidden  { visibility: hidden; }

    table, td { border: 1px solid black; }
    .collapse { visibility: collapse; }
    /* .collapse { visibility: hidden; } */
  </style>
</head>
<body>
  <h1 class="visible">visibility: visible</h1>
  <h1 class="hidden">visibility: hidden</h1>
  <h1 style="display:none">display:none</h1>

  <table>
    <tr>
      <td>A</td>
      <td>B</td>
    </tr>
    <tr class="collapse">
      <td>C</td>
      <td>D</td>
    </tr>
  </table>
</body>
</html>
```

- result

  ![visibility 프로퍼티.png](https://prod-files-secure.s3.us-west-2.amazonaws.com/510cd684-c9a0-45bd-b45d-b35ad6027628/dde7fd00-6ac0-4a8e-9076-53e2f3f14a1d/visibility_%ED%94%84%EB%A1%9C%ED%8D%BC%ED%8B%B0.png)

## 3. opacity 프로퍼티

- opacity 프로퍼티는 요소의 투명도를 정의함. (0.0~1.0의 값을 입력하며 0.0은 투명, 1.0은 불투명을 의미.)

```html
<!DOCTYPE html>
<html>
<head>
  <style>
    div, img {
      float: left;
      width: 150px;
      height: 150px;
      margin: 30px;
      background-color: blue;
      color: white;
      opacity: 0.5;
      transition: opacity 1s;
    }
    div:hover, img:hover {
      opacity: 1.0;
    }
  </style>
</head>
<body>
  <div>opacity: 0.5</div>
  <img src="<https://poiemaweb.com/img/doug.jpg>" alt="doug">
</body>
</html>
```

- result

![opacity.png](https://prod-files-secure.s3.us-west-2.amazonaws.com/510cd684-c9a0-45bd-b45d-b35ad6027628/6633983e-b867-49f9-977f-15bd25c87bf3/opacity.png)