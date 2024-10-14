<<<<<<< HEAD
# React - JSX 장점과 사용법

------

## 장점

- 코드가 간결해짐.

```jsx
// JSX 사용

<div>Hello, {name}</div>
// JSX 사용 안함

React.createElement('div', null, 'Hello, ${name}');
```

- 가독성 향상
  - 가독성이 높을수록 코드상에 존재하는 버그를 쉽게 발견할 수 있음.
- 보완성 향상(Injection Attacks 방어)

------

### [ 사용 방법 ]

- 기본적으로 JSX는 자바스크립트 문법을 확장시킨 것이므로 모든 자바스크립트 문법을 지원함.

```jsx
/*  XML / HTML 코드를 사용하다가 중간에 자바스크립트 코드를 사용하고 싶으면
중괄호를 이용하여 묶어주면 됨. */

XML / HTML
{JavaScript 코드}
XML / HTML
```

------

### HTML 태그의 속성에 값을 넣고 싶을 때

- 큰 따옴표 사이에 문자열을 넣거나 중괄호 사이에 자바스크립트 코드를 넣으면 됨.

------

### 자식(Children)을 정의하는 방법

```jsx
const element = (
    <div>
        <h1>안녕하세요</h1>
        <h2>열심히 리액트를 공부해 봅시다.</h2>
    <div>
);
```

- 평소에 HTML을 사용하듯이 상위 태그가 하위 태그를 둘러싸도록 하면 칠드런이 정의됨.

------

## 참고 자료

=======
# React - JSX 장점과 사용법

------

## 장점

- 코드가 간결해짐.

```jsx
// JSX 사용

<div>Hello, {name}</div>
// JSX 사용 안함

React.createElement('div', null, 'Hello, ${name}');
```

- 가독성 향상
  - 가독성이 높을수록 코드상에 존재하는 버그를 쉽게 발견할 수 있음.
- 보완성 향상(Injection Attacks 방어)

------

### [ 사용 방법 ]

- 기본적으로 JSX는 자바스크립트 문법을 확장시킨 것이므로 모든 자바스크립트 문법을 지원함.

```jsx
/*  XML / HTML 코드를 사용하다가 중간에 자바스크립트 코드를 사용하고 싶으면
중괄호를 이용하여 묶어주면 됨. */

XML / HTML
{JavaScript 코드}
XML / HTML
```

------

### HTML 태그의 속성에 값을 넣고 싶을 때

- 큰 따옴표 사이에 문자열을 넣거나 중괄호 사이에 자바스크립트 코드를 넣으면 됨.

------

### 자식(Children)을 정의하는 방법

```jsx
const element = (
    <div>
        <h1>안녕하세요</h1>
        <h2>열심히 리액트를 공부해 봅시다.</h2>
    <div>
);
```

- 평소에 HTML을 사용하듯이 상위 태그가 하위 태그를 둘러싸도록 하면 칠드런이 정의됨.

------

## 참고 자료

>>>>>>> 88752f10985abb553e5666fa10794057c19770e8
- https://www.inflearn.com/course/lecture?courseSlug=처음-만난-리액트&unitId=113263