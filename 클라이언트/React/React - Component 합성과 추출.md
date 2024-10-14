<<<<<<< HEAD
# React - Component 합성과 추출

------

## Component 합성

- 컴포넌트 합성은 여러 개의 컴포넌트를 합쳐서 하나의 컴포넌트를 만드는 것임.
- 리액트에서는 컴포넌트 안에도 다른 컴포넌트를 사용할 수 있으므로 복잡한 화면을 여러 개의 컴포넌트로 나눠서 구현할 수 있음.

```jsx
// 컴포넌트 합성 예제 코드

function Welcome(props) {
  return <h1>Hello, {props.name}</h1>;
}

function App(props) {
  return (
    <div>
      <Welcome name="Mike" />
      <Welcome name="Steve" />
      <Welcome name="Jane" />
    </div>
  )
}

ReacDOM.render(
  <App />,
  document.getElementById('root')
);
```

- 이런 식으로 여러 개의 컴포넌트를 합쳐서 또 다른 컴포넌트를 만드는 것을 컴포넌트 합성이라고 함.

------

## Component 추출

- 복잡한 컴포넌트를 쪼개서 여러 개의 컴포넌트로 나누는 것을 컴포넌트 추출이라고 함.
- 큰 컴포넌트에서 일부를 추출해서 새로운 컴포넌트를 만듦.
- 컴포넌트 추출을 잘 활용하게 되면 컴포넌트의 재사용성이 올라가게 됨.

------

## 참고 자료

- https://www.inflearn.com/course/lecture?courseSlug=처음-만난-리액트&unitId=113271

=======
# React - Component 합성과 추출

------

## Component 합성

- 컴포넌트 합성은 여러 개의 컴포넌트를 합쳐서 하나의 컴포넌트를 만드는 것임.
- 리액트에서는 컴포넌트 안에도 다른 컴포넌트를 사용할 수 있으므로 복잡한 화면을 여러 개의 컴포넌트로 나눠서 구현할 수 있음.

```jsx
// 컴포넌트 합성 예제 코드

function Welcome(props) {
  return <h1>Hello, {props.name}</h1>;
}

function App(props) {
  return (
    <div>
      <Welcome name="Mike" />
      <Welcome name="Steve" />
      <Welcome name="Jane" />
    </div>
  )
}

ReacDOM.render(
  <App />,
  document.getElementById('root')
);
```

- 이런 식으로 여러 개의 컴포넌트를 합쳐서 또 다른 컴포넌트를 만드는 것을 컴포넌트 합성이라고 함.

------

## Component 추출

- 복잡한 컴포넌트를 쪼개서 여러 개의 컴포넌트로 나누는 것을 컴포넌트 추출이라고 함.
- 큰 컴포넌트에서 일부를 추출해서 새로운 컴포넌트를 만듦.
- 컴포넌트 추출을 잘 활용하게 되면 컴포넌트의 재사용성이 올라가게 됨.

------

## 참고 자료

- https://www.inflearn.com/course/lecture?courseSlug=처음-만난-리액트&unitId=113271

>>>>>>> 88752f10985abb553e5666fa10794057c19770e8
------