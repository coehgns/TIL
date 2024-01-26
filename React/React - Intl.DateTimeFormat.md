# React - Intl.DateTimeFormat

------

## Intl.DateTimeFormat

- JavaScript 내장 라이브러리로, 날짜를 다양한 언어와 지역에 맞게 표현할 수 있음.

```jsx
// React에서 Intl.DateTimeFormat을 사용

const date = new Date();
const formattedDate = new Intl.DateTimeFormat('ko-KR', {
  year: 'numeric',
  month: 'long',
  day: 'numeric',
  hour: 'numeric',
  minute: 'numeric',
  second: 'numeric',
}).format(date);

return <div>{formattedDate}</div>;
```

------

## 참고 자료

- https://steemit.com/hive-101145/@realmankwon/react

------