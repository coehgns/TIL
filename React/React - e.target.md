# React - e.target

------

# e.target

- 이벤트가 일어날 객체를 말함.

------

## 이벤트 발생 과정

1. 지정된 event target에
2. 지정된 event type(클릭이나 스크롤 등)이 발생하면
3. 지정된 event handler(함수)가 실행됨.

------

```jsx
export function App(props) {
  const handleClick=(e)=>{console.log(e.target.innerText)}

  return (
    <div className='App'>
      <div onClick={handleClick}>hi</div>
    </div>
  );
}
```

- 화면의 hi 를 클릭 시 클릭이 발생한 객체의 innerText인 hi를 가져와서 로그를 찍음.

------