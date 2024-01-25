# React - useRef

------

# useRef

- useRef Hook은 DOM을 선택하는 용도와 컴포넌트 안에서 조회 및 수정 할 수 있는 변수를 관리함.
- useRef로 관리하는 변수는 값이 바뀐다고 해서 컴포넌트가 리렌더링되지 않음.
- useRef로 관리하고 있는 변수는 설정 후 바로 조회할 수 있음.

------

## useRef로 관리할 수 있는 값들

- setTimeout, setInterval을 통해서 만들어진 id
- 외부 라이브러리를 사용하여 생성된 인스턴스
- scroll 위치

------

## 참고 자료

- https://react.vlpt.us/basic/12-variable-with-useRef.html

------