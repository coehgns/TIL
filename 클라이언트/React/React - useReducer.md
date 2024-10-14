<<<<<<< HEAD
# React - useReducer

------

# useReducer

- useState의 대체 함수.
- State를 관리하고 업데이트할 수 있는 Hook.
- 좀 더 복잡한 로직을 다룰 수 있음.

------

- 컴포넌트에서 상태를 변경하면 해당 컴포넌트가 다시 렌더링됨.

## useReducer와 useState의 차이점

- useState는 간단한 상태 로직을 다루기에 적합한 반면 useReducer는 좀 더 복잡한 상태 로직을 다룰 수 있음.
- useState는 상태를 업데이트할 때 이전 상태를 덮어쓰는 반면, useReducer는 이전 상태를 변경하지 않고 새로운 상태를 생성함.
- useState는 한 개의 상태만 다룰 수 있지만, useReducer는 여러 개의 연관된 상태를 함께 다룰 수 있음.
- useState는 컴포넌트 내부에서 상태를 다루지만, useReducer는 다른 파일에서 리듀서 함수를 정의하여 상태를 다룰 수 있음.

------

## useReducer를 사용하기 위한 구성 요소 4가지

1. useReducer 함수
2. action
3. dispatch 함수
4. reducer 함수

------

### useReducer 함수

- useReducer 함수는 첫 번째 인자인 reducer 함수가 반환하는 값으로 state를 갱신하는 역할을 함.

```jsx
// useReducer 사용 형태

const [state, dispatch] = useReducer(reducer, initialState, init);
```

- state : 컴포넌트에서 사용할 State
- dispatch : reducer 함수를 실행시키며, 컴포넌트 내에서 state의 업데이트를 일으키기 위해서 사용하는 함수.
- reducer : 컴포넌트 외부에서 state를 업데이트하는 로직을 담당하는 함수. 현재의 state와 action 객체를 인자로 받아서, 기존의 state를 대체(replace)할 새로운 State를 반환하는 함수.
- initialState : 초기 State
- init : 초기 함수

------

### action

- action은 업데이트를 위한 정보를 가지고 있는 것이며, dispatch의 인자가 되며, reducer 함수의 두 번째 인자인 action에 할당됨.
- 주로 type이라는 값을 지닌 객체 형태로 사용됨.

------

### dispatch 함수

- dispatch 함수는 reducer 함수를 실행시킴.
- dispatch 함수의 인자로써 업데이트를 위한 정보를 가진 action을 이용하며, 컴포넌트 내에서 state의 업데이트를 일으키기 위해 사용됨.
- dispatch 함수의 인자인 action은 reducer 함수의 두 번째 인자인 action에 할당됨.

------

### reducer 함수

- reducer 함수는 dispatch 함수에 의해 실행되며, 컴포넌트 외부에서 state를 업데이트하는 로직을 담당함.
- useReducer 함수의 첫 번째 파라미터로 입력된 reducer 함수는, 현재의 state와 action은 인자로 받게 되는데, 이 action 값에 근거하여 기존의 state를 대체할 새로운 state를 반환함.

```jsx
function reducer(state, action) {
  switch (action.type) {
    case "decrement":
      // action의 type이 "decrement"일 때, 현재 state에서 1을 뺀 값을 반홤함
      return state - 1;
    case "increment":
      // action의 type이 "increment"일 때, 현재 state에서 1을 더한 값을 반환함
      return state + 1;
    default:
      // 정의되지 않은 action type이 넘어왔을 때는 에러를 발생시킴
      throw new Error("Unsupported action type:", action.type);
  }
}
```

------

## 참고 자료

- https://despiteallthat.tistory.com/183

=======
# React - useReducer

------

# useReducer

- useState의 대체 함수.
- State를 관리하고 업데이트할 수 있는 Hook.
- 좀 더 복잡한 로직을 다룰 수 있음.

------

- 컴포넌트에서 상태를 변경하면 해당 컴포넌트가 다시 렌더링됨.

## useReducer와 useState의 차이점

- useState는 간단한 상태 로직을 다루기에 적합한 반면 useReducer는 좀 더 복잡한 상태 로직을 다룰 수 있음.
- useState는 상태를 업데이트할 때 이전 상태를 덮어쓰는 반면, useReducer는 이전 상태를 변경하지 않고 새로운 상태를 생성함.
- useState는 한 개의 상태만 다룰 수 있지만, useReducer는 여러 개의 연관된 상태를 함께 다룰 수 있음.
- useState는 컴포넌트 내부에서 상태를 다루지만, useReducer는 다른 파일에서 리듀서 함수를 정의하여 상태를 다룰 수 있음.

------

## useReducer를 사용하기 위한 구성 요소 4가지

1. useReducer 함수
2. action
3. dispatch 함수
4. reducer 함수

------

### useReducer 함수

- useReducer 함수는 첫 번째 인자인 reducer 함수가 반환하는 값으로 state를 갱신하는 역할을 함.

```jsx
// useReducer 사용 형태

const [state, dispatch] = useReducer(reducer, initialState, init);
```

- state : 컴포넌트에서 사용할 State
- dispatch : reducer 함수를 실행시키며, 컴포넌트 내에서 state의 업데이트를 일으키기 위해서 사용하는 함수.
- reducer : 컴포넌트 외부에서 state를 업데이트하는 로직을 담당하는 함수. 현재의 state와 action 객체를 인자로 받아서, 기존의 state를 대체(replace)할 새로운 State를 반환하는 함수.
- initialState : 초기 State
- init : 초기 함수

------

### action

- action은 업데이트를 위한 정보를 가지고 있는 것이며, dispatch의 인자가 되며, reducer 함수의 두 번째 인자인 action에 할당됨.
- 주로 type이라는 값을 지닌 객체 형태로 사용됨.

------

### dispatch 함수

- dispatch 함수는 reducer 함수를 실행시킴.
- dispatch 함수의 인자로써 업데이트를 위한 정보를 가진 action을 이용하며, 컴포넌트 내에서 state의 업데이트를 일으키기 위해 사용됨.
- dispatch 함수의 인자인 action은 reducer 함수의 두 번째 인자인 action에 할당됨.

------

### reducer 함수

- reducer 함수는 dispatch 함수에 의해 실행되며, 컴포넌트 외부에서 state를 업데이트하는 로직을 담당함.
- useReducer 함수의 첫 번째 파라미터로 입력된 reducer 함수는, 현재의 state와 action은 인자로 받게 되는데, 이 action 값에 근거하여 기존의 state를 대체할 새로운 state를 반환함.

```jsx
function reducer(state, action) {
  switch (action.type) {
    case "decrement":
      // action의 type이 "decrement"일 때, 현재 state에서 1을 뺀 값을 반홤함
      return state - 1;
    case "increment":
      // action의 type이 "increment"일 때, 현재 state에서 1을 더한 값을 반환함
      return state + 1;
    default:
      // 정의되지 않은 action type이 넘어왔을 때는 에러를 발생시킴
      throw new Error("Unsupported action type:", action.type);
  }
}
```

------

## 참고 자료

- https://despiteallthat.tistory.com/183

>>>>>>> 88752f10985abb553e5666fa10794057c19770e8
------