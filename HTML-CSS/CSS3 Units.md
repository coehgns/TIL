# CSS3 - Units

### 1. 키워드

각 프로퍼티에 따라 사용할 수 있는 키워드가 존재함.

ex) display 프로퍼티의 값으로 사용할 수 있는 키워드는 block, inline, inline-block, none이 있음.

### 2. 크기 단위

cm, mm, inch 등의 단위도 존재하나 CSS에서 사용하는 대표적인 크기 단위는 px, em, %임.

px는 절대값이고 em, %는 상대 값임.

대부분 브라우저의 폰트 사이즈 기본값은 16px, 1em, 100%임. (프로퍼티 값이 0인 경우, 단위를 생략 가능.)

#### 2.1 px

px은 픽셀(화소) 단위. 1px은 화소 1개 크기를 의미함. 

해상도가 1680*1050인 모니터는 가로에 1680개의 픽셀, 세로에 1050개의 픽셀을 가진다는 의미임.

픽셀은 디바이스 해상도에 따라 상대적인 크기를 갖음.

대부분의 브라우저는 1px을 1/96 인치의 절대 단위로 인식함.

CSS

복사

캡션



<!DOCTYPE html>
<html>
<head>
  <style>
    body {
      text-align: center;
    }
    div {
      font-size: 14px;
      font-weight: bold;
      padding: 2em; /* 14px * 2 = 28px */
      background-color: rgba(255, 0, 0, 0.2);
    }
  </style>
</head>
<body>
  <div>Font size: 14px</div>
</body>
</html>



result

