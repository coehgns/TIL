# React - Hooks 사용하기

------

## useCounter() Custom Hook 만들기

### 코드

```jsx
// useCounter.jsx

import React, { useState } from "react";

function useCounter(initialValue) {
    const [count, setCount] = useState(initialValue);

    const increaseCount = () => setCount((count) => count + 1);
    const decreaseCount = () => setCount((count) => Math.max(count - 1, 0));

    return [count, increaseCount, decreaseCount];
}

export default useCounter;
// Accommodate.jsx

import React, { useState, useEffect } from "react";
import useCounter from "./useCounter";

const MAX_CAPACITY = 10;

function Accommodate(props) {
    const [isFull, setIsFull] = useState(false);
    const [count, increaseCount, decreaseCount] = useCounter(0);

    useEffect(() => {
        console.log("======================");
        console.log("useEffect() is called.");
        console.log('isFull: ${isFull}');
    });

    useEffect(() => {
        setIsFull(count >= MAX_CAPACITY);
        console.log('Current count value: ${count}');
    }, [count]);

    return (
        <div style={{padding: 16}}>
            <p>{`총 ${count}명 수용했습니다.`}</p>

            <button onClick={increaseCount} disabled={isFull}>
                입장
            </button>
            <button onClick={decreaseCount}>퇴장</button>

            {isFull && <p style={{ color: "red" }}>정원이 가득찼습니다.</p>}
        </div>
    );
}

export default Accommodate;
```

------

- 입장 버튼을 누르게되면 두 개의 useEffectHook이 호출되어 카운트 값이 1증가함.
- 정원이 가득 차면 isFull의 값이 true가 되므로 입장 버튼이 비활성화 되어 더 이상 버튼을 누를 수 없음.
- 퇴장 버튼을 누르게되면 두 개의 useEffectHook이 호출되어 카운트 값이 1씩 줄어듦.
- useCounterHook에서 mess.max함수를 사용하여 카운트값이 0 아래로 내려갈 수 없게 만들어 놓았기 때문에 값이 0이 되면 더 이상 useEffectHook이 호출되지 않음.

------

## 참고 자료

- https://www.inflearn.com/course/lecture?courseSlug=처음-만난-리액트&unitId=113225

------