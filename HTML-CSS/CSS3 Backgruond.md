# CSS3 Backgruond

- background 관련 프로퍼티는 해당 요소의 배경으로 이미지 또는 색상을 정의함.

## 1. background-image 프로퍼티

- 요소에 배경 이미지를 지정함.

```html
<!DOCTYPE html>
<html>
<head>
  <style>
    body {
      background-image: url("<http://poiemaweb.com/img/bg/dot.png>");
    }
  </style>
</head>
<body>
  <h3>Background Image</h3>
</body>
</html>
```

- result

  ![backgorund image 프로퍼티.png](https://prod-files-secure.s3.us-west-2.amazonaws.com/510cd684-c9a0-45bd-b45d-b35ad6027628/745db2c6-8a0a-43f3-8ede-f7ad3422160e/backgorund_image_%ED%94%84%EB%A1%9C%ED%8D%BC%ED%8B%B0.png)

## 2. background-repeat 프로퍼티

- 배경 이미지의 반복을 지정함. (수직, 수평 또는 수직과 수평 모두의 반복을 지정할 수 있음.)
- 만약 설정된 이미지의 크기가 화면보다 작으면 자동으로 이미지가 반복 출력되어 화면을 채우게 됨.
- x축으로만 배경 이미지를 반복할 경우, background-repeat 프로퍼티값에 repeat-x, y축으로만 배경 이미지를 반복할 경우, background-repeat 프로퍼티값에 repeat-y를 설정함.

```html
<!DOCTYPE html>
<html>
<head>
  <style>
    body {
      background-image: url("<http://poiemaweb.com/img/bg/dot.png>");
      background-repeat: repeat-x;
    }
  </style>
</head>
<body>
  <h3>background-repeat: repeat-x;</h3>
</body>
</html>
```

- result

  ![backgroun-repeat.png](https://prod-files-secure.s3.us-west-2.amazonaws.com/510cd684-c9a0-45bd-b45d-b35ad6027628/a6596402-e1cd-4343-bcb5-830fc3e61dee/backgroun-repeat.png)

- 반복 출력을 멈추고 싶은 경우, background-repeat 프로퍼티값에 no-repeat 을 설정하면 됨.

- background-img에 복수개의 이미지를 설정할 경우, 먼저 설정된 이미지가 전면에 출력됨.

```html
<!DOCTYPE html>
<html>
<head>
  <style>
    body {
      background-image: url("<http://poiemaweb.com/img/bg/dot.png>"), url("<http://poiemaweb.com/img/bg/paper.gif>");
      background-repeat: no-repeat, repeat;
    }
  </style>
</head>
<body>
  <h3>background-repeat: no-repeat, repeat;</h3>
</body>
</html>
```

- result

  ![백그라운드 반복 전면 프로퍼티.png](https://prod-files-secure.s3.us-west-2.amazonaws.com/510cd684-c9a0-45bd-b45d-b35ad6027628/93401ca4-007c-42e9-9d67-36de4d24e550/%EB%B0%B1%EA%B7%B8%EB%9D%BC%EC%9A%B4%EB%93%9C_%EB%B0%98%EB%B3%B5_%EC%A0%84%EB%A9%B4_%ED%94%84%EB%A1%9C%ED%8D%BC%ED%8B%B0.png)

## 3. background-size 프로퍼티

- 배경 이미지의 사이즈를 지정함.
- 프로퍼티값은 px, %, cover, contain 등을 사용함.
- 배경이미지의 width, height를 모두 설정할 수 있음. 이때 첫번째 값은 width, 두번째 값은 height를 의미함.
- 만약 하나의 값만을 지정한 경우, 지정한 값은 width를 의미하게 되며 height는 auto로 지정됨.
- px값 지정
  - 배경이미지 크기가 지정된 px값 그대로 설정됨.
  - 첫 번째 값은 width, 두 번째 값은 height를 의미.

```css
.bg {
  background-size: 700px 500px;
}
```

- %값 지정
  - 배경이미지 크기가 지정된 %값에 비례하여 설정됨.
  - 화면을 줄이거나 늘리면 배경이미지의 크기도 따라서 변경되어 찌그러지는 현성이 나타남.

```css
.bg {
  background-size: 100% 100%;
}
```

- cover 지정
  - 배경이미지의 크기 비율을 유지한 상태에서 부모 요소의 width, height 중 큰값에 배경이미지를 맞춤.

```css
.bg {
  background-size: cover;
}
```

- contain 지정
- 배경이미지의 크기 비율을 유지한 상태에서 부모 요소의 영역에 배경이미지가 보이지 않는 부분없이 전체가 들어갈 수 있도록 이미지 스케일을 조정함.

```css
.bg {
  background-size: contain;
}
```

- width, height의 프로퍼티값은 공백으로 구분.

```css
body {
  background-image: url("front.png"), url("back.png");
  background-repeat: no-repeat, no-repeat;
  background-size: 100%, 500px;
}
```

## 4. backgruond-attachment 프로퍼티

- 화면이 스크롤되더라도 배경이미지는 스크롤되지 않고 고정되어 있게 하려면 background-attachment 프로퍼티에 fixed 키워드를 지정함.

## 5. background-position 프로퍼티

- backgruond-position 프로퍼티를 사용하면 이미지의 좌표(xpos, ypos)를 지정할 수 있음.
- 기본값은 background-position: 0% 0%; 로 배경이미지는 우측 상단에 위치하게 됨.

## 6. background-color 프로퍼티

- background-color 프로퍼티는 요소의 배경 색상을 지정함.(색상값 또는 transparent 키워드를 지정할 수 있음.)

```css
.bg-col-white {
  background-color: rgb(255, 255, 255);
}

.bg-col-red {
  background-color: red;
}
```

## 7.background Shorthand

- background-color, background-image, background-repeat, background-position를 한번에 정의하기 위한 Shorthand Syntax임.