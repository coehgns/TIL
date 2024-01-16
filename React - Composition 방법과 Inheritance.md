# React - Composition 방법과 Inheritance

------

# Composition

- React에서 컴포지션은 여러 개의 컴포넌트를 합쳐서 새로운 컴포넌트를 만드는 것임.
- 조합 방법에 따라 컴포지션의 사용 기법이 나뉨.

------

## Composition 방법

### 1. Containment

- 하위 컴포넌트를 포함하는 형태의 합성 방법
- children이라는 props을 사용해서 조합함.

```jsx
// children props을 사용한 FancyBorder 컴포넌트 

function FancyBorder(props) {
    return (
    <div className={'FancyBorder FancyBorder=' + props.color}>
	        {props.children}
	  </div>
    );
}
```

- children이라는 프랍은 React에서 기본적으로 제공해줌.

### 2. Specialization

- 범용적인 개념을 구별이 되게 구체화 되는것.
- 객체지향 언어에서는 상속(Inheritance)을 사용하여 Specailization을 구현함.
- 리액트에서는 합성(Composition)을 사용하여 Specailiztion을 구현함.

------

## Inheritance

- 다른 컴포넌트로부터 상속을 받아서 새로운 컴포넌트를 만드는 것.

------

## 참고 자료

- https://www.inflearn.com/course/lecture?courseSlug=처음-만난-리액트&unitId=113239

------