![img](notion://www.notion.so/image/https%3A%2F%2Fprod-files-secure.s3.us-west-2.amazonaws.com%2F510cd684-c9a0-45bd-b45d-b35ad6027628%2F83b59a60-c650-420f-8a43-792b335dd7b3%2Fpx.png?table=block&id=0f805d18-c34e-4ec0-92ea-c4f003650483&spaceId=510cd684-c9a0-45bd-b45d-b35ad6027628&width=1570&userId=f4300f36-5424-46cc-8d1c-b19f0c3dd9c2&cache=v2)









#### 2.2 %

%는 백분률 단위의 상대 단위임.

요소에 지정된 사이즈에 상대적인 사이즈를 설정함.

CSS

복사

캡션



<!DOCTYPE html>
<html>
<head>
  <style>
    body {
      font-size: 14px;
      text-align: center;
    }
    div {
      font-size: 120%; /* 14px * 1.2 = 16.8px */
      font-weight: bold;
      padding: 2em;    /* 16.8px * 2 = 33.6px */
      background-color: rgba(255, 0, 0, 0.2);
    }
  </style>
</head>
<body>
  <div>Font size: 14px * 120% → 16.8px</div>
</body>
</html>



result

![img](notion://www.notion.so/image/https%3A%2F%2Fprod-files-secure.s3.us-west-2.amazonaws.com%2F510cd684-c9a0-45bd-b45d-b35ad6027628%2F11587f4c-4012-48c4-84f7-83e3bc1f9e4f%2F.png?table=block&id=c639fc02-9b2a-49fa-bfcf-b737bdbfef82&spaceId=510cd684-c9a0-45bd-b45d-b35ad6027628&width=1580&userId=f4300f36-5424-46cc-8d1c-b19f0c3dd9c2&cache=v2)









#### 2.3 em

em은 배수 단위로 상대 단위임. 

요소에 지정된 사이즈에 상대적인 사이즈를 설정함.(ex: 1em은 요소에 지정된 사이즈와 같고 2em은 요소에 지정된 사이즈의 2배임.)

CSS

복사

캡션



<!DOCTYPE html>
<html>
<head>
  <style>
    body {
      font-size: 14px;
      text-align: center;
    }
    div {
      font-size: 1.2em; /* 14px * 1.2 = 16.8px */
      font-weight: bold;
      padding: 2em;     /* 16.8px * 2 = 33.6px */
      background-color: rgba(255, 0, 0, 0.2);
    }
  </style>
</head>
<body>
  <div>Font size: 1.2em → 14px * 1.2 = 16.8px</div>
</body>
</html>



result

![img](notion://www.notion.so/image/https%3A%2F%2Fprod-files-secure.s3.us-west-2.amazonaws.com%2F510cd684-c9a0-45bd-b45d-b35ad6027628%2F7fe060d6-cb28-4f72-a5da-e8ba9d5d120e%2Fem.png?table=block&id=d11b2d05-9f91-468e-a124-2b199c99f291&spaceId=510cd684-c9a0-45bd-b45d-b35ad6027628&width=2000&userId=f4300f36-5424-46cc-8d1c-b19f0c3dd9c2&cache=v2)









#### 2.4 rem

em의 기준은 상속의 영향으로 바뀔 수 있음.

rem은 최상위 요소(html)의 사이즈를 기준으로 삼음.

rem의 r은 root를 의미.

CSS

복사

캡션



<!DOCTYPE html>
<html>
<head>
  <style>
    html {
      font-size: 14px;
      /* font-size 미지정 시에는 16px */
    }
    div {
      font-size: 1.2rem; /* html font-size: 14px * 1.2 = 16.8px */
      font-weight: bold;
      padding: 2em;
      text-align: center;
    }
    .box1 { background-color: rgba(255, 0, 0, 0.2); }
    .box2 { background-color: rgba(255, 0, 0, 0.6); }
    .box3 { background-color: rgba(255, 0, 0, 0.8); }
  </style>
</head>
<body>
  <div class='box1'>
    Font size: 1.2rem ⇒ 14px * 1.2 = 16.8px
    <div class='box2'>
      Font size: 1.2rem ⇒ 14px * 1.2 = 16.8px
      <div class='box3'>
        Font size: 1.2rem ⇒ 14px * 1.2 = 16.8px
      </div>
    </div>
  </div>
</body>
</html>



result

![img](notion://www.notion.so/image/https%3A%2F%2Fprod-files-secure.s3.us-west-2.amazonaws.com%2F510cd684-c9a0-45bd-b45d-b35ad6027628%2F5ef2a72e-01e3-4b22-94f7-b8fc6c82cb83%2Frem.png?table=block&id=b71bebe8-7d8b-4383-9bef-8a4ce34bfabc&spaceId=510cd684-c9a0-45bd-b45d-b35ad6027628&width=1600&userId=f4300f36-5424-46cc-8d1c-b19f0c3dd9c2&cache=v2)









#### 2.5 Viewport 단위(vh, vw, vmin, vmax)

Viewport 단위는 상대적인 단위로 viewport를 기준으로 한 상대적 사이즈를 의미함.

| 단위 | Description                                |
| ---- | ------------------------------------------ |
| vw   | viewport 너비의 1/100                      |
| vh   | viewport 높이의 1/100                      |
| vmin | viewport 너비 또는 높이 중 작은 쪽의 1/100 |
| vmax | viewport 너비 또는 높이 중 큰 쪽의 1/100   |







viewport 너비가 1000px, 높이가 600px인 경우

1vw : viewport 너비 1000px의 1%인 10px

1vh : viewport 높이 600px의 1%인 6px

vmin : viewport 높이 600px의 1%인 6px

vmax : viewport 너비 1000px의 1%인 10px

### 3. 색상 표현 단위

색상을 지정하기 위해 키워드를 사용할 수 있다.

표현할 수 있는 색상의 수는 제한됨.

색상 표현 단위

| 단위                                            | 사용예                 |
| ----------------------------------------------- | ---------------------- |
| HEX 코드 단위 (Hexadecimal Colors)              | #000000                |
| RGB (Red, Green, Blue)                          | rgb(255, 255, 0)       |
| RGBA (Red, Green, Blue, Alpha/투명도)           | rgba(255, 255, 0, 1)   |
| HSL (Hue/색상, Saturation/채도, Lightness/명도) | hsl(0, 100%, 25%)      |
| HSLA (Hue, Saturation, Lightness, Alpha)        | hsla(60, 100%, 50%, 1) |