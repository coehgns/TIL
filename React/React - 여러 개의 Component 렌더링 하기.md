# React - 여러 개의 Component 렌더링 하기

------

- React에서는 배열과 키를 사용하여 반복되는 여러 개의 컴포넌트들을 렌더링 할 수 있음.

  ( 반복되는 다수의 엘리먼트가 렌더링 되는 것. )

------

## map()

- 배열에 들어있는 각 변수에 어떠한 처리를 한 뒤 리턴하는 것.

```jsx
// map() 함수 예제 코드

const doubled = numbers.map((number) => number * 2);
```

- 맵함수는 배열의 첫번째 아이템부터 순서대로 각 아이템의 어떠한 연산을 수행한 뒤에 최종 결과를 배열로 만들어서 리턴해 줌.

------

## 기본적인 List Component

```jsx
// numberList 컴포넌트

function NumberList(props) {
  const { numbers } = props;

  const listItems = numbers.map((number) =>
      <li>{number}</li>
  );

  return (
      <ul>{listItems}</ul>
  );
}

const number = [1, 2, 3, 4, 5];
ReactDOM.render(
    <NumberList numbers={numbers} />,
    document.getElementById('root')
);
```

- numberList 컴포넌트는 props로 숫자가 들어있는 배열일 numbers를 받아서 목록으로 출력함.

------

## 참고 자료

- https://www.inflearn.com/course/lecture?courseSlug=처음-만난-리액트&unitId=113231

------