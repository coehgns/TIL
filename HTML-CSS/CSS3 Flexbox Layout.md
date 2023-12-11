## 1. Introduction

- Flexbox는 모던 웹을 위하여 제안된 기존 layout 보다 더 세련된 방식의 니즈에 부합하기 위한 CSS3의 새로운 layout 방식임.
- 복잡한 레이아웃이라도 적은 코드로 보다 간단하게 표현할 수 있음.

```html
<!DOCTYPE html>
<html>
<head>
  <meta charset="UTF-8">
  <title>Flexbox Layout Example</title>
  <style>
    .flex-container {
      margin: 10px;
      padding: 15px;
      border-radius: 5px;
      background: #60B99A;
    }

    .flex-item {
      margin: 10px;
      padding: 20px;
      color: #fff;
      text-align: center;
      border-radius: 5px;
      background: #4584b1;
    }
  </style>
</head>
<body>
  <div class="flex-container">
    <div class="flex-item">1</div>
    <div class="flex-item">2</div>
    <div class="flex-item">3</div>
    <div class="flex-item">4</div>
    <div class="flex-item">5</div>
  </div>
</body>
</html>
```

- result

  ![flexbox.png](https://prod-files-secure.s3.us-west-2.amazonaws.com/510cd684-c9a0-45bd-b45d-b35ad6027628/b1f031ae-ba74-4388-8357-ed0b7ecf701e/flexbox.png)

  - div 요소는 block 요소이므로 수직 정렬됨.(수평 정렬하려면 자식요소를 inline-block으로 지정하거나 float 프로퍼티를 지정함.)

```css
.flex-item {
  display: inline-block;
  /* or */
  float: left;
}
```

- Flexbox의 장점
  - 1줄의 코드 추가로 수평 정렬이 가능함.
  - 요소의 상하좌우 정렬, 순서 변경이 간단함.
  - 요소가 간격 조절이 간단함.
  - 서로 다른 height를 갖는 요소의 수평정렬 시, 간단히 상하중앙 정렬이 가능함.

## 2. Usage

- Flexbox 레이아웃은 flex item이라 불리는 복수의 자식 요소와 이들을 내포하는 flex-container 부모 요소로 구성됨.

  ![CSS3-Flexbox-Model.jpg](https://prod-files-secure.s3.us-west-2.amazonaws.com/510cd684-c9a0-45bd-b45d-b35ad6027628/3b9ba50a-26f5-49da-b9e1-97c67b1e1286/CSS3-Flexbox-Model.jpg)

- flexbox를 사용하기 위해선 HTML 부모 요소인 display 속성에 flex를 지정함.

```css
.flex-container {
  display: flex;
}
```

- 부모 요소가 inline 요소인 경우 inline-flex를 지정함.

```css
.flex-container {
  display: inline-flex;
}
```

- flex 또는 inline-flex는 부모 요소에 반드시 지정해야하는 유일한 속성이며 자식 요소는 자동적으로 flex item이 됨.

## 3. Flexbox container 속성

### 3.1 flex-direction

- flex-direction 속성은 flex 컨테이너의 주축 방향을 설정하마.

```css
/* 좌에서 우로 수평 배치됨. flex-direction 속성의 기본값 */
.flex-container {
  flex-direction: row;
}
```

![flexbox-flex-direction-row.jpg](https://prod-files-secure.s3.us-west-2.amazonaws.com/510cd684-c9a0-45bd-b45d-b35ad6027628/adfe61bd-9883-4c8a-b0f5-eafa5279095e/flexbox-flex-direction-row.jpg)

```css
/* 우에서 좌로 수평 배치됨. */\\
.flex-container {
  flex-direction: row-reverse;
}
```

![flexbox-flex-direction-row-reverse.jpg](https://prod-files-secure.s3.us-west-2.amazonaws.com/510cd684-c9a0-45bd-b45d-b35ad6027628/3e760558-4e73-49db-b16b-36b43a8ee869/flexbox-flex-direction-row-reverse.jpg)

```css
/* 위에서 아래로 수직 배치됨. */
.flex-container {
  flex-direction: column;
}
```

![flexbox-flex-direction-column.jpg](https://prod-files-secure.s3.us-west-2.amazonaws.com/510cd684-c9a0-45bd-b45d-b35ad6027628/f28a64c5-6037-4d5b-b8b9-1df6c17c5d13/flexbox-flex-direction-column.jpg)

```css
/* 아래에서 위로 수직 배치됨. */
.flex-container {
  flex-direction: column-reverse;
}
```

![flexbox-flex-direction-column-reverse.jpg](https://prod-files-secure.s3.us-west-2.amazonaws.com/510cd684-c9a0-45bd-b45d-b35ad6027628/781d1183-bea5-4b1b-b9c2-c615823e7378/flexbox-flex-direction-column-reverse.jpg)

### 3.2 flex-wrap

- flex-wrap 속성은 flex 컨테이너의 복수 flex item을 1행으로 또는 복수행으로 배치함.

```css
.flex-container {
  flex-wrap: nowrap; /* flex-wrap 속성의 기본값*/
}
```

![flexbox-flex-wrap-nowrap.jpg](https://prod-files-secure.s3.us-west-2.amazonaws.com/510cd684-c9a0-45bd-b45d-b35ad6027628/640d7c69-58d0-4e7d-b151-fdb909ed1383/flexbox-flex-wrap-nowrap.jpg)

- flex item들의 width의 합계가 flex 컨테이너의 width보다 큰 경우 flex 컨테이너를 넘치게 됨. 이때 overflow: auto;를 지정하면 가로 스크롤이 생기며 컨테이너를 넘치지 않음.
- flex item들의 width의 합계가 flex 컨테이너의 width보다 큰 경우 flex item을 복수행에 배치함.(기본적으로 좌에서 우로, 위에서 아래로 배치됨.)

```css
`.flex-container {
  flex-wrap: wrap;
}
```

![flexbox-flex-wrap-wrap.jpg](https://prod-files-secure.s3.us-west-2.amazonaws.com/510cd684-c9a0-45bd-b45d-b35ad6027628/d5aea69f-b7e4-4eac-b0b1-b2c3c7f5c8fa/flexbox-flex-wrap-wrap.jpg)

- flex-wrap: wrap;과 동일하나 아래에서 위로 배치됨.

```css
.flex-container {
  flex-wrap: wrap-reverse;
}
```

![flexbox-flex-wrap-wrap-reverse.jpg](https://prod-files-secure.s3.us-west-2.amazonaws.com/510cd684-c9a0-45bd-b45d-b35ad6027628/83c98834-d527-4a15-89eb-91b0c62e489b/flexbox-flex-wrap-wrap-reverse.jpg)

### 3.3 flex-flow

- flex-flow 속성은 flex-direction 속성과 flex-wrap 속성을 설정하기 위한 shrthand임.(기본값은 row nowrap.)

```css
.flex-container {
  flex-flow: <flex-direction> || <flex-wrap>;
}
```

### 3.4 justify-content

- flex container의 main axis를 기준으로 flex item을 수평 정렬함.
- main start를 기준으로 정렬함.(justify-content 속성의 기본값.)

```css
.flex-container {
  justify-content: flex-start;
}
```

![flexbox-justify-content-flex-start.jpg](https://prod-files-secure.s3.us-west-2.amazonaws.com/510cd684-c9a0-45bd-b45d-b35ad6027628/c925d7a7-b054-4ffe-98b0-ba1c2e9ee8ab/flexbox-justify-content-flex-start.jpg)

- main end를 기준으로 정렬함.

```css
.flex-container {
  justify-content: flex-end;
}
```

![flexbox-justify-content-flex-end.jpg](https://prod-files-secure.s3.us-west-2.amazonaws.com/510cd684-c9a0-45bd-b45d-b35ad6027628/b3e37605-c06a-4135-b20e-fc3c1bbe0aa6/flexbox-justify-content-flex-end.jpg)

- flex container의 중앙에 정렬함.

```css
.flex-container {
  justify-content: center;
}
```

![flexbox-justify-content-center.jpg](https://prod-files-secure.s3.us-west-2.amazonaws.com/510cd684-c9a0-45bd-b45d-b35ad6027628/7a93ad81-8ba4-49d3-abf2-4ed977ba8d10/flexbox-justify-content-center.jpg)

- 첫번째와 마지막 flex item은 좌우 측면에 정렬되고 나머지와 균등한 간격으로 정렬됨.

```css
**.flex-container {
  justify-content: space-between;
}**
```

![flexbox-justify-content-space-between.jpg](https://prod-files-secure.s3.us-west-2.amazonaws.com/510cd684-c9a0-45bd-b45d-b35ad6027628/b9ed809c-09cf-421a-a851-b0e5cf0bdbf7/flexbox-justify-content-space-between.jpg)

- 모든 flex item은 균등한 간격으로 정렬됨.

```css
.flex-container {
  justify-content: space-around;
}
```

![flexbox-justify-content-space-around.jpg](https://prod-files-secure.s3.us-west-2.amazonaws.com/510cd684-c9a0-45bd-b45d-b35ad6027628/ecc5aa35-9092-4f06-8e04-a162b237ff87/flexbox-justify-content-space-around.jpg)

### 3.5 align-items

- flex item을 flex container의 수직 방향으로 정렬함.(align-items 속성은 모든 flex item에 적용됨.)
- 모든 flex item은 flex container의 높이에 꽉찬 높이를 갖음.(align-items 속성의 기본값.)

```css
.flex-container {
  align-items: stretch;
}
```

![flexbox-align-items-stretch.jpg](https://prod-files-secure.s3.us-west-2.amazonaws.com/510cd684-c9a0-45bd-b45d-b35ad6027628/014e2e33-3957-476a-a21d-c9929f8c4136/flexbox-align-items-stretch.jpg)

- 모든 flex item은 flex container의 cross start 기준으로 정렬됨.

```css
.flex-container {
  align-items: flex-start;
}
```

![flexbox-align-items-flex-start.jpg](https://prod-files-secure.s3.us-west-2.amazonaws.com/510cd684-c9a0-45bd-b45d-b35ad6027628/4ab2588a-a353-4309-8f6f-5b6732a3e50b/flexbox-align-items-flex-start.jpg)

- 모든 flex item은 flex container의 cross end 기준으로 정렬됨.

```css
.flex-container {
  align-items: flex-end;
}
```

![flexbox-align-items-flex-end.jpg](https://prod-files-secure.s3.us-west-2.amazonaws.com/510cd684-c9a0-45bd-b45d-b35ad6027628/6c69b8c3-cdea-4f94-9e42-0975cb7f53ab/flexbox-align-items-flex-end.jpg)

- 모든 flex item은 flex container의 cross axis의 중앙에 정렬됨.

```css
.flex-container {
  align-items: center;
}
```

![flexbox-align-items-center.jpg](https://prod-files-secure.s3.us-west-2.amazonaws.com/510cd684-c9a0-45bd-b45d-b35ad6027628/e601d7a0-44d2-4ad3-b978-de7e83f954c2/flexbox-align-items-center.jpg)

- 모든 flex item은 flex container의 baseline을 기준으로 정렬됨.

```css
.flex-container {
  align-items: baseline;
}
```

![flexbox-align-items-baseline.jpg](https://prod-files-secure.s3.us-west-2.amazonaws.com/510cd684-c9a0-45bd-b45d-b35ad6027628/8928e553-7492-40b9-ba76-abceb4019e70/flexbox-align-items-baseline.jpg)

### 3.6 align-content

- flex container의 cross axis를 기준으로 flex item을 수직 정렬함.
- 모든 flex item은 flex item의 행 이후에 균등하게 분배된 공간에 정렬되어 배치됨.(align-content 속성의 기본값.)

```css
.flex-container {
  align-content: stretch;
}
```

![flexbox-align-content-stretch.jpg](https://prod-files-secure.s3.us-west-2.amazonaws.com/510cd684-c9a0-45bd-b45d-b35ad6027628/d6b90c61-986a-4a2a-98da-5eef1c6ccf1b/flexbox-align-content-stretch.jpg)

- 모든 flex item은 flex container의 cross start 기준으로 stack 정렬됨.

```css
.flex-container {
  align-content: flex-start;
}
```

![flexbox-align-content-flex-start.jpg](https://prod-files-secure.s3.us-west-2.amazonaws.com/510cd684-c9a0-45bd-b45d-b35ad6027628/05b39bc7-efff-4aab-901c-dcf05386c1b9/flexbox-align-content-flex-start.jpg)

- 모든 flex item은 flex container의 cross end 기준으로 stack 정렬됨.

```css
.flex-container {
  align-content: flex-end;
}
```

![flexbox-align-content-flex-end.jpg](https://prod-files-secure.s3.us-west-2.amazonaws.com/510cd684-c9a0-45bd-b45d-b35ad6027628/8a6d1fb8-8633-498d-b591-e58b784242c9/flexbox-align-content-flex-end.jpg)

- 모든 flex item은 flex container의 cross axis의 중앙에 stack 정렬됨.

```css
.flex-container {
  align-content: center;
}
```

![flexbox-align-content-center.jpg](https://prod-files-secure.s3.us-west-2.amazonaws.com/510cd684-c9a0-45bd-b45d-b35ad6027628/5879341b-746b-44f2-a1b3-a666bc7a71ae/flexbox-align-content-center.jpg)

- 첫번째 flex item의 행은 flex container의 상단에 마지막 flex item의 행은 flex container의 하단에 배치되며 나머지 행은 균등 분할된 공간에 배치 정렬됨.

```css
.flex-container {
  align-content: space-between;
}
```

![flexbox-align-content-space-between.jpg](https://prod-files-secure.s3.us-west-2.amazonaws.com/510cd684-c9a0-45bd-b45d-b35ad6027628/9cc2f628-c5f9-4dc7-bb34-df1c70e81de4/flexbox-align-content-space-between.jpg)

- 모든 flex item은 균등 분할된 공간 내에 배치 정렬됨.

```css
.flex-container {
  align-content: space-around;
}
```

![flexbox-align-content-space-around.jpg](https://prod-files-secure.s3.us-west-2.amazonaws.com/510cd684-c9a0-45bd-b45d-b35ad6027628/b15313e5-526b-4f66-8299-e07bf9ddc9c8/flexbox-align-content-space-around.jpg)

## 4. Flexbox item 속성

- float, clear, vertical-align 속성은 flex item에 영향을 주지 않는다.

### 4.1 order

- flex item의 배치 순서를 지정함.
- 기본 배치 순서는 flex container에 추가된 순서임.(기본값은 0.)

```css
.flex-item {
  order: 정수값;
}
```

![flexbox-order.jpg](https://prod-files-secure.s3.us-west-2.amazonaws.com/510cd684-c9a0-45bd-b45d-b35ad6027628/dd8bd82c-f1fd-45aa-9774-c547a181d845/flexbox-order.jpg)

### 4.2 flex-grow

- flex item의 너비에 대한 확대 인자를 지정함.(기본값은 0, 음수값은 무효함.)

```css
.flex-item{
  flex-grow: 양의 정수값;
}
```

- 모든 flew item이 동일한 flex-grow 속성값은 가지면 모든 flex item은 동일한 너비를 갖음.

  ![flexbox-flex-grow-1.jpg](https://prod-files-secure.s3.us-west-2.amazonaws.com/510cd684-c9a0-45bd-b45d-b35ad6027628/fd963ed9-4f57-4ebb-bb73-d439689aeb85/flexbox-flex-grow-1.jpg)

- 두번째 flex item의 flex-grow 속성값을 3으로 지정하면 다른 flex item 보다 더 넓은 너비를 갖음.

  ![flexbox-flex-grow-2.jpg](https://prod-files-secure.s3.us-west-2.amazonaws.com/510cd684-c9a0-45bd-b45d-b35ad6027628/d33d61e8-6ff3-4057-b079-f48d94c0ff5b/flexbox-flex-grow-2.jpg)

### 4.3 flex-shrink

- flex item의 너비에 대한 축소 인자를 지정함.(기본값은 1, 음수값은 무효함. 0을 지정하면 축소가 해제되어 원래의 너비를 유지.)

```css
.flex-item {
  flex-shrink: 양의 정수값;
}
```

- 기본적으로 모든 flex item은 축소된 상태로 지정하고 두번째 flex item만 축소를 해제하면 원래의 너비를 유지함.

  ![flexbox-flex-shrink.jpg](https://prod-files-secure.s3.us-west-2.amazonaws.com/510cd684-c9a0-45bd-b45d-b35ad6027628/3784b571-df67-4ef1-a786-3cbc00b2d495/flexbox-flex-shrink.jpg)

### 4.4 flex-basis

- flex item의 너비 기본값을 px, % 등의 단위로 지정함.(기본값은 auto)

```css
.flex-item {
   flex-basis: auto | <width>;
}
```

![flexbox-flex-basis.jpg](https://prod-files-secure.s3.us-west-2.amazonaws.com/510cd684-c9a0-45bd-b45d-b35ad6027628/bc4a17c5-f1bf-4493-b85e-0d5279e7ecbd/flexbox-flex-basis.jpg)

### 4.5 flex

- flex-grow, flex-shrink, flex-basis 속성의 shorthand임.(기본갑슨 0 1 auto)

```css
.flex-item {
  flex: none | auto | [ <flex-grow> <flex-shrink>? || <flex-basis> ];
}
```

### 4.6 align-self

- align-items 속성보다 우선하여 개별 flex item을 정렬함.(기본값은 auto)

```css
.flex-item {
  align-self: auto | flex-start | flex-end | center | baseline | stretch;
}
```

- 3번째, 4번째 flex item은 align-self 속성값이 우선 적용되어 정렬됨.

  ![flexbox-align-self.jpg](https://prod-files-secure.s3.us-west-2.amazonaws.com/510cd684-c9a0-45bd-b45d-b35ad6027628/d8a54b95-8c3d-42fa-ab11-1a2fa75d0ad5/flexbox-align-self.jpg)