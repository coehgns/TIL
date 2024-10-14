# CSS3 Animation

- 애니메이션 효과는 HTML 요소에 적용되는 CSS 스타일을 다른 CSS 스타일로 부드럽게 변화시킴.
- 애니메이션은 애니메이션을 나타내는 CSS 스타일과 애니메이션의 sequence를 나타내는 복수의 키프레임들로 이루어짐.
- transition 프로퍼티는 단순히 요소의 프로퍼티 변화에 주안점이 있다면 anmation 프로퍼티는 하나의 줄거리를 구성하여 줄거리 내에서 세부 움직임을 시간 흐름 단위로 제어할 수 있고 전체 줄거리의 재생과 정지, 반복까지 제어할 수 있음.

| 프로퍼티                  | 설명                                                         | 기본값  |
| ------------------------- | ------------------------------------------------------------ | ------- |
| animation-name            | @keyframes 애니메이션 이름을 지정한다                        |         |
| animation-duration        | 한 싸이클의 애니메이션에 소요되는 시간을 초 단위(s) 또는 밀리 초 단위(ms)로 지정한다. | 0s      |
| animation-timing-function | 애니메이션 효과를 위한 타이밍 함수를 지정한다.               | ease    |
| animation-delay           | 요소가 로드된 시점과 애니메이션이 실제로 시작하는 사이에 대기하는 시간을 초 단위(s) 또는 밀리 초 단위(ms)로 지정한다 | 0s      |
| animation-iteration-count | 애니메이션 재생 횟수를 지정한다.                             | 1       |
| animation-direction       | 애니메이션이 종료된 이후 반복될 때 진행하는 방향을 지정한다. | normal  |
| animation-fill-mode       | 애니메이션 미실행 시(종료 또는 대기) 요소의 스타일을 지정한다. |         |
| animation-play-state      | 애니메이션 재생 상태(재생 또는 중지)를 지정한다.             | running |
| animation                 | 모든 애니메이션 프로퍼티를 한번에 지정한다 (https://drafts.csswg.org/css-animations/#animation) |         |

## 1. @keyframes

- CSS 애니메이션과 트랜지션 방식의 주된차이는 @keyframes rule에 있는데 이 rule을 사용하면 애니메이션의 흐름 중의 여러 시점에서 CSS 프로퍼티값을 지정할 수 있음.

```html
<!DOCTYPE html>
<html>
<head>
  <style>
    div {
      position: absolute;
      width: 100px;
      height: 100px;
      background-color: red;
      animation-name: move;
      animation-duration: 5s;
      animation-iteration-count: infinite;
    }
    /* @keyframes rule */
    @keyframes move {
      /* keyframe */
      from {
        left: 0;
      }
      /* keyframe */
      to {
        left: 300px;
      }
    }
  </style>
</head>
<body>
  <div></div>
</body>
</html>
```

- @keyframes rule은 시간의 흐름에 따라 애니메이션을 정의함.
- 여러 개의 키프레임을 정의하거나 애니메이션 중에 특정 CSS 프로퍼티에 값을 지정하는 지점을 정의할 수 있음.

```css
@keyframes move{}
```

- from, to 키워드를 사용하여 애니메이션의 시작과 끝 시점을 정의할 수 있음.

```css
@keyframes move {
  /* 애니메이션 시작 시점 */
  from { left: 0; }
  /* 애니메이션 종료 시점 */
  to   { left: 300px; }
}
```

- from, to 키워드 대신 %를 사용할 수 있음. 또 시작과 끝 키프레임 사이에 % 단위로 키프레임을 삽입할 수 있음.

```css
@keyframes move {
  0%   { left: 0; }
  50%  { left: 100px; }
  100% { left: 300px; }
}
```

## 2. animation-name

```css
@keyframes move {}
```

- 이 이름을 animation-name 프로퍼티값으로 지정하여 사용하고자 하는 @keyframes rule을 선택함.(하나 이상의 애니메이션 이름을 지정할 수 있음.)

```html
<!DOCTYPE html>
<html>
<head>
  <style>
    div {
      position: absolute;
      width: 100px;
      height: 100px;
      animation-name: move, fadeOut, changeColor;
      animation-duration: 5s;
      animation-iteration-count: infinite;
    }
    @keyframes move {
      from { left: 0; }
      to   { left: 300px; }
    }
    @keyframes fadeOut {
      from { opacity: 1; }
      to   { opacity: 0; }
    }
    @keyframes changeColor {
      from { background-color: red; }
      to   { background-color: blue; }
    }
  </style>
</head>
<body>
  <div></div>
</body>
</html>
```

## 3. animation-duration

- 한 싸이클의 애니메이션에 소요되는 시간을 초 단위(s) 또는 밀치 초 단위(ms)로 지정함.

```html
CODE
animation-duration: .5s;
animation-duration: 500ms;
```

- animation-duration은 반드시 지정해야함.(지정하지 않는 경우 기본값 0s가 셋팅되어 어떠한 애니메이션도 실행되지 않음.)

## 4. animation-timing-function

- 애니메이션 효과를 위한 수치 함수를 지정함.

## 5. animation-delay

- 요소가 로드된 시점과 애니메이션이 실제로 시작하는 사이에 대기하는 시간을 초 단위(s) 또는 밀치 초 단위(ms)로 지정함.

```html
CODE
animation-delay: 2s;
```

## 6. animation-iteration-count

- 애니메이션 주기의 재생 횟수를 지정함.(기본값은 1이며 infinite로 무한반복 가능.)

```html
CODE
animation-iteration-count: 3;
```

## 7. animation-direction

- 애니메이션이 종료된 이후 반복될 때 진행하는 방향을 지정함.

| 프로퍼티값        | 설명                                                |
| ----------------- | --------------------------------------------------- |
| normal            | 기본값으로 from(0%)에서 to(100%) 방향으로 진행한다. |
| reverse           | to에서 from 방향으로 진행한다.                      |
| alternate         | 홀수번째는 normal로, 짝수번째는 reverse로 진행한다. |
| alternate-reverse | 홀수번째는 reverse로, 짝수번째는 normal로 진행한다. |

```html
<!DOCTYPE html>
<html>
<head>
  <style>
    div {
      width: 100px;
      height: 100px;
      background: red;
      position: relative;
      animation: myAnimation 5s infinite;
      /*홀수번째는 normal로, 짝수번째는 reverse로 진행*/
      animation-direction: alternate;
    }
    @keyframes myAnimation {
      0%   { background: red;    left: 0px;   top: 0px; }
      25%  { background: yellow; left: 200px; top: 0px; }
      50%  { background: blue;   left: 200px; top: 200px; }
      75%  { background: green;  left: 0px;   top: 200px; }
      100% { background: red;    left: 0px;   top: 0px; }
    }
  </style>
  </head>
  <body>
    <div></div>
  </body>
</html>
```

## 8. animation-fill-mode

- 애니메이션 미실행 시(대기 또는 종료) 요소의 스타일을 지정함.

| 프로퍼티값 | 상태 | 설명                                                         |
| ---------- | ---- | ------------------------------------------------------------ |
| none       | 대기 | 시작 프레임(from)에 설정한 스타일을 적용하지 않고 대기한다.  |
|            | 종료 | 애니메이션 실행 전 상태로 애니메이션 요소의 프로퍼티값을 되돌리고 종료한다. |
| forwards   | 대기 | 시작 프레임(from)에 설정한 스타일을 적용하지 않고 대기한다.  |
|            | 종료 | 종료 프레임(to)에 설정한 스타일을 적용하고 종료한다.         |
| backwards  | 대기 | 시작 프레임(from)에 설정한 스타일을 적용하고 대기한다.       |
|            | 종료 | 애니메이션 실행 전 상태로 애니메이션 요소의 프로퍼티값을 되돌리고 종료한다. |
| both       | 대기 | 시작 프레임(from)에 설정한 스타일을 적용하고 대기한다.       |
|            | 종료 | 종료 프레임(to)에 설정한 스타일을 적용하고 종료한다.         |

## 9. animation-play-state

- 애니메이션 재생 상태(재생 또는 중지)를 지정함.(기본값은 running)

## 10. animation

- 모든 애니메이션 프로퍼티를 한번에 지정함.(값을 지정하지 않은 프로퍼티에는 기본값이 지정됨.)

```html
CODE
animation: name duration timing-function delay iteration-count direction fill-mode play-state
```

- animation=-duration은 반드시 지정해야 함.(지정하지 않는 경우 애니메이션 실행 X)