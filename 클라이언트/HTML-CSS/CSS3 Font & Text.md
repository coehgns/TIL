# CSS3 Font & Text

- 폰트 및 텍스트 관련 프로퍼티는 폰트의 크기, 폰트의 지정, 폰트의 스타일, 텍스트 정렬 등을 정의함.

## 1. font-size 프로퍼티

- 텍스트의 크기를 정의함.

```html
<!DOCTYPE html>
<html>
<head>
  <style>
    .font-size-40 { font-size: 40px; }
    .font-size-2x { font-size: 2.0em; }
    .font-size-150ps { font-size: 150%; }
    .font-size-large { font-size: large; }
  </style>
</head>
<body>
  <p>default font size: 16px</p>
  <p class='font-size-40'>font-size: 40px</p>
  <p class='font-size-2x'>font-size: 2.0em</p>
  <p class='font-size-150ps'>font-size: 150%</p>
  <p class='font-size-large'>font-size: large</p>
</body>
</html>
```

- result

  ![font-size.png](https://prod-files-secure.s3.us-west-2.amazonaws.com/510cd684-c9a0-45bd-b45d-b35ad6027628/4f0c47d9-ca28-47fb-9006-3117ea165e36/font-size.png)

## 2. font-family 프로퍼티

- 폰트를 지정함. ( 컴퓨터에 해당 폰트가 설치되어 있지 않으면 적용X)
- 폰트는 여러 개를 동시에 지정 가능.
- 첫 번째 지정한 폰트가 클라이언트 컴퓨터에 설치되어 있지 않은 경우 다음에 지정된 폰트를 적용함.

```html
<!DOCTYPE html>
<html>
<head>
  <style>
    .serif {
      font-family: "Times New Roman", Times, serif;
    }

    .sans-serif {
      font-family: Arial, Helvetica, sans-serif;
    }

    .monospace {
      font-family: "Courier New", Courier, monospace;
    }
  </style>
</head>
<body>
  <h1>font-family</h1>
  <p class="serif">Times New Roman font.</p>
  <p class="sans-serif">Arial font.</p>
  <p class="monospace">Courier New font.</p>
</body>
</html>
```

- result

  ![font-family.png](https://prod-files-secure.s3.us-west-2.amazonaws.com/510cd684-c9a0-45bd-b45d-b35ad6027628/f06709a1-f2ba-469e-93cd-3949631376bf/font-family.png)

## 3. font-style / font-weight 프로퍼티

- font-style 프로퍼티는 이탤릭체의 지정, font-weight 프로퍼티는 폰트 굵기 지정에 사용됨.

```html
<!DOCTYPE html>
<html>
<head>
  <style>
    p { font-size: 2.0em; }

    /*
      font-style
      normal / italic / oblique
    */
    .italic {
      font-style: italic;
    }

    /*
      font-weight
      100 ~ 900 or normal / bold / lighter / bolder
    */
    .light {
      font-weight: lighter;
    }
    .thick {
      font-weight: bold;
    }
    .thicker {
      font-weight: 900;
    }
  </style>
</head>
<body>
  <p>normal style.</p>
  <p class="italic">font-style: italic</p>

  <p class="light">font-weight: lighter</p>
  <p class="thick">font-weight: bold</p>
  <p class="thicker">font-weight: 900</p>
</body>
</html>
```

- result

  ![font-style font-weight.png](https://prod-files-secure.s3.us-west-2.amazonaws.com/510cd684-c9a0-45bd-b45d-b35ad6027628/8fecfe04-02f2-48e4-bfba-96b2aea9df2a/font-style_font-weight.png)

## 4. font Shorthand

Shortgand Syntax

```css
CODE
font : font-style(optional) font-variant(optional) font-weight(optional) 
font-size(mandatory) line-height(optional) font-family(mandatory)
/* size | family */
font: 2em "Open Sans", serif;

/* style | size | family */
font: italic 2em "Open Sans", sans-serif;

/* style | variant | weight | size/line-height | family */
font: italic small-caps bolder 16px/1.2 monospace;

/* style | variant | weight | size/line-height | family */
/* font-variant: small-caps; 소문자를 대문자로 만든다. 단 크기는 일반 대문자에 비해 더 작다.*/
font: italic small-caps bolder 16px/3 cursive;
```

## 5. line-height 프로퍼티

- 텍스트의 높이를 지정함.

```html
<!DOCTYPE html>
<html>
<head>
  <style>
    .small {
      line-height: 70%; /* 16px * 70% */
    }
    .big {
      line-height: 1.2; /* 16px * 1.2 */
    }
    .lh-3x {
      line-height: 3.0; /* 16px * 3 */
    }

  </style>
</head>
<body>
  <p>
    default line-height.<br>
    default line-height.<br>
    대부분 브라우저의 default line height는 약 110% ~ 120%.<br>
  </p>

  <p class="small">
    line-height: 70%<br>
    line-height: 70%<br>
  </p>

  <p class="big">
    line-height: 1.2<br>
    line-height: 1.2<br>
  </p>

  <p class="lh-3x">
    line-height: 3.0<br>
    line-height: 3.0<br>
  </p>
</body>
</html>
```

- result

  ![line height 프롶터ㅣ.png](https://prod-files-secure.s3.us-west-2.amazonaws.com/510cd684-c9a0-45bd-b45d-b35ad6027628/e3bff695-a345-4383-8370-80d04434b375/line_height_%ED%94%84%EB%A1%B6%ED%84%B0%E3%85%A3.png)

## 6. letter-spacing 프로퍼티

- 글자 사이의 간격을 지정함.

```html
<!DOCTYPE html>
<html>
<head>
  <style>
    .loose {
      letter-spacing: 2px;
    }
    .tight {
      letter-spacing: -1px;
    }
  </style>
</head>
<body>
  <p>Lorem ipsum dolor sit amet, consectetur adipisicing elit</p>

  <p class="loose">Lorem ipsum dolor sit amet, consectetur adipisicing elit</p>

  <p class="tight">Lorem ipsum dolor sit amet, consectetur adipisicing elit</p>
</body>
</html>
```

- result

  ![letter-spacing.png](https://prod-files-secure.s3.us-west-2.amazonaws.com/510cd684-c9a0-45bd-b45d-b35ad6027628/873c460d-97f3-45a4-bfc9-5235e69f227f/letter-spacing.png)

## 7. text-align 프로퍼티

- 텍스트의 수평 정령을 정의함.

```html
<!DOCTYPE html>
<html>
<head>
  <style>
    h1 { text-align: center; }
    h3 { text-align: right; }
    p.left  { text-align: left; }
    p.justify  { text-align: justify; }
    a  { text-align: center; }
  </style>
</head>
<body>
  <h1>Lorem ipsum</h1>
  <h3>2016.03.07</h3>

  <p class="left">Lorem ipsum dolor sit amet, consectetur adipisicing elit, sed do eiusmod tempor incididunt ut labore et dolore magna aliqua. Ut enim ad minim veniam, quis nostrud exercitation ullamco laboris nisi ut aliquip ex ea commodo consequat. Duis aute irure dolor in reprehenderit in voluptate velit esse cillum dolore eu fugiat nulla pariatur. Excepteur sint occaecat cupidatat non proident, sunt in culpa qui officia deserunt mollit anim id est laborum.</p>

  <p class="justify">Lorem ipsum dolor sit amet, consectetur adipisicing elit, sed do eiusmod tempor incididunt ut labore et dolore magna aliqua. Ut enim ad minim veniam, quis nostrud exercitation ullamco laboris nisi ut aliquip ex ea commodo consequat. Duis aute irure dolor in reprehenderit in voluptate velit esse cillum dolore eu fugiat nulla pariatur. Excepteur sint occaecat cupidatat non proident, sunt in culpa qui officia deserunt mollit anim id est laborum.</p>

  <a href='#'>Reference</a>
</body>
</html>
```

- result

  ![align.png](https://prod-files-secure.s3.us-west-2.amazonaws.com/510cd684-c9a0-45bd-b45d-b35ad6027628/a28c3122-c71a-4912-b6bf-d0721e9f7df5/align.png)

## 8. text-decoration 프로퍼티

- text-decration 프로퍼티를 사용하여 링크 underline을 제고할 수 있음. (또는 텍스트에 underline, overline, line-through를 추가할 수도 있음.)

```html
<!DOCTYPE html>
<html>
<head>
  <style>
    a { text-decoration: none; }

    p:nth-of-type(1) { text-decoration: overline; }
    p:nth-of-type(2) { text-decoration: line-through; }
    p:nth-of-type(3) { text-decoration: underline; }
  </style>
</head>
<body>
  <a href='#'>text-decoration: none</a>

  <p>text-decoration: overline</p>
  <p>text-decoration: line-through</p>
  <p>text-decoration: underline</p>
</body>
</html>
```

- result

  ![text-decoration.png](https://prod-files-secure.s3.us-west-2.amazonaws.com/510cd684-c9a0-45bd-b45d-b35ad6027628/e28c2e8b-0993-40c7-bde5-92c80e882bd6/text-decoration.png)

## 9.white-space 프로퍼티

- white space는 공백, 들여쓰기, 줄바꿈을 의미함.
- white-space 프로퍼티는 기본 동작을 제어하기 위한 프로퍼티임.

| 프로퍼티값 | line break | space/tab   | wrapping(자동줄바꿈) |
| ---------- | ---------- | ----------- | -------------------- |
| normal     | 무시       | 1번만 반영  | O                    |
| nowrap     | 무시       | 1번만 반영  | X                    |
| pre        | 반영       | 그대로 반영 | X                    |
| pre-wrap   | 반영       | 그대로 반영 | O                    |
| pre-line   | 반영       | 1번만 반영  | O                    |

## 10. text-overflow 프로퍼티

- 부모 영역을 벗어난 wrapping(자동줄바꿈)이 되지 않은 텍스트의 처리 방법을 정의함.
  - 사용하기 위한 조건
    - width 프로퍼티가 지정되어 있어야함.
    - 자동 줄바꿈을 방지하려면 white-space 프로퍼티를 nowrap으로 설정함.
    - overflow 프로퍼티에 반드시 “visible” 이외의 값이 지정되어 있어야 함.

```css
/* 부모 영역을 벗어난 텍스트를 잘라내어 보이지 않게 하고 말줄임표(...)를 표시한다. */
.truncate {
  width: 150px;             /* width가 지정되어 있어야 한다. */
  white-space: nowrap;      /* 자동 줄바꿈을 방지 */
  overflow: hidden;         /* 반드시 "visible" 이외의 값이 지정되어 있어야 한다. */
  text-overflow: ellipsis;  /* ellipsis or clip */
}
```

- text-overflow 프로퍼티에 설정할 수 있는 프로퍼티 값

| 프로퍼티값 | Description                                                  |                                                              |
| ---------- | ------------------------------------------------------------ | ------------------------------------------------------------ |
| clip       | 영역을 벗어난 텍스트를 표시하지 않는다. (기본값)             |                                                              |
| ellipsis   | 영역을 벗어난 텍스트를 잘라내어 보이지 않게 하고 말줄임표(…)를 표시한다. |                                                              |
| <!–        | <string>                                                     | 프로퍼티 값으로 지정한 임의의 문자열을 출력한다. Firefox(9.0~)만 지원하는 기능이다. –> |

## 11. word-wrap 프로퍼티

- 한 단어의 길이가 길어서 부모 영역을 벗어난 텍스트의 처리 방법을 정의함.

```css
<!DOCTYPE html>
<html>
<head>
  <meta charset="utf-8">
  <style>
    div {
      width: 150px;
      height: 150px;
      padding: 10px;
      margin: 40px;
      border-radius: 6px;
      border-color: gray;
      border-style: dotted;
    }
    .word-wrap { word-wrap: break-word; }
  </style>
</head>
<body>
  <h1>word-wrap</h1>
  <div>
    Floccinaucinihilipilification <https://poiemaweb.com/css3-font-text>
  </div>
  <div class="word-wrap">
    Floccinaucinihilipilification <https://poiemaweb.com/css3-font-text>
  </div>
</body>
</html>
```

- result

  ![word-wrap.png](https://prod-files-secure.s3.us-west-2.amazonaws.com/510cd684-c9a0-45bd-b45d-b35ad6027628/2dd918fb-fde6-46ad-bca3-ff4efb5f076d/word-wrap.png)

## 12. word-break 프로퍼티

- 한 단어의 길이가 길어서 부모 영역을 벗어난 텍스트의 처리 방법을 정의함.
- word-wrap 프로퍼티는 단어를 어느 정도는 고려하여 개행하지만 word-break: break-all; 은 단어를 고려하지 않고 부모 영역에 맞추어 강제 개행함.

```css
<!DOCTYPE html>
<html>
<head>
  <meta charset="utf-8">
  <style>
    div {
      width: 150px;
      height: 150px;
      padding: 10px;
      margin: 40px;
      border-radius: 6px;
      border-color: gray;
      border-style: dotted;
    }
    .word-wrap  { word-wrap: break-word; }
    .word-break { word-break: break-all; }
  </style>
</head>
<body>
  <div>
    Floccinaucinihilipilification <https://poiemaweb.com/css3-font-text>
  </div>

  <h1>word-wrap</h1>
  <div class="word-wrap">
    Floccinaucinihilipilification <https://poiemaweb.com/css3-font-text>
  </div>

  <h1>word-break</h1>
  <div class="word-break">
    Floccinaucinihilipilification <https://poiemaweb.com/css3-font-text>
  </div>
</body>
</html>
```

- result

![word-break.png](https://prod-files-secure.s3.us-west-2.amazonaws.com/510cd684-c9a0-45bd-b45d-b35ad6027628/d6210f1d-9b0d-4c54-a3fc-f439bbf8c6b1/word-break.png)