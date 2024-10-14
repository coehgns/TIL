# CSS3 Transition

- 트랜지션은 CSS 프로퍼티의 값이 변화할 때, 프로퍼티 값의 변화가 일정 시간에 걸쳐 일어나도록 하는 것.

```html
<!DOCTYPE html>
<html>
<head>
  <style>
    div {
      width: 100px;
      height: 100px;
      background: red;
    }
    div:hover {
      border-radius: 50%;
      background: blue;
    }
  </style>
</head>
<body>
  <div></div>
</body>
</html>
```

- result

  ![transition2.png](https://prod-files-secure.s3.us-west-2.amazonaws.com/510cd684-c9a0-45bd-b45d-b35ad6027628/71ed806c-ea50-4f86-8c8b-0b2974aa005b/transition2.png)

  ![transition.png](https://prod-files-secure.s3.us-west-2.amazonaws.com/510cd684-c9a0-45bd-b45d-b35ad6027628/f2bdba18-b571-43c1-a5f4-868d5f454a57/transition.png)

- 트랜지션은 상태 변화에 동반하여 변경되는 CSS 프로퍼티 값에 의한 표시의 변화를 부드럽게 하기 위해 애니메이션 속도를 조절함.

- 프로퍼티 값의 변경이 표시의 변화에 즉시 영향을 미치게 하는 대신 그 프로퍼티 값의 변화가 일정 시간에 걸쳐 일어나도록 하는 것.

- transition의 프로퍼티

| 프로퍼티                   | 설명                                                         | 기본값 |
| -------------------------- | ------------------------------------------------------------ | ------ |
| transition-property        | 트랜지션의 대상이 되는 CSS 프로퍼티를 지정한다               | all    |
| transition-duration        | 트랜지션이 일어나는 지속시간(duration)을 초 단위(s) 또는 밀리 초 단위(ms)로 지정한다 | 0s     |
| transition-timing-function | 트랜지션 효과를 위한 수치 함수를 지정한다.                   | ease   |
| transition-delay           | 프로퍼티가 변화한 시점과 트랜지션이 실제로 시작하는 사이에 대기하는 시간을 초 단위(s) 또는 밀리 초 단위(ms)로 지정한다 | 0s     |
| transition                 | 모든 트랜지션 프로퍼티를 한번에 지정한다 (https://www.w3.org/TR/css3-transitions/#transition-shorthand-property) |        |

## 1. transition-property

- transition-property 프로퍼티는 트랜지션의 대상이 되는 CSS 프로퍼티명을 지정함.(지정하지 않는 경우 모든 프로퍼티가 트랜지션의 대상이 됨.)
- 복수의 프로퍼티를 지정하는 경우 쉼표(,)로 구분.

<aside> 🚫 모든 CSS 프로퍼티가 트랜지션의 대상이 될 수 없음.

</aside>

- 트랜지션의 대상이 될 수 있는 CSS 프로퍼티

```html
CODE
// Box model
width height max-width max-height min-width min-height
padding margin
border-color border-width border-spacing
// Background
background-color background-position
// 좌표
top left right bottom
// 텍스트
color font-size font-weight letter-spacing line-height
text-indent text-shadow vertical-align word-spacing
// 기타
opacity outline-color outline-offset outline-width
visibility z-index
```

- 요소의 프로퍼티 값이 변화하면 브라우저는 프로퍼티 값의 변화에 영향을 받는 모든 요소의 기하값(위치와 크기)를 계산하여 layout 작업을 수행함.
- layout에 영향을 주는 프로퍼티

```html
CODE
width height padding margin border
display position float overflow
top left right bottom
font-size font-family font-weight
text-align vertical-align line-height
clear white-space
```

## 2. transition-duration

- transition-duration 프로퍼티는 트랜지션에 일어나는 지속시간을 초 단위 또는 밀치 초 단위로 지정함.(프로퍼티 값을 지정하지 않을 경우 기본값 0s이 적용되어 어떠한 트랜지션 효과도 볼 수 없음.)
- transition-duration 프로퍼티값은 transition-property 프로퍼티값과 1:1 대응함.

```css
/*width 프로퍼티는 2초의 지속시간을 갖음.*/
div {
  transition-property: width;
  transition-duration: 2s;
}
/* width 프로퍼티는 2초, opacity 프로퍼티는 4초의 지속시간을 갖음. */
div {
  transition-property: width, opacity;
  transition-duration: 2s, 4s;
}
/* transition 프로퍼티만으로 축약 표현 가능.*/
div {
  /* shorthand syntax */
  transition: width 2s, opacity 4s;
}
/* width 프로퍼티는 2초, opacity 프로퍼티는 1초, left 프로퍼티는 2초, 
top 프로퍼티는 1초의 지속시간을 갖음. */
div {
  transition-property: width, opacity, left, top;
  transition-duration: 2s, 1s;
}
```

## 3. transition-timing-function

- 트랜지션 효관의 변화 흐름, 시간에 따른 변화 속도와 같은 일종의 변화의 리듬을 지정함.
- 대부분의 타이밍 함수는 큐빅 베이지어를 정의하는 네 점에 의해 정의되므로 상응하는 함수의 그래프로 제공해서 명시할 수 있음.

[제목 없는 데이터베이스](https://www.notion.so/4fd607164414487788e7ffe0c2582426?pvs=21)

## 4. transition-delay

- 프로퍼티가 변화한 시점과 트랜지션이 실제로 시작하는 사이에 대기하는 시간을 초 단위 또는 밀리 초 단위로 지정함.
- transition-delay로 대기 시간을 지정하여 프로퍼티의 값이 변화하여도 즉시 트랜지션이 실행되지 않고, 일정 시간 대기한 후 트랜지션이 실행되도록 함.

## 5. transition

- 모든 트랜지션 프로퍼티를 한번에 지정할 수 있는 shorthand.

```css
CODE
transition: property duration function delay
```

- transition-duration은 반드시 지정해야 함.(지정하지 않는 경우 기본값 0이 셋팅되어 어떠한 트랜지션도 실행되지 않음.)

```css
CODE
all 0 ease 0
```