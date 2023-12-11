# CSS3 Float

- float 프로퍼티는 주로 레이아웃을 구성할 때 블록 레벨 요소를 가로 정렬하기 위해 사용되는 중요한 기법임.
- flexbox 레이아웃을 사용하면 더욱 간단하게 정렬을 구현할 수 있음.
- float 프로퍼티는 해당 요소를 다음ㅇ ㅛ소 위에 떠 있게 함.
- 떠 있다는 의미는 요소가 기본 레이아웃 흐름에서 벗어나 요소의 모서리가 페이지의 왼쪽이나 오른쪽에 이동하는 것.
- float 프로퍼티를 사용할 때 요소의 위치를 고정시키는 position 프로퍼티의 absolute를 사용하면 안됨.

| 프로퍼티값 | Description                          |
| ---------- | ------------------------------------ |
| none       | 요소를 떠 있게 하지 않는다. (기본값) |
| right      | 요소를 오른쪽으로 이동시킨다         |
| left       | 요소를 왼쪽으로 이동시킨다.          |

![float.png](https://prod-files-secure.s3.us-west-2.amazonaws.com/510cd684-c9a0-45bd-b45d-b35ad6027628/b22a7c4c-70d2-4630-aed2-036717682bdd/float.png)

## 1. 정렬

- float 프로퍼티를 사용하지 않은 블록 요소들이 수직으로 정렬됨.
- float:left; 프로퍼티를 사용하면 왼쪽부터 가로 정렬되고, float:right; 프로퍼티를 사용하면 오른쪽 부터 가로 정렬됨.

```css
<!DOCTYPE html>
<html>
<head>
  <style>
    .box {
      color: white;
      font-weight: bold;
      font-size: 50px;
      border-radius: 6px;
      width: 100px;
      height: 100px;
      margin: 10px;
      padding: 10px;
    }
    .d1, .d2 {
      float: left;
    }
    .d1 {
      background: red;
    }
    .d2 {
      background: orange;
    }
    .d3, .d4 {
      float: right;
    }
    .d3 {
      background: red;
    }
    .d4 {
      background: orange;
    }
  </style>
</head>
<body>
  <div class="container">
    <div class="box d1"> 1 </div>
    <div class="box d2"> 2 </div>
    <div class="box d3"> 3 </div>
    <div class="box d4"> 4 </div>
  </div>
</body>
</html>
```

- result

  ![left right float.png](https://prod-files-secure.s3.us-west-2.amazonaws.com/510cd684-c9a0-45bd-b45d-b35ad6027628/3b7eb148-2c6d-49a9-8adb-198cc0ec257b/left_right_float.png)

- float 프로퍼티는 좌, 우 가로 정렬만 가능함. 중앙 가로 정렬은 margin 프로퍼티를 사용해야 함.

```css
div {
  width: 960px;
  margin: 0 auto;
}
```

## 2. width

- width 프로퍼티의 기본값은 100%이므로 width 프로퍼티값을 지정하지 않은 block 요소는 부모 요소의 가로폭을 가득 채움.

```css
<!DOCTYPE html>
<html>
<head>
  <style>
    .box {
      color: white;
      font-weight: bold;
      font-size: 30px;
      line-height: 50px;
      height: 50px;
      margin: 0 10px;
      padding: 10px;
    }
    .d1 {
      background: red;
    }
    .d2 {
      background: orange;
    }
  </style>
</head>
<body>
  <div class="box d1"> div </div>
  <div class="box d2"> div </div>
</body>
</html>
```

- result

  ![width 기본값.png](https://prod-files-secure.s3.us-west-2.amazonaws.com/510cd684-c9a0-45bd-b45d-b35ad6027628/d5cdde5a-6147-4d0c-9034-34958ea59445/width_%EA%B8%B0%EB%B3%B8%EA%B0%92.png)

- width 프로퍼티를 선언하지 않은 block 레벨 요소에 float 프로퍼티가 선언되면 width가 inline 요소와 같이 content에 맞게 최소화되고 다음 요소 위에 떠 있게 됨.

```css
<!DOCTYPE html>
<html>
<head>
  <style>
    .box {
      color: white;
      font-weight: bold;
      font-size: 30px;
      line-height: 50px;
      height: 50px;
      margin: 0 10px;
      padding: 10px;
    }
    .d1 {
      float: left;
      background: red;
    }
    .d2 {
      background: orange;
    }
  </style>
</head>
<body>
  <div class="box d1"> float: left; </div>
  <div class="box d2"> div </div>
</body>
</html>
```

- result

  ![width 값에 float.png](https://prod-files-secure.s3.us-west-2.amazonaws.com/510cd684-c9a0-45bd-b45d-b35ad6027628/79e951c5-f44b-4931-aada-8d8b186a9638/width_%EA%B0%92%EC%97%90_float.png)

## 3. float 프로퍼티 관련 문제 해결 방법

### 3.1 float 프로퍼티가 선언된 요소와 float 프로퍼티가 선언되지 않은 요소간 margin이 사라지는 문제

- 위 예제는 float 프로퍼티가 선언된 요소가 다음 요소 위에 떠 있는 상태임. 두 요소간의 margin은 제대로 표현되지 않음.
- float 프로퍼티를 선언하지 않은 요소(.d2)에 overflow: hidden 프로퍼티를 선언하면 문제가 해결 됨.
- overflow: hidden 프로퍼티는 자식 요소가 부모 요소의 영역보다 클 경우 넘치는 부분을 안보이게 해주는 역할을 하는데 여기서는 float 프로퍼티가 없어서 제대로 표현되지 못하는 요소를 제대로 출력해줌.

```css
<!DOCTYPE html>
<html>
<head>
  <style>
    .box {
      color: white;
      font-weight: bold;
      font-size: 30px;
      line-height: 50px;
      height: 50px;
      margin: 0 10px;
      padding: 10px;
    }
    .d1 {
      float: left;
      background: red;
    }
    .d2 {
      overflow: hidden;
      background: orange;
    }
  </style>
</head>
<body>
  <div class="box d1"> float: left; </div>
  <div class="box d2"> div </div>
</body>
</html>
```

- result

![overflow hidden.png](https://prod-files-secure.s3.us-west-2.amazonaws.com/510cd684-c9a0-45bd-b45d-b35ad6027628/168e02f1-d7a8-4bc7-af1f-a9758e33ced9/overflow_hidden.png)