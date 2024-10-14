# CSS3 Shadow

## 1. text-shadow

- 텍스트에 그림자 효과를 부여하는 프로퍼티

```html
CODE
선택자 { text-shadow: Horizontal-offset Vertical-offset Blur-Radius Shadow-Color; }
```

| 프로퍼티 값       | 단위  | 설명                                                         | 생략 |
| ----------------- | ----- | ------------------------------------------------------------ | ---- |
| Horizontal-offset | px    | 그림자를 텍스트의 오른쪽으로 지정값만큼 이동시킨다           |      |
| Vertical-offset   | px    | 그림자를 텍스트의 아래로 지정값만큼 이동시킨다               |      |
| Blur-Radius       | px    | 그림자의 흐림정도를 지정한다. 지정값만큼 그림자가 커지고 흐려진다. (양수) | 가능 |
| Shadow-Color      | color | 그림자의 색상을 지정한다                                     | 가능 |

```html
<!DOCTYPE html>
<html>
<head>
  <style>
    h1:nth-child(1) {
      text-shadow: 5px 5px;
    }
    h1:nth-child(2) {
      text-shadow: 5px 5px red;
    }
    h1:nth-child(3) {
      text-shadow: 5px 5px 3px red;
    }
    h1:nth-child(4) {
      color: white;
      text-shadow: 5px 5px 3px black;
    }
    h1:nth-child(5) {
      text-shadow: 0 0 3px red;
    }
    /*Multiple Shadows*/
    h1:nth-child(6) {
      text-shadow: 0 0 3px red, 0 0 10px blue;
    }
    /*Multiple Shadows*/
    h1:nth-child(7) {
      color: white;
      text-shadow: 1px 1px 2px black, 0 0 25px blue, 0 0 5px darkblue;
    }
  </style>
</head>
<body>
  <h1>Text-shadow effect!</h1>
  <h1>Text-shadow effect!</h1>
  <h1>Text-shadow effect!</h1>
  <h1>Text-shadow effect!</h1>
  <h1>Text-shadow effect!</h1>
  <h1>Text-shadow effect!</h1>
  <h1>Text-shadow effect!</h1>
</body>
</html>
```

- result

  ![text-shadow.png](https://prod-files-secure.s3.us-west-2.amazonaws.com/510cd684-c9a0-45bd-b45d-b35ad6027628/01b6badc-001a-4a80-94fd-7e784749b2e4/text-shadow.png)

| Property    | Chrome | Edge | IE   | Firefox | Safari | Opera |
| ----------- | ------ | ---- | ---- | ------- | ------ | ----- |
| text-shadow | 4.0    | 12.0 | 10.0 | 3.5     | 4.0    | 9.5   |

## 2. box-shadow

- 요소에 그림자 효과를 부여하는 프로퍼티

```html
CODE선택자 { box-shadow: Inset Horizontal-offset Vertical-offset Blur-Radius Spread Shadow-Color; }
```

| 프로퍼티 값       | 단위  | 설명                                                         | 생략 |
| ----------------- | ----- | ------------------------------------------------------------ | ---- |
| Inset             | inset | inset 키워드를 지정하면 그림자가 요소 안쪽에 위치한다.       | 가능 |
| Horizontal-offset | px    | 그림자를 텍스트의 오른쪽으로 지정값만큼 이동시킨다           |      |
| Vertical-offset   | px    | 그림자를 텍스트의 아래로 지정값만큼 이동시킨다               |      |
| Blur-Radius       | px    | 그림자의 흐림정도를 지정한다. 지정값만큼 그림자가 커지고 흐려진다. (양수) | 가능 |
| Spread            | px    | 그림자를 더 크게 확장시킨다. (음수, 양수)                    | 가능 |
| Shadow-Color      | color | 그림자의 색상을 지정한다                                     | 가능 |

```html
<!DOCTYPE html>
<html>
<head>
  <style>
    div {
      width: 300px;
      height: 100px;
      padding: 15px;
      margin: 20px;
      background-color: yellow;
    }
    /*box-shadow: Inset Horizontal-offset Vertical-offset Blur-Radius Spread Shadow-Color;*/
    /* Horizontal-offset Vertical-offset */
    div:nth-of-type(1) {
      box-shadow: 10px 10px;
    }
    /* Horizontal-offset Vertical-offset Shadow-Color */
    div:nth-of-type(2) {
      box-shadow: 10px 10px blue;
    }
    /* Horizontal-offset Vertical-offset Blur-Radius Shadow-Color */
    div:nth-of-type(3) {
      box-shadow: 10px 10px 5px blue;
    }
    /* Horizontal-offset Vertical-offset Blur-Radius Spread Shadow-Color */
    div:nth-of-type(4) {
      box-shadow: 10px 10px 5px 5px blue;
    }
    /* Inset Horizontal-offset Vertical-offset Blur-Radius Spread Shadow-Color */
    div:nth-of-type(5) {
      box-shadow: inset 10px 10px 5px 5px blue;
    }
    /* Horizontal-offset Vertical-offset Blur-Radius Spread Shadow-Color */
    div:nth-of-type(6) {
      background-color: white;
      box-shadow: 0 4px 8px 0 rgba(0, 0, 0, 0.2), 0 6px 20px 0 rgba(0, 0, 0, 0.19);
    }
  </style>
</head>
<body>
  <div>This is a div element with a box-shadow</div>
  <div>This is a div element with a box-shadow</div>
  <div>This is a div element with a box-shadow</div>
  <div>This is a div element with a box-shadow</div>
  <div>This is a div element with a box-shadow</div>
  <div>This is a div element with a box-shadow</div>
</body>
</html>
```

- result

  ![box-shadow.png](https://prod-files-secure.s3.us-west-2.amazonaws.com/510cd684-c9a0-45bd-b45d-b35ad6027628/dec0c723-00b5-4b53-b87d-bdf2fff3e81a/box-shadow.png)

  | Property   | Chrome | Edge | IE   | Firefox | Safari | Opera |
  | ---------- | ------ | ---- | ---- | ------- | ------ | ----- |
  | box-shadow | 10.0   | 12.0 | 9.0  | 4.0     | 5.1    | 10.5  |
  | prefix     | 4.0    |      |      | 3.5     | 3.1    |       |