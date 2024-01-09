# React - Hooks

------

# Hooks

- 함수 컴포넌트에 없는 기능을 클래스 컴포넌트에서 따오는 것.
- 리액트의 훅은 리액트의 state와 생명주기 기능의 갈고리를 걸어 원하는 시점에 정해진 함수를 실행되도록 만든 것임.
- hook의 이름은 모두 use로 시작함.
- 개발자가 커스텀 훅을 만들어 사용할 수도 있음.

------

## 대표적인 Hooks

### useState()

- state를 사용하기 위한 Hook.

```jsx
// useState() 사용법

const [변수명, set함수명] = useState(초기값);
```

### useEffect()

- side effect를 수행하기 위한 Hook.
  - 리액트의 side effect : 효과, 영향

```jsx
// useEffect() 사용법

useEffect(이팩트 함수, 의존성 배열);
```

### useMemo()

- Memoized value를 리턴하는 Hook.

```jsx
// useMemo() 사용법

cosnt memoizedValue = useMemo(
     () => {
         // 연산량이 높은 작업을 수행하여 결과를 반환
         return computeExpensiveValue(의존성 변수1, 의존성 변수 2);
     },
     [의존성 변수1, 의존성 변수2]
);
```

- 의존성 배열을 넣지 않을 경우, 매 렌더링마다 함수가 실행 됨.
- 의존성 배열이 빈 배열일 경우, 컴포넌트 마운트 시에만 호출 됨.

### useCallback()

- useMemo() Hook과 유사하지만 값이 아닌 함수를 반환하는 Hook.

```jsx
// useCallback() 사용법

const memoizedCallback = useCallback(
     () => {
         doSomething(의존성 변수1, 의존성 변수2);
     },
     [의존성 변수1, 의존성 변수2]
);
```

### useRef()

- Reference를 사용하기 위한 Hook.
  - Reference : 특정 컴포넌트에 접근할 수 있는 객체.

```jsx
// useRef() 사용법

const refContainer = useRef(초깃값);
```

- useRef() Hook은 내부의 데이터가 변경되었을 때 별도로 알리지 않음.

------

## 참고 자료

- https://www.inflearn.com/course/lecture?courseSlug=처음-만난-리액트&unitId=113223

------