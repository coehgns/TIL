<<<<<<< HEAD
# React - Card 컴포넌트 만들기

------

```jsx
// Crad.jsx

function Card(props) {
    const { title, backgroundColor, children } = props;

    return (
        <div 
            style={{
                margin: 8,
                padding: 8,
                borderRadius: 8,
                boxShadow: "0px 0px 4px grey",
                backgroundColor: backgroundColor || "white",
            }}
        >
            {title && <h1>{title}</h1>}
            {children}
        </div>
    );
}

export default Card;
```

- 카드 컴포넌트는 하위 컴포넌트를 감싸서 카드 형태로 보여주는 컴포넌트임.
- children을 사용한 부분이 containment이고 title과 background를 사용한 부분이 specialization임.

------

## 참고 자료

- https://www.inflearn.com/course/lecture?courseSlug=처음-만난-리액트&unitId=113240

=======
# React - Card 컴포넌트 만들기

------

```jsx
// Crad.jsx

function Card(props) {
    const { title, backgroundColor, children } = props;

    return (
        <div 
            style={{
                margin: 8,
                padding: 8,
                borderRadius: 8,
                boxShadow: "0px 0px 4px grey",
                backgroundColor: backgroundColor || "white",
            }}
        >
            {title && <h1>{title}</h1>}
            {children}
        </div>
    );
}

export default Card;
```

- 카드 컴포넌트는 하위 컴포넌트를 감싸서 카드 형태로 보여주는 컴포넌트임.
- children을 사용한 부분이 containment이고 title과 background를 사용한 부분이 specialization임.

------

## 참고 자료

- https://www.inflearn.com/course/lecture?courseSlug=처음-만난-리액트&unitId=113240

>>>>>>> 88752f10985abb553e5666fa10794057c19770e8
------