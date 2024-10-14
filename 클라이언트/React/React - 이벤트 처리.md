<<<<<<< HEAD
# React - 이벤트 처리

------

# onChange

- react에서는 변경될 수 있는 입력값(<input>, <textarea>, <select>) 일반적으로 컴포넌트의 state로 관리하고 업데이트함.
- onChange 이벤트가 발생하면 e.target.value를 통해 이벤트 객체에 담겨있는 input 값을 읽어올 수 있음.
- 컴포넌트 return 문 안에 input 태그에 value와 onChange를 작성하고, onChange는 input의 텍스트가 바뀔 때마다 발생하는 이벤트로, 이벤트가 발생하면 handleChange 함수가 작동하며 이벤트 객체에 담긴 input 값을 setState를 통해 새로운 state로 갱신함.

```jsx
// 예시코드

function NameForm() {
  const [name, setName] = useState("");

  const handleChange = (e) => {
    setName(e.target.value);
};

return (
  <div>
    <input type = "text" value={name} onChange={handleChange}></input>
    <h1>{name}</h1>
  </div>
 )
};
```

------

# onClick

- 사용자가 클릭이라는 행동을 했을 때 발생하는 이벤트.
- 사용자의 행동에 따라 애플리케이션이 반응해야 할 때 자주 사용됨.
- onClick 이벤트에 함수를 전달할 때는 함수를 호출하는 것이 아니라 리턴문 안에서 함수를 정의하거나 리턴문 외부에서 함수를 정의 후 이벤트에 함수 자체를 전달해야 함.

```jsx
// 예시코드

function NameForm() {
  const [name, setName] = useState("");

  const handleChange = (e) => {
    setName(e.target.value);
};

const handleClick = () => {
  alert(name);
}; 
return (
  <div className = "App">
    <h1>Event handler practice</h1>
    <input type = "text" value={name} onChange={handleChange}></input>
    <button onClick={alert(name)>Button</button> 
    <h1>{name}</h1>
  </div>
 )
};
```

- onChange 예시에 버튼을 추가하여 버튼 클릭 시 <input> tag에 입력한 이름이 alert을 통해 알리 창이 팝업 되도록 추가 구현한 코드임.

------

## 참고 자료

- https://velog.io/@ko9612/React-이벤트-처리

=======
# React - 이벤트 처리

------

# onChange

- react에서는 변경될 수 있는 입력값(<input>, <textarea>, <select>) 일반적으로 컴포넌트의 state로 관리하고 업데이트함.
- onChange 이벤트가 발생하면 e.target.value를 통해 이벤트 객체에 담겨있는 input 값을 읽어올 수 있음.
- 컴포넌트 return 문 안에 input 태그에 value와 onChange를 작성하고, onChange는 input의 텍스트가 바뀔 때마다 발생하는 이벤트로, 이벤트가 발생하면 handleChange 함수가 작동하며 이벤트 객체에 담긴 input 값을 setState를 통해 새로운 state로 갱신함.

```jsx
// 예시코드

function NameForm() {
  const [name, setName] = useState("");

  const handleChange = (e) => {
    setName(e.target.value);
};

return (
  <div>
    <input type = "text" value={name} onChange={handleChange}></input>
    <h1>{name}</h1>
  </div>
 )
};
```

------

# onClick

- 사용자가 클릭이라는 행동을 했을 때 발생하는 이벤트.
- 사용자의 행동에 따라 애플리케이션이 반응해야 할 때 자주 사용됨.
- onClick 이벤트에 함수를 전달할 때는 함수를 호출하는 것이 아니라 리턴문 안에서 함수를 정의하거나 리턴문 외부에서 함수를 정의 후 이벤트에 함수 자체를 전달해야 함.

```jsx
// 예시코드

function NameForm() {
  const [name, setName] = useState("");

  const handleChange = (e) => {
    setName(e.target.value);
};

const handleClick = () => {
  alert(name);
}; 
return (
  <div className = "App">
    <h1>Event handler practice</h1>
    <input type = "text" value={name} onChange={handleChange}></input>
    <button onClick={alert(name)>Button</button> 
    <h1>{name}</h1>
  </div>
 )
};
```

- onChange 예시에 버튼을 추가하여 버튼 클릭 시 <input> tag에 입력한 이름이 alert을 통해 알리 창이 팝업 되도록 추가 구현한 코드임.

------

## 참고 자료

- https://velog.io/@ko9612/React-이벤트-처리

>>>>>>> 88752f10985abb553e5666fa10794057c19770e8
------