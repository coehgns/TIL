<<<<<<< HEAD
# React - 로그인 여부를 나타내는 툴바 만들기

------

```jsx
// Toolbar.jsx

import React from "react";

const styles = {
    wrapper: {
        padding: 16,
        display: "flex",
        flexDirection: "row",
        borderBottom: "1px solid grey",
    },
    greeting: {
        marginRight: 8,
    },
};

function Toolbar(props) {
    const { isLoggedIn, onClickLogin, onClickLogout } = props;

    return (
        <div style={styles.wrapper}>
            {isLoggedIn && <span style={styles.greeting}>환영합니다!</span>}

            {isLoggedIn ? (
                <button onClick={onClickLogout}>로그아웃</button>
            ) : (
                <button onClick={onClickLogin}>로그인</button>
            )}
        </div>
    );
}

export default Toolbar;
// landingpage.jsx

import React, { useState } from "react";
import Toolbar from "./Toolbar";

function LandingPage(props) {
    const [isLoggedIn, setIsloggedIn] = useState(false);

    const onClickLogin = () => {
        setIsloggedIn(true);
    };

    const onClickLogout = () => {
        setIsloggedIn(false);
    };

    return (
        <div>
            <Toolbar
                isLoggedIn={isLoggedIn}
                onClickLogin={onClickLogin}
                onClickLogout={onClickLogout}
            />
            <div style={{ padding: 16}}>리액트 공부!</div>
        </div>
    );
}

export default LandingPage;
```

- 로그인 버튼을 누르면 로그인 상태가 true로 바뀌기 때문에 환영 메시지가 표시되고 로그아웃 버튼이 나옴.
- 로그아웃 버튼을 누르면 처음처럼 돌아감.

------

## 참고 자료

=======
# React - 로그인 여부를 나타내는 툴바 만들기

------

```jsx
// Toolbar.jsx

import React from "react";

const styles = {
    wrapper: {
        padding: 16,
        display: "flex",
        flexDirection: "row",
        borderBottom: "1px solid grey",
    },
    greeting: {
        marginRight: 8,
    },
};

function Toolbar(props) {
    const { isLoggedIn, onClickLogin, onClickLogout } = props;

    return (
        <div style={styles.wrapper}>
            {isLoggedIn && <span style={styles.greeting}>환영합니다!</span>}

            {isLoggedIn ? (
                <button onClick={onClickLogout}>로그아웃</button>
            ) : (
                <button onClick={onClickLogin}>로그인</button>
            )}
        </div>
    );
}

export default Toolbar;
// landingpage.jsx

import React, { useState } from "react";
import Toolbar from "./Toolbar";

function LandingPage(props) {
    const [isLoggedIn, setIsloggedIn] = useState(false);

    const onClickLogin = () => {
        setIsloggedIn(true);
    };

    const onClickLogout = () => {
        setIsloggedIn(false);
    };

    return (
        <div>
            <Toolbar
                isLoggedIn={isLoggedIn}
                onClickLogin={onClickLogin}
                onClickLogout={onClickLogout}
            />
            <div style={{ padding: 16}}>리액트 공부!</div>
        </div>
    );
}

export default LandingPage;
```

- 로그인 버튼을 누르면 로그인 상태가 true로 바뀌기 때문에 환영 메시지가 표시되고 로그아웃 버튼이 나옴.
- 로그아웃 버튼을 누르면 처음처럼 돌아감.

------

## 참고 자료

>>>>>>> 88752f10985abb553e5666fa10794057c19770e8
- https://www.inflearn.com/course/lecture?courseSlug=처음-만난-리액트&unitId=113228