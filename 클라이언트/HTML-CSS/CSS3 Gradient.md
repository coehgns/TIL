# CSS3 Gradient

- 그레이디언트는 2가지 이상의 색상을 혼합하여 부드러운 색감의 배경 등을 생성하는 것.
- 그레이디언트의 종류
  - 선형 그레디언트
  - 방사형 그레이디언트

```html
<!DOCTYPE html>
<html>
<head>
  <style>
    body {
      margin: 0;
    }
    div {
      width: 100vw;
      height: 100vh;
    }
    .dawn {
      /* Old browsers */
      background: #b3cae5;
      /* FF3.6+ */
      background: -moz-linear-gradient(-45deg, #b3cae5 12%, #dbdde4 46%, #e4e3e4 70%, #f7ddbb 94%, #efcab2 100%);
      /* Chrome,Safari4+ */
      background: -webkit-gradient(linear, left top, right bottom, color-stop(12%, #b3cae5), color-stop(46%, #dbdde4), color-stop(70%, #e4e3e4), color-stop(94%, #f7ddbb), color-stop(100%, #efcab2));
      /* Chrome10+,Safari5.1+ */
      background: -webkit-linear-gradient(-45deg, #b3cae5 12%, #dbdde4 46%, #e4e3e4 70%, #f7ddbb 94%, #efcab2 100%);
      /* Opera 11.10+ */
      background: -o-linear-gradient(-45deg, #b3cae5 12%, #dbdde4 46%, #e4e3e4 70%, #f7ddbb 94%, #efcab2 100%);
      /* IE10+ */
      background: -ms-linear-gradient(-45deg, #b3cae5 12%, #dbdde4 46%, #e4e3e4 70%, #f7ddbb 94%, #efcab2 100%);
      /* W3C */
      background: linear-gradient(135deg, #b3cae5 12%, #dbdde4 46%, #e4e3e4 70%, #f7ddbb 94%, #efcab2 100%);
    }
  </style>
</head>
<body>
  <div class="dawn"></div>
</body>
</html>
```

- result

![gradient.png](https://prod-files-secure.s3.us-west-2.amazonaws.com/510cd684-c9a0-45bd-b45d-b35ad6027628/b1443e06-30bf-45b5-9796-9cccb84ae23c/gradient.png)

| Property        | Chrome | Edge | IE   | Firefox | Safari | Opera |
| --------------- | ------ | ---- | ---- | ------- | ------ | ----- |
| linear-gradient | 26.0   | 12.0 | 10.0 | 16.0    | 6.1    | 12.1  |
| prefix          | 10.0   |      |      | 3.6     | 5.1    | 11.1  |

| Property        | Chrome | Edge | IE   | Firefox | Safari | Opera |
| --------------- | ------ | ---- | ---- | ------- | ------ | ----- |
| radial-gradient | 26.0   | 12.0 | 10.0 | 16.0    | 6.1    | 12.1  |
| prefix          | 10.0   |      |      | 3.6     | 5.1    | 11.1  |

| Property                  | Chrome | Edge | IE   | Firefox | Safari | Opera |
| ------------------------- | ------ | ---- | ---- | ------- | ------ | ----- |
| repeating-linear-gradient | 26.0   | 12.0 | 10.0 | 16.0    | 6.1    | 12.1  |
| prefix                    | 10.0   |      |      | 3.6     | 5.1    | 11.1  |

| Property                  | Chrome | Edge | IE   | Firefox | Safari | Opera |
| ------------------------- | ------ | ---- | ---- | ------- | ------ | ----- |
| repeating-radial-gradient | 26.0   | 12.0 | 10.0 | 16.0    | 6.1    | 12.1  |
| prefix                    | 10.0   |      |      | 3.6     | 5.1    | 11.1  |