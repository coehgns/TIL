# CSS3 Box Model

- 모든 HTML 요소는 Box 형태의 영역을 가지고 있음.
- Box는 콘텐트, 패딩, 테두리, 마진으로 구성되어 있음.

![box-model.png](https://prod-files-secure.s3.us-west-2.amazonaws.com/510cd684-c9a0-45bd-b45d-b35ad6027628/d89002d5-edd9-45f2-83ee-ea9d48434bb9/box-model.png)

- 브라우저는 박스 모델의 크기와 프로퍼티(색, 배경, 모양 등), 위치를 근거로 하여 렌더링을 실행함.
- 웹디자인은 콘텐츠를 담을 박스 모델을 정의하고 CSS 프로퍼티를 통해 스타일(배경, 폰트와 텍스트 등)과 위치 및 정렬을 지정하느 ㄴ것이라고 할 수 있음.
- Box 모델 구성 설명

| 명칭    | 설명                                                         |
| ------- | ------------------------------------------------------------ |
| Content | 요소의 텍스트나 이미지 등의 실제 내용이 위치하는 영역이다. width, height 프로퍼티를 갖는다. |
| Padding | 테두리(Border) 안쪽에 위치하는 요소의 내부 여백 영역이다. padding 프로퍼티 값은 패딩 영역의 두께를 의미하며 기본색은 투명(transparent)이다. 요소에 적용된 배경의 컬러, 이미지는 패딩 영역까지 적용된다. |
| Border  | 테두리 영역으로 border 프로퍼티 값은 테두리의 두께를 의미한다. |
| Margin  | 테두리(Border) 바깥에 위치하는 요소의 외부 여백 영역이다. margin 프로퍼티 값은 마진 영역의 두께를 의미한다. 기본적으로 투명(transparent)하며 배경색을 지정할 수 없다. |

## 1. width/ height 프로퍼티

- width와 height 프로퍼티는 요소의 너비와 높이를 지정하기 위해 사용됨. 지정되는 요소의 너비와 높이는 콘텐츠 영역을 대상으로 함.
- overflow: hidden; 을 지정하면 넘친 콘텐를 감출 수 있음.
- 전체 너비
  - width + left padding + right padding + left border + right border + left magin + right margin
- 전체 높이
  - height + top padding + bottom padding + top border + bottom border + top margin + bottom margin

![box-model-calc.png](https://prod-files-secure.s3.us-west-2.amazonaws.com/510cd684-c9a0-45bd-b45d-b35ad6027628/e1f83602-b8c8-432b-a193-9696505f144e/box-model-calc.png)

**Width**

492px = 20px + 6px + 20px + 400px + 20px + 6px + 20px

**Height**

192px = 20px + 6px + 20px + 100px + 20px + 6px + 20px

- 명시적을 width 와 height를 지정하기 위해서는 px, % 등의 크기 단위를 사용함.

## 2.margin/padding 프로퍼티

- margin / padding 프로퍼티는 content의 4개 방향 (top, right, left, bottom)에 대하여 지정이 가능함.

  ![box-model-detail.png](https://prod-files-secure.s3.us-west-2.amazonaws.com/510cd684-c9a0-45bd-b45d-b35ad6027628/7cf913ca-3e79-4146-a96e-1be25233e510/box-model-detail.png)

- top, -right, -bottom, -left 4방향의 프로퍼티를 각각 지정하지 않고 margin, padding 1개의 프로퍼티만으로 4방향의 프로퍼티를 한번에 지정할 수 있음.

**4개의 값을 지정할 때**

margin: 25px 50px 75px 100px; • margin-top: 25px; • margin-right: 50px; • margin-bottom: 75px; • margin-left: 100px;

**3개의 값을 지정할 때**

margin: 25px 50px 75px; • margin-top: 25px; • margin-right: 50px; margin-left: 50px; • margin-bottom: 75px

**2개의 값을 지정할 때**

margin: 25px 50px; • margin-top: 25px; margin-bottom: 25px; • margin-right: 50px; margin-left: 50px;

**1개의 값을 지정할 때**

margin: 25px; • margin-top: 25px; margin-right: 25px; margin-bottom: 25px; margin-left: 25px;

- max-width 프로퍼티를 사용하면 브라우저 너비가 요소의 너비보다 좁알질 때 자동으로 요소의 너비가 줄어듦.

## 3. border 프로퍼티

### 3.1 border-style

- border-style 프로퍼티는 테두리 선의 스타일을 지정함.

```html
<!DOCTYPE html>
<html>
  <head>
    <style>
      p {
        background: palegreen;
        padding: 10px;
      }
      p.dotted { border-style: dotted; }
      p.dashed { border-style: dashed; }
      p.solid  { border-style: solid; }
      p.double { border-style: double; }
      p.groove { border-style: groove; }
      p.ridge  { border-style: ridge; }
      p.inset  { border-style: inset; }
      p.outset { border-style: outset; }
      p.none   { border-style: none; }
      p.hidden { border-style: hidden; }
      p.mix    { border-style: dotted dashed solid double; }
    </style>
  </head>
  <body>
    <h2>border-style Property</h2>

    <p class="dotted">dotted</p>
    <p class="dashed">dashed</p>
    <p class="solid">solid</p>
    <p class="double">double</p>
    <p class="groove">groove</p>
    <p class="ridge">ridge</p>
    <p class="inset">inset</p>
    <p class="outset">outset</p>
    <p class="none">none</p>
    <p class="hidden">hidden</p>
    <p class="mix">dotted dashed solid double</p>
  </body>
</html>
```

- result

  ![border-style.png](https://prod-files-secure.s3.us-west-2.amazonaws.com/510cd684-c9a0-45bd-b45d-b35ad6027628/1411d457-8154-440b-b8c9-b69687632c35/border-style.png)

### 3.2 border-width

- border-width 프로퍼티는 테두리의 두께를 지정함. 프로퍼티 값의 갯수에 따라 4개 방향에 대하여 지정 가능.
- border-width 프로퍼티는 border-style과 함께 사용하지 않으면 적용되지 않음.

```html
<!DOCTYPE html>
<html>
  <head>
    <style>
      p {
        background: palegreen;
        padding: 10px;
        border-style: solid
      }
      p.one {
        border-width: thin; /* 1px */
      }
      p.two {
        border-width: medium; /* 3px */
      }
      p.three {
        border-width: thick; /* 5px */
      }
      p.four {
        border-width: 15px;
      }
      p.five {
        border-width: 2px 10px 4px 20px;
      }
    </style>
  </head>
  <body>
    <h2>border-width Property</h2>

    <p>initial: 3px</p>
    <p class="one">thin: 1px</p>
    <p class="two">medium: 3px</p>
    <p class="three">thick: 5px</p>
    <p class="four">15px</p>
    <p class="five">2px 10px 4px 20px</p>
  </body>
</html>
```

- result

  ![border-width.png](https://prod-files-secure.s3.us-west-2.amazonaws.com/510cd684-c9a0-45bd-b45d-b35ad6027628/d0270bdc-17de-4aba-be5b-32ec464e027c/border-width.png)

### border-color

- border-color 프로퍼티는 테두리의 색상을 지정함.
- border-color 프로퍼티는 border-style과 함께 사용하지 않으면 적용되지 않음.

```html
<!DOCTYPE html>
<html>
  <head>
    <style>
      p {
        background: palegreen;
        padding: 10px;
        border-style: solid;
      }
      p.one {
        border-color: red;
      }
      p.two {
        border-color: green;
      }
      p.three {
        border-color: red green blue yellow;
      }

    </style>
  </head>
  <body>
    <h2>border-color Property</h2>

    <p class="one">border-color: red</p>
    <p class="two">border-color: green</p>
    <p class="three">border-color: red green blue yellow</p>
  </body>
</html>
```

- result

  ![border-color.png](https://prod-files-secure.s3.us-west-2.amazonaws.com/510cd684-c9a0-45bd-b45d-b35ad6027628/bd9ed478-4dbe-413a-87e6-2cf4891f3846/border-color.png)

### 3.4 border-radius

- border-radius 프로퍼티는 테두리 모서리를 둥글게 표현하도록 지정함.
- 프로퍼티 값은 길이를 나타내는 단위(px,em 등)와 %를 사용함.
- 각각의 모서리에 border-radius 프로퍼티를 개별적으로 지정할 수도 있고 4개의 모서리를 shor-hand로 한번에 지정할 수도 있다.

```html
<!DOCTYPE html>
<html>
  <head>
    <style>
      div {
        background: #eaeaed;
        color: #666;
        display: inline-block;
        width: 90px;
        height: 90px;
        line-height: 90px;
        margin: 0 14px;
        text-align: center;
      }

      .border-rounded {
        /* 4 꼭지점에 대해 Radius 지정 */
        border-radius: 5px;
      }
      .border-circle {
        border-radius: 50%;
      }
      .border-football {
        /* top-left & bottom-right | top-right & bottom-left */
        border-radius: 15px 75px;
      }
    </style>
  </head>
  <body>
    <div class="border-rounded">5px</div>
    <div class="border-circle">50%</div>
    <div class="border-football">15px 75px</div>
  </body>
</html>
```

- result

  ![bordre-radius.png](https://prod-files-secure.s3.us-west-2.amazonaws.com/510cd684-c9a0-45bd-b45d-b35ad6027628/d400e999-61bd-4d83-8fae-4def788889cd/bordre-radius.png)

```css
/*모든 모서리에 동일한 둥근 모서리 설정*/
.border-rounded {
  border-radius: 20px;

  /* 위 코드는 아래의 shorthand이다.
  border-top-left-radius:     20px;
  border-top-right-radius:    20px;
  border-bottom-right-radius: 20px;
  border-bottom-left-radius:  20px;
  */
}
```

![IC485208.png](https://prod-files-secure.s3.us-west-2.amazonaws.com/510cd684-c9a0-45bd-b45d-b35ad6027628/7c080b65-89e0-44f0-bd38-ce7ba31213a2/IC485208.png)

### 3.5 border

- border 프로퍼티는 border-width, border-style, border-color를 한번에 설정하기 위한 shorthand 프로퍼티임.

```html
CODE
/* Syntax */
border: border-width border-style border-color;
p {
  /* border-width border-style border-color */
  border: 5px solid red;
}
```

## 4. box-sizing 프로퍼티

- box-sizing 프로퍼티는 width, height 프로퍼티의 대상 영역을 변결할 수 있음.
- box-sizing 프로퍼티의 값을 border-box로 지정하면 마진을 제외한 박스 모델 전체를 width,height 프로퍼티의 대상 영역으로 지정할 수 있어서 CSS Layout을 직관적으로 사용할 수 있게 함.

| 키워드      | 설명                                                         |
| ----------- | ------------------------------------------------------------ |
| content-box | width, height 프로퍼티 값은 content 영역을 의미한다. (기본값) |
| border-box  | width, height 프로퍼티 값은 content 영역, padding, border가 포함된 값을 의미한다. |

![box-sizing.png](https://prod-files-secure.s3.us-west-2.amazonaws.com/510cd684-c9a0-45bd-b45d-b35ad6027628/b8d1239d-2011-4ffb-810b-ca89ed7a5063/box-sizing.png)

- box-sizing 프로퍼티는 상속되지 않음.
- box-sizing 프로퍼티를 사용하도록 초기화하려면 아래와 같이 정의하면 됨.

```css
html {
  box-sizing: border-box;
}
*, *:before, *:after {
  box-sizing: inherit;
}
```