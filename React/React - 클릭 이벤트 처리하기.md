# React - 클릭 이벤트 처리하기

------

```jsx
// ConfirmButton.jsx

import React from "react";

class ConfirmButton extends React.Component {
    constructor(props) {
        super(props);

        this.state = {
            isConfirmed: false,
        };

        this.handleConfirm = this.handleConfirm.bind(this);
    }

    handleConfirm() {
        this.setState((prevState) => ({
            isConfirmed: !prevState.isConfirmed,
        }));
    }

    render() {
        return (
            <button
              onClick={this.handleConfirm}
              disabled={this.state.isConfirmed}
            >
              {this.state.isConfirmed ? "확인됨" : "확인하기"}
            </button>
        );
    }
}

export default ConfirmButton;
```

- 화면에 나오는 확인 버튼을 누르면 클릭 이벤트가 핸들러로 전달되고 isConfirmed의 값이 true로 바뀌면서 버튼이 “확인됨”이라는 버튼으로 비활성화 됨.

------

## Class fields syntax 사용하기

```jsx
// 수정한 ConfirmButton.jsx

import React from "react";

class ConfirmButton extends React.Component {
    constructor(props) {
        super(props);

        this.state = {
            isConfirmed: false,
        };
    }

    handleConfirm = () => {
        this.setState((prevState) => ({
            isConfirmed: !prevState.isConfirmed,
        }));
    }

    render() {
        return (
            <button
              onClick={this.handleConfirm}
              disabled={this.state.isConfirmed}
            >
              {this.state.isConfirmed ? "확인됨" : "확인하기"}
            </button>
        );
    }
}

export default ConfirmButton;
```

- 컨스트럭터에 있는 바인드 코드를 제거함.
- 이벤트 핸들러를 arrow function을 사용하도록 수정함.
- 수정 후 다시 확인 버튼을 눌러도 이전과 결과가 같음.

------

## confirmButton 컴포넌트를 함수 컴포넌트로 변경하기

```jsx
// 함수 컴포넌트로 변경한 코드 

import React, { useState } from "react";

function ConfirmButton(props) {
    const [isConfirmed, setIsConfirmed] = useState(false);

    const handleConfirm = () => {
        setIsConfirmed((preveIsConfirmed) => !preveIsConfirmed);
    };

    return (
        <button onClick={handleConfirm} disabled={isConfirmed}>
            {isConfirmed ? "확인됨" : "확인하기"}
        </button>
    );
}

export default ConfirmButton;
```

- state는 useStateHook을 사용하여 처리함.
- eventHandler는 arrow function을 사용함.
- 이전과 동일한 결과가 나옴.

------

## 참고 자료

- https://www.inflearn.com/course/lecture?courseSlug=처음-만난-리액트&unitId=113276

------