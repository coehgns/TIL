# React - Elements의 특징

------

# Elements 특징

- 불변성을 가지고 있음. (Elements 생성후에는 children이나 attributes를 바꿀 수 없음.)

------

## Elements 렌더링하기

```jsx
// 리액트 엘리먼트를 렌더링하기 위해 사용하는 코드

const element = <h1>hello, React!</h1>;
ReactDOM.render(element, document.getElementById('root'));
```

- 위 코드는 엘리먼트를 하나 생성하고 생성된 엘리먼트를 루트DIV에 렌더링하는 코드임.
- 렌더링을 위해 리액트돔에 렌더라는 함수를 사용하게 되는데 이 함수는 React 엘리먼트를 DOM 엘리먼트에 렌더링하는 역할을 함.

------

## 렌더링된 Elements를 업데이트 하기

- Elements는 한번 생성하면 바꿀 수 없으므로 업데이트하기 위해서는 다시 생성해야 함.

------

## 참고 자료

- https://www.inflearn.com/course/lecture?courseSlug=처음-만난-리액트&unitId=113266