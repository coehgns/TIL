<<<<<<< HEAD
# React - Props 특징

------

## Props 특징

- 값을 변경할 수 없음.
- 같은 프랍스가 들어오면 항상 같은 엘리먼트를 반환해야 함.
  - 다른 프롭스의 값으로 엘리먼트를 생성하려면 새로운 값을 컴포넌트에 전달하여 새로 엘리먼트를 생성하면 됨.

------

### Props 사용 방법

```jsx
// JSX 사용하는 경우

function App(props) {
  return (
    <Layout 
    width={2560}
    height={1440}
    header={
      <Header title="          " />
    }
    footer={
      <Footer />
    }
    />
  );
}
```

------

## 참고 자료

- https://www.inflearn.com/course/lecture?courseSlug=처음-만난-리액트&unitId=113270

=======
# React - Props 특징

------

## Props 특징

- 값을 변경할 수 없음.
- 같은 프랍스가 들어오면 항상 같은 엘리먼트를 반환해야 함.
  - 다른 프롭스의 값으로 엘리먼트를 생성하려면 새로운 값을 컴포넌트에 전달하여 새로 엘리먼트를 생성하면 됨.

------

### Props 사용 방법

```jsx
// JSX 사용하는 경우

function App(props) {
  return (
    <Layout 
    width={2560}
    height={1440}
    header={
      <Header title="          " />
    }
    footer={
      <Footer />
    }
    />
  );
}
```

------

## 참고 자료

- https://www.inflearn.com/course/lecture?courseSlug=처음-만난-리액트&unitId=113270

>>>>>>> 88752f10985abb553e5666fa10794057c19770e8
------