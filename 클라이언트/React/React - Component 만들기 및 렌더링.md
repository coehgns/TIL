<<<<<<< HEAD
# React - Component 만들기 및 렌더링

------

컴포넌트는 크게 Function Component와 Class Component로 나뉨.

### Function Component

```jsx
// Function Component 예제

function Welcome(props) {
  return <h1>hello. {props.name}</h1>
}
```

### Class Component

- class 컴포넌트는 class라는 것을 사용해서 만들어진 형태의 컴포넌트임.

```jsx
// class Component 예제

class Welcome extends React.Component {
  render() {
    return <h1>hello, {this.props.name}</h1>
  }
}
```

------

## Component 이름 짓기

- Component의 이름은 항상 대문자로 시작해야 함.
  - React는 소문자로 시작하는 컴포넌트를 DOM 태그로 인식하기 때문.

```jsx
// 예제 코드
// Welcome이라는 리액트 Component로 인식

const element = <WelCome name="인제" />;
```

------

### Component 렌더링

- 컴포넌트가 직접 화면에 렌더링되지는 않음.
- 렌더링을 하기 위해서는 가장 먼저 컴포넌트로부터 엘리먼트를 만들어야 함.

```jsx
// 렌더링 코드

function Welcome(props) {
  return <h1>hello, {props.name}<h1>;
}
const element = <Welcome name="인제" />;
ReactDOM.render(
  element,
  document.getElementById('root')
);
```

------

## 참고 자료

- https://www.inflearn.com/course/lecture?courseSlug=처음-만난-리액트&unitId=113270

=======
# React - Component 만들기 및 렌더링

------

컴포넌트는 크게 Function Component와 Class Component로 나뉨.

### Function Component

```jsx
// Function Component 예제

function Welcome(props) {
  return <h1>hello. {props.name}</h1>
}
```

### Class Component

- class 컴포넌트는 class라는 것을 사용해서 만들어진 형태의 컴포넌트임.

```jsx
// class Component 예제

class Welcome extends React.Component {
  render() {
    return <h1>hello, {this.props.name}</h1>
  }
}
```

------

## Component 이름 짓기

- Component의 이름은 항상 대문자로 시작해야 함.
  - React는 소문자로 시작하는 컴포넌트를 DOM 태그로 인식하기 때문.

```jsx
// 예제 코드
// Welcome이라는 리액트 Component로 인식

const element = <WelCome name="인제" />;
```

------

### Component 렌더링

- 컴포넌트가 직접 화면에 렌더링되지는 않음.
- 렌더링을 하기 위해서는 가장 먼저 컴포넌트로부터 엘리먼트를 만들어야 함.

```jsx
// 렌더링 코드

function Welcome(props) {
  return <h1>hello, {props.name}<h1>;
}
const element = <Welcome name="인제" />;
ReactDOM.render(
  element,
  document.getElementById('root')
);
```

------

## 참고 자료

- https://www.inflearn.com/course/lecture?courseSlug=처음-만난-리액트&unitId=113270

>>>>>>> 88752f10985abb553e5666fa10794057c19770e8
------