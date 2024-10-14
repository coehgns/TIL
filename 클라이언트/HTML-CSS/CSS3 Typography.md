# CSS3 Typography

- 컨테이너 요소로 img 요소를 래핑하면 img 요소 아래에 의도하지 않은 여분의 공간이 패딩됨.

```css
<!DOCTYPE html>
<html>
<head>
  <style>
    .container {
      width: 350px;
      border: 1px solid red;
    }
  </style>
</head>
<body>
  <div class="container">
    <img src="<http://via.placeholder.com/350x150/f5ab3d/fff>">
  </div>
</body>
</html>
```

![typo.png](https://prod-files-secure.s3.us-west-2.amazonaws.com/510cd684-c9a0-45bd-b45d-b35ad6027628/90c78c34-6ea9-4fca-8461-cd03421449c4/typo.png)

- image 요소는 inline 요소이며 텍스트로 취급되는데 image 요소 또한 위 그림과 같이 타이포그래피를 따른다는 것을 의미.
- image 요소를 블록 요소로 전환하면 더 이상 텍스트로 취급되지 않음.

```css
<!DOCTYPE html>
<html>
<head>
  <style>
    .container {
      width: 350px;
      border: 1px solid red;
    }

    img {
      display: block;
    }
  </style>
</head>
<body>
  <div class="container">
    <img src="<http://via.placeholder.com/350x150/f5ab3d/fff>">
  </div>
</body>
</html>
```

- result

  ![typography.png](https://prod-files-secure.s3.us-west-2.amazonaws.com/510cd684-c9a0-45bd-b45d-b35ad6027628/b923b65b-faae-484b-84dd-0d7ee569240d/typography.png)

  - 이 방법은 image 요소를 블록 요소로 전환할 수 없는 레이아웃에서는 사용할 수 없음.

- inline 요소에 사용할 수 있는 vertical-align 프로퍼티를 사용하는 방법

- vertical-align 프로퍼티의 기본값은 baseline인데 이를 변경하여 이미지 표시 위치를 조정하는 것.

```css
<!DOCTYPE html>
<html>
<head>
  <style>
    .container {
      width: 350px;
      border: 1px solid red;
    }

    img {
      vertical-align: bottom;
    }
  </style>
</head>
<body>
  <div class="container">
    <img src="<http://via.placeholder.com/350x150/f5ab3d/fff>">
  </div>
</body>
</html>
```

- result

  ![typography.png](https://prod-files-secure.s3.us-west-2.amazonaws.com/510cd684-c9a0-45bd-b45d-b35ad6027628/68de09fd-3142-4a38-965a-cfdea9727e9a/typography.png)