# CSS3 Responsive Web Design

## 1. Responsive Web Design 개요

- layout은 방문자의 화면 해상도를 고려하여야 하는데 가로폭이 너무 큰 layout을 작성하면 작은 해상도 모니터로 방문하였을 때 가로 스크롤이 생겨서 사용이 불편할 수 도 있음.

- 반응형 웹디자인은 화면 해상도에 따라 가로폭이나 배치를 변경하여 가독성을 높이는데 하나의 웹사이트를 구축하여 다양한 디바이스의 화면 해상도에 최적화된 웹사이트를 제공함.

  ![Responsive_Web_Design_for_Desktop_Notebook_Tablet_and_Mobile_Phone.png](https://prod-files-secure.s3.us-west-2.amazonaws.com/510cd684-c9a0-45bd-b45d-b35ad6027628/289254a8-22b5-4b30-926f-853d45d98ebc/Responsive_Web_Design_for_Desktop_Notebook_Tablet_and_Mobile_Phone.png)

### 1.1 viewport meta tag

- viewport란 웹페이지의 가시영역을 의미함.

- viewport를 이용하여 디바이스의 특성과 디바이스의 화면 크기 등을 고려하여 각종 디바이스 사용자에게 최적화된 웹페이지를 제공할 수 있음.

  ![viewportExample.jpg](https://prod-files-secure.s3.us-west-2.amazonaws.com/510cd684-c9a0-45bd-b45d-b35ad6027628/286f30cb-0843-4115-b7f4-d973cdf0f93f/viewportExample.jpg)

- viewport meta tag는 브라우저의 화면 설정과 관련된 정보를 제공함.

| 프로퍼티      | Description                      | 사용예              |
| ------------- | -------------------------------- | ------------------- |
| width         | viewport 너비(px). 기본값: 980px | width=240           |
|               |                                  | width=device-width  |
| height        | viewport 높이(px)                | height=800          |
|               |                                  | width=device-height |
| initial-scale | viewport초기 배율                | initial-scale=1.0   |
| user-scale    | 확대 축소 가능 여부              | user-scale=no       |
| maximum-scale | viewport 최대 배율               | maximum-scale=2.0   |
| minimum-scale | viewport 최소 배율               | minimum-scale=1.0   |

- meta tag에서는 px단위를 사용하며 단위 표현은 생략하고 복수개의 프로퍼티를 사용할 때는 쉼표(,)로 구분함.(일반적으로 viewport meta tag는 모바일 디바이스에서만 적용됨.)

```html
/* 가장 일반적인 viewport 설정 */
<meta name="viewport" content="width=device-width, initial-scale=1.0">
```

### 1.2 @media

- @media는 서로 다른 미디어 타입(print,screen…)에 따라 각각의 styles를 지정하는 것을 가능하게 함.

```html
/* 일반 화면과 인쇄장치 별로 서로 다른 style응 지정하는 예 */
<!DOCTYPE html>
<html>
<head>
  <meta name="viewport" content="width=device-width, initial-scale=1.0">
  <style>
    @media screen {
      * { color: red; }
    }
    @media print {
      * { color: blue; }
    }
  </style>
</head>
<body>
  <h1>@media practice</h1>
  <p>Lorem ipsum dolor sit amet, consectetur adipisicing elit, sed do eiusmod tempor incididunt ut labore et dolore magna aliqua. Ut enim ad minim veniam, quis nostrud exercitation ullamco laboris nisi ut aliquip ex ea commodo consequat. Duis aute irure dolor in reprehenderit in voluptate velit esse cillum dolore eu fugiat nulla pariatur. Excepteur sint occaecat cupidatat non proident, sunt in culpa qui officia deserunt mollit anim id est laborum.</p>
</body>
</html>
```

- result

  ![@media.png](https://prod-files-secure.s3.us-west-2.amazonaws.com/510cd684-c9a0-45bd-b45d-b35ad6027628/18443ef7-59db-4dc8-9905-967bdbae8168/media.png)

- 반응형 웹디자인에 사용되는 핵심 기술은 @media인데 @media를 사용하여 미디어 별로 style을 지정하는 것을 Media Query라고 함.(디바이스를 지정하는 것 뿐만 아니라 디바이스의 크기나 비율까지 구분할 수 있음.)

```html
Media Query의 문법
@media not|only mediatype and (expressions) {
  CSS-Code;
}
@media screen and (min-width: 480px) {
  body {
    background-color: lightgreen;
  }
}
```

- Media Querty의 표현식에서 사용할 수 있는 프로퍼티

| 프로퍼티            | Description                                              |
| ------------------- | -------------------------------------------------------- |
| width               | viewport 너비(px)                                        |
| height              | viewport 높이(px)                                        |
| device-width        | 디바이스의 물리적 너비(px)                               |
| device-height       | 디바이스의 물리적 높이(px)                               |
| orientation         | 디바이스 방향 (가로 방향: landscape, 세로방향: portrait) |
| device-aspect-ratio | 디바이스의 물리적 width/height 비율                      |
| color               | 디바이스에서 표현 가능한 최대 색상 비트수                |
| monochrome          | 흑백 디바이스의 픽셀 당 비트수                           |
| resolution          | 디바이스 해상도                                          |

- orientation을 제외한 모든 프로퍼티는 min/max 접두사를 사용할 수 있음.

```html
/* 화면이 세로일 때, 가로일 때를 구분하는 예제 */
<!DOCTYPE html>
<html>
<head>
  <meta name="viewport" content="width=device-width, initial-scale=1.0">
  <style>
    /* 세로  */
    * { color: black; }
    /* 가로 */
    /* Desktop의 화면은 가로화면(landscape)이므로 아래 rule이 적용된다. */
    /*
    @media screen and (orientation: landscape) {
      { color: blue; }
    }
    */

    /* Landscape */
    @media screen
      /* 디바이스가 모바일일때(device-width 0 ~ 768px) */
      and (max-device-width: 760px)
      /* 가로 */
      and (orientation: landscape) {
      * { color: blue; }
    }
  </style>
</head>
<body>
  <h1>@media practice: orientation</h1>
  <p>Lorem ipsum dolor sit amet, consectetur adipisicing elit, sed do eiusmod tempor incididunt ut labore et dolore magna aliqua. Ut enim ad minim veniam, quis nostrud exercitation ullamco laboris nisi ut aliquip ex ea commodo consequat. Duis aute irure dolor in reprehenderit in voluptate velit esse cillum dolore eu fugiat nulla pariatur. Excepteur sint occaecat cupidatat non proident, sunt in culpa qui officia deserunt mollit anim id est laborum.</p>
</body>
</html>
```

- result

  ![가로 세로 구분.png](https://prod-files-secure.s3.us-west-2.amazonaws.com/510cd684-c9a0-45bd-b45d-b35ad6027628/27e18cc2-8263-4e7f-b020-bcdabb8b29b6/%EA%B0%80%EB%A1%9C_%EC%84%B8%EB%A1%9C_%EA%B5%AC%EB%B6%84.png)

## 2. Responsive Navigation Bar

```html
/* 디바이스 해상도에 따라 반응할 수 있도록 viewport meta tag와 media query를 추가함. */
<!DOCTYPE html>
<html>
<head>
  <meta name="viewport" content="width=device-width, initial-scale=1.0">
  <style>
    /* Media Query */
    /* for Desktop: 801px ~ */

    /* for tablet: ~ 800px */
    @media screen and (max-width: 800px) {

    }
    /* for smartphone: ~ 480px */
    @media screen and (max-width: 480px) {

    }
  </style>
</head>
...
```

- 스마트폰, 태블릿, 데스크탑 그룹의 3단계로 구분하여 breakpoint를 정의함.

```css
/* for Desktop: 801px ~ */

/* for tablet: ~ 800px */
@media screen and (max-width: 800px) {
}
```

- 800px 한정 → 화면 크기가 800px 이하인 디바이스를 위한 정의란 의미.

```css
/* for smartphone: ~ 480px */
@media screen and (max-width: 480px) {
}
```

- 480px 한정 → 화면 크기가 480px 이하인 디바이스를 위한 정의란 의미.
- CSS 적용 우선 순위에 따라 나중에 선언된 스타일이 우선 적용됨.(Media Query는 기술 순서에 의미가 있음.)

```css
/* Media Query */
/* for Desktop: 801px ~ */

/* for smartphone: ~ 480px */
/*
Media Query는 기술 순서에 의미가 있다.
만일 스마트폰용 스타일을 태블릿용 스타일보다 먼저 기술하면 최종적으로 태블릿용 스타일이 적용된다.
Non Mobile First Method의 경우, max-width의 값이 큰 것부터 기술하여 한다.
*/
@media screen and (max-width: 480px) {

}

/* for tablet: ~ 800px */
@media screen and (max-width: 800px) {

}
```

## 2.1 Responsive Navigation Bar - Tablet

- 데스크탑 layout에서 화면이 작아질 때 header navigation bar는 header 영역 아래로 내려오는 현상이 발생함.
- viewport width가 800 px 이하가 되면 header 영역을 2단으로 구분하기 위하여 header 영역의 높이를 현재의 2배로 넓힘. 그리고 logo image와 navigation bar를 centering함.

```css
@media screen and (max-width: 800px) {
  header {
    height: 120px;
    text-align: center;
  }
}
```

- aside, section영역도 header의 height만큼 내려가야 함.

```css
@media screen and (max-width: 800px) {
  header {
    height: 120px;
    text-align: center;
  }
  #wrap {
    /* margin-top = header height */
    margin-top: 120px;
  }
  aside {
    top: 120px;
  }
}
```

- 가로로 나란히 정렬되어 있던 logo image와 navigation bar를 상단과 하단으로 분리 배치하기 위하여 navigation bar의 float: right; 프로퍼티를 해제함.
- navigation bar는 block 프로퍼티를 가지게 되어 logo image의 아래 영역으로 내려가게 됨.

```css
@media screen and (max-width: 800px) {
  header {
    height: 120px;
    text-align: center;
  }
  nav {
    float: none;
    /*margin-right: 0;*/
  }
  #wrap {
    /* margin-top = header height */
    margin-top: 120px;
  }
  aside {
    top: 120px;
  }
}
```

![res-layout-practice-1.png](https://prod-files-secure.s3.us-west-2.amazonaws.com/510cd684-c9a0-45bd-b45d-b35ad6027628/5a6aa5e2-c5b1-4b01-8795-f5633f94653a/res-layout-practice-1.png)

### 2.2 Responsive Navigation Bar - Smartphone

- nav 요소 내에 클릭할 수 있는 navigation icon을 만들기 위한 html tag를 추가함.
- label tag의 for 프로퍼티값과 input tag의 id 프로퍼티값이 일치하여야 함.

```html
<nav>
  <input class="nav-toggle" id="nav-toggle" type="checkbox">
  <label class="navicon" for="nav-toggle"><span class="navicon-bar"></span></label>
  <ul class="nav-items">
    <li><a href="#home">Home</a></li>
...
<label for="remeber-pw">Remeber password?</label>
<input type="checkbox" name="remeber-pw" id="remeber-pw">
```

- input checkbox 요소의 id 프로퍼티값과 label 요소의 for 프로퍼티값을 일치시켜 연동하면 label 요소를 클릭하여도 input checkbox 요소가 클릭됨.
- navigation icon은 input checkbox 요소와 연동되어야 하므로 label 요소를 사용함.

```css
/* navigation icon의 style */
.navicon {
  cursor: pointer;
  height: 60px;
  padding: 28px 15px;
  position: absolute;
  top: 0; right: 0;
}
```

- navigation icon은 header 우측의 절대 위치에 배치되어야 하므로 position: absolute;를 지정함.

```css
/* label tag 내의 span tag의 style을 정의. */
.navicon-bar {
  display: block;
  width: 20px;
  height: 3px;
  background-color: #333;
}
```

![res-layout-practice-4.png](https://prod-files-secure.s3.us-west-2.amazonaws.com/510cd684-c9a0-45bd-b45d-b35ad6027628/caaa72a0-6ad5-4b95-9727-5b80686010f7/res-layout-practice-4.png)

```css
/* 가상 요소 선택자를 사용하여 navigation icon의 내부 막대 앞뒤 공간에 내부 막대를 추가.*/
.navicon-bar::before,
.navicon-bar::after {
  background-color: #333;
  content: "";
  display: block;
  height: 100%;
  width: 100%;
  position: absolute;
}
.navicon-bar::before {
  top: -7px;
}
.navicon-bar::after {
  top: 7px;
}
```

- 절대 위치를 지정하기 위해 position: absolute; 를 사용하였으므로 가상 요소의 부모 요소인 span 요소(,navicon-bar)에 position: relative; 를 추가함.

```css
.navicon-bar {
  background-color: #333;
  display: block;
  position: relative;
  width: 20px;
  height: 3px;
}
```

![res-layout-practice-5.png](https://prod-files-secure.s3.us-west-2.amazonaws.com/510cd684-c9a0-45bd-b45d-b35ad6027628/5f2607a3-a3a8-4546-ad09-5c63832c3e62/res-layout-practice-5.png)

- input checkbox tag의 가상 클래스 선택자 checked를 이용하여 클릭되었을 때(input:checked)와 그렇지 않을 때를 구분할 수 있음.

```css
.nav-toggle:checked ~ .navicon > .navicon-bar {
  background: transparent;
}
.nav-toggle:checked ~ .navicon > .navicon-bar::before {
  transform: rotate(45deg);
  top: 0;
}
.nav-toggle:checked ~ .navicon > .navicon-bar::after {
  transform: rotate(-45deg);
  top: 0;
}
```

- 중간에 위치한 막대를 업새고 상하 막대를 45도 회전시킴.(이때 위치가 틀어지므로 top: 0; 으로 보정함.)

  ![res-layout-practice-6.png](https://prod-files-secure.s3.us-west-2.amazonaws.com/510cd684-c9a0-45bd-b45d-b35ad6027628/130ffd15-bbff-4ff8-b1b4-2acb57780d7f/res-layout-practice-6.png)

- navigation icon에 transition 효과를 부여하여 좀 더 부드럽게 움직이도록 함.

```css
.navicon-bar {
  background-color: #333;
  display: block;
  position: relative;
  transition: background-color .2s ease-out;
  width: 20px;
  height: 3px;
}
.navicon-bar::before,
.navicon-bar::after {
  background-color: #333;
  content: "";
  display: block;
  height: 100%;
  width: 100%;
  position: absolute;
  transition: all .2s ease-out;
}
```

- transition 프로퍼티는 property, duration, delay 순으로 정의함.

  ![res-layout-practice-7.png](https://prod-files-secure.s3.us-west-2.amazonaws.com/510cd684-c9a0-45bd-b45d-b35ad6027628/1a58dffc-f4be-4a65-8550-a5e5b2b29b53/res-layout-practice-7.png)

- 이것은 navigation icon이 텍스트이기 때문에 발생하는 문제인데 이 문제는 텍스트 선택을 차단하는 방법인 user-select: none; 프로퍼티를 지정하여 회피할 수 있음.

```css
.navicon {
  cursor: pointer;
  height: 60px;
  padding: 28px 15px;
  position: absolute;
  top: 0; right: 0;

  -webkit-user-select: none;  /* Chrome all / Safari all */
  -moz-user-select: none;     /* Firefox all */
  -ms-user-select: none;      /* IE 10+ */
  user-select: none;          /* Likely future */
}
```

- navigation icon과 checkbox input tag는 스마트폰 layout 이외의 경우 화면에 표시되면 안됨.
- display: none; 으로 화면에 표시되지 않도록 함.
- 일반적으로 media query를 가장 마지막에 정의하므로 media query 정의부 직전에 위치시킴.

```css
.nav-toggle {
  display: none;
}
.navicon {
  display: none;
}
```

- tablet용 layout에서 header height를 2배로 하였으므로 mobile용 layout을 위해 다시 60px로 되돌림.

```css
@media screen and (max-width: 480px) {
  header {
    height: 60px;
  }
}
```

- 스마트폰 layout에서는 navigation bar가 초기상태에서 비표시되어야 함.
- navigation icon은 표시되어야 함.(아직 navigation icon을 완성하지 않았으므로 표시되지 않음.)

```css
@media screen and (max-width: 480px) {
  header {
    height: 60px;
  }
  .nav-items {
    display: none;
  }
  .navicon {
    display: block;
  }
}
```

- header 영역 바로 아래로 다시 끌어 올림.

```css
@media screen and (max-width: 480px) {
  /*...*/
  #wrap {
    /* margin-top = header height */
    margin-top: 60px;
  }
  aside {
    top: 60px;
  }
  /*...*/
}
```

- 마지막으로 navigation icon을 클릭하면 navigation item이 표시되도록 함.

```css
@media screen and (max-width: 480px) {
  ...

  .nav-toggle:checked ~ .nav-items {
    display: block;
    width: 100%;
    background-color: #fff;
    box-shadow: 0 2px 2px rgba(0, 0, 0, 0.05), 0 1px 0 rgba(0, 0, 0, 0.05);
  }
  .nav-items > li  {
    display: block;
  }
  .nav-items > li > a {
    line-height: 50px;
  }
}
```

## 3. Section & Aside & Footer

- article은 layout에 상관없이 1행에 1개씩 배치되었음.(1행에 2열로 배치하면 responsive web design의 효과를 좀 더 체감할 수 있음.)
- article을 2열로 배치하기 위해서 width 값을 지정해야 함.
- %로 width 값을 지정하여 viewport에 상대적인 너비를 갖도록 함.(이때 margin도%로 지정함. 그리고 float: left;를 지정하여 2열로 정렬되도록 함.)

```css
article {
  width: 48.5%;
  margin: 1%;
  padding: 25px;
  background-color: white;
  float: left;
}
```

- 짝수번째 배치되는 article의 좌측 마진과 3번째부터 등장하는 article의 우측 마진을 0으로 하여 가운데 마진이 2배가 되는 것을 방지함.

```css
article:nth-of-type(2n) {
  margin-left: 0;
}
article:nth-of-type(n+3) {
  margin-top: 0;
}
```

- tablet layout을 작성. 800px 이하로 화면이 작아지면 2열로 배치되어 있던 article을 1열로 배치함.

```css
@media screen and (max-width: 800px) {
  ...
  article {
    width: inherit;
    display: block;
    margin: 10px;
    float: none;
  }
  article:nth-of-type(2n) {
    margin: 10px;
  }
  article:nth-of-type(n+2) {
    margin-top: 0;
  }
}
```

- mobile layout을 작성. 480px 이하로 화면이 작아지면 고정 배치되어 있던 aside를 article 위로 올려 배치함.

```css
@media screen and (max-width: 480px) {
  /*...*/
  aside {
    top: 60px;
    position: static;
    width: 100%;
    padding: 5px 0;
  }
  /* aside navigation */
  aside > ul {
    width: 100%;
  }
  aside > h1 {
    padding: 5px 0 10px 20px;
    color: #fff;
  }
  section {
    float: none;
    margin-left: 0;
  }
  /*...*/
}
```