# React- JSX

------

# JSX

- JSX는 자바스크립트의 문법을 확장 시킨 것임.(자바스크립트, XML, HTML을 합친 것으로 봐도 됨.)
- 리액트는 JSX 코드를 모두 createElement 함수를 사용하는 코드로 변환함.

------

### JSX 코드

```jsx
const element = <h1>Hello, world!</h1>;
```

- 위 코드는 자바스크립트 코드와 HTML 코드가 합쳐진 JSX 코드임.

------

## createElement

- createElement의 파라미터

```jsx
React.createElement(
    type,
    [props],
    [...children]
)
```

------

## 참고 자료

- https://www.inflearn.com/course/lecture?courseSlug=처음-만난-리액트&unitId=113262

------