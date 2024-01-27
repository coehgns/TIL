# React - map() 함수

------

# map() 함수

- 반복되는 컴포넌트를 렌더링하기 위해 자바스크립트 배열의 내장 함수인 map()을 사용 함.
- 파라미터로 전달된 함수를 사용하여 배열 내 각 요소를 원하는 규칙에 따라 변환 후 새로운 배열을 생성함.

------

## 문법

```jsx
arr.map(callbackFunction,[thisArg]
arr.map(callbackFunction(currenValue,index,array),thisArg)
```

- callbackFunction : 새로운 배열의 요소를 생성하는 함수로서 인수를 갖음.
  - currenValue : 현재 배열 내의 값들을 의미
  - index : 현재 배열 내 값의 인덱스를 의미
  - array : 현재 배열
- thisArg(선택 항목) : callback 함수 내부에서 사용할 this 레퍼런스를 설정함.

```jsx
// 2차원 배열을 객체로 표현

import React from "react";
const App = () => {
 const names = [
  {userName:"ㅇㅇㅇ",age:19},
  {userName:"ㅇㅇㅇ",age:29},
  {userName:"ㅇㅇㅇ",age:39}
]
const nameList = names.map((v) => (<Main name={v.userName} age={v.age}/>))
return (
 <div>
  {nameList}
 </div>
 );
}
```

------

## 참고 자료

- https://goddaehee.tistory.com/303