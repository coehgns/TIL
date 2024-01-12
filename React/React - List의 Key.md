# React - List의 Key

------

- Key의 값은 같은 List에 있는 Elements 사이에서만 고유한 값이면 됨.

------

### key로 id를 사용하는 경우

```jsx
cosnt todoItems = todos.map((todo) =>
    <li key={todo.id}>
        {todo.text}
    </li>
);
```

- 아이디의 의미 자체가 고유한 값이므로 킷값으로 사용하기에 적합함.

------

### [ 주의 사항 ]

- map() 함수 안에 있는 Elements는 꼭 key가 필요함.

------

## 참고 자료

- https://www.inflearn.com/course/lecture?courseSlug=처음-만난-리액트&unitId=113231

------