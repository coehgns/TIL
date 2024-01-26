# React - Context

------

# Context

- 컴포넌트 트리를 통해 곧바로 컴포넌트로 전달하는 새로운 방식을 제공함.
- 일일이 프롭스를 전달할 필요 없이 데이터를 필요로 하는 컴포넌트에 곧바로 데이터를 전달할 수 있음.
- 컨텍스트는 다른 레벨의 많은 컴포넌트가 특정 데이터를 필요로 하는 경우에 주로 사용함.

```jsx
// Context 생성

const MyContext = React.createContext(기본값);
```

- 상위 레벨에 매칭되는 프로바이더가 없다면 이 경우에만 기본값이 사용됨.
- 기본값으로 undefined를 넣으면 기본값이 사용되지 않음.

------

## Context Provider

- 데이터를 제공해주는 컴포넌트
- 모든 컨텍스트 객체는 Provider라는 React 컴포넌트를 갖고 있음.
- Context.provider 컴포넌트로 하위 컴포넌트들을 감싸주면 모든 하위 컴포넌트들이 해당 컨텍스트의 데이터에 접근할 수 있게 됨.

```jsx
// Provider 사용

<MyContext.Provider value={/* some value */}>
```

------

## Context.Consumer

- Consumer 컴포넌트는 컨텍스트의 데이터를 구독하는 컴포넌트임.
- 함수 컴포넌트에서 Context.comsumer를 사용하여 컨텍스트를 구독할 수 있음.

```jsx
// context.consumer 사용 방법

<MyContext.Consumer>
    {value => /* 컨텍스트의 값에 따라 컴포넌트들을 렌더링 */}
</MyContext.Consumer>
```

- 컴포넌트의 자식으로 함수가 올 수 있는데 이것을 function as a child라고 함.
- context.consumer로 감싸주면 자식으로 들어간 함수가 현재 컨텍스트의 value를 받아서 react node로 반환함.

## function as a child

- 컴포넌트의 자식으로 함수를 사용하는 방법임.

```jsx
// function as a child 사용 방법

//children이라는 prop을 직접 선언하는 방식
<Profile children={name => <p>이름: {name}</p>} />

	// Profile 컴포넌트로 감싸서 children으로 만드는 방식
<Profile>{name => <p>이름: {name}</p>}</Profile>
```

------

## useContext()

- useContext() Hook은 함수 컴포넌트에서 컨텍스트를 쉽게 사용할 수 있게 해줌.

------

## 참고 자료

- https://www.inflearn.com/course/lecture?courseSlug=처음-만난-리액트&unitId=113241
- https://www.inflearn.com/course/lecture?courseSlug=처음-만난-리액트&unitId=113242

------