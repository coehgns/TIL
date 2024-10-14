<<<<<<< HEAD
# React - 사용자 정보 입력 받기

## SignUp 컴포넌트

```jsx
import React, { useState } from "react";

function SignUp(props) {
    const [name, setName] = useState("");

    const handleChangeName = (event) => {
        setName(event.target.value);
    };

    const handleSubmit = (event) => {
        alert (`이름:  ${name}`);
        event.preventDefault();
    };

    return (
        <form onSubmit={handleSubmit}>
            <lable>
                이름:
                <input type="text" value={name} onChange={handleChangeName} />
            </lable>
            <button type="submit">제출</button>
        </form>
    );
}

export default SignUp;
```

- signup 컴포넌트는 이름을 입력할 수 있는 input 태그와 입력된 값을 저장하기 위한 name이라는 state를 가지고 있음.
- 단순한 형태의 입력 양식 컴포넌트임.

------

### SignUp 컴포넌트에 성별 필드 추가하기

```jsx
import React, { useState } from "react";

function SignUp(props) {
    const [name, setName] = useState("");
    const [gender, setGender] = useState("남자");

    const handleChangeName = (event) => {
        setName(event.target.value);
    };

    const handleChangeGender = (event) => {
        setGender(event.target.value);
    };

    const handleSubmit = (event) => {
        alert (`이름:  ${name}, 성별: ${gender}`);
        event.preventDefault();
    };

    return (
        <form onSubmit={handleSubmit}>
            <lable>
                이름:
                <input type="text" value={name} onChange={handleChangeName} />
            </lable>
            <br />
            <label>
                성별:
                <select value={gender} onChange={handleChangeGender}>
                    <option value="남자">남자</option>
                    <option value="여자">여자</option>
                </select>
            </label>
            <button type="submit">제출</button>
        </form>
    );
}

export default SignUp;
```

- 젠더라는 이름의 state가 추가되었고 성별을 입력받기 위한 select 태그가 추가됨.
- select 태그에는 select 태그의 값이 변경되면 처리하기 위해 handleChangeGender라는 이벤트 핸들러를 만들어서 사용함.

------

## 참고 자료

- https://www.inflearn.com/course/lecture?courseSlug=처음-만난-리액트&unitId=113235

=======
# React - 사용자 정보 입력 받기

## SignUp 컴포넌트

```jsx
import React, { useState } from "react";

function SignUp(props) {
    const [name, setName] = useState("");

    const handleChangeName = (event) => {
        setName(event.target.value);
    };

    const handleSubmit = (event) => {
        alert (`이름:  ${name}`);
        event.preventDefault();
    };

    return (
        <form onSubmit={handleSubmit}>
            <lable>
                이름:
                <input type="text" value={name} onChange={handleChangeName} />
            </lable>
            <button type="submit">제출</button>
        </form>
    );
}

export default SignUp;
```

- signup 컴포넌트는 이름을 입력할 수 있는 input 태그와 입력된 값을 저장하기 위한 name이라는 state를 가지고 있음.
- 단순한 형태의 입력 양식 컴포넌트임.

------

### SignUp 컴포넌트에 성별 필드 추가하기

```jsx
import React, { useState } from "react";

function SignUp(props) {
    const [name, setName] = useState("");
    const [gender, setGender] = useState("남자");

    const handleChangeName = (event) => {
        setName(event.target.value);
    };

    const handleChangeGender = (event) => {
        setGender(event.target.value);
    };

    const handleSubmit = (event) => {
        alert (`이름:  ${name}, 성별: ${gender}`);
        event.preventDefault();
    };

    return (
        <form onSubmit={handleSubmit}>
            <lable>
                이름:
                <input type="text" value={name} onChange={handleChangeName} />
            </lable>
            <br />
            <label>
                성별:
                <select value={gender} onChange={handleChangeGender}>
                    <option value="남자">남자</option>
                    <option value="여자">여자</option>
                </select>
            </label>
            <button type="submit">제출</button>
        </form>
    );
}

export default SignUp;
```

- 젠더라는 이름의 state가 추가되었고 성별을 입력받기 위한 select 태그가 추가됨.
- select 태그에는 select 태그의 값이 변경되면 처리하귀 위해 handleChangeGender라는 이벤트 핸들러를 만들어서 사용함.

------

## 참고 자료

- https://www.inflearn.com/course/lecture?courseSlug=처음-만난-리액트&unitId=113235

>>>>>>> 88752f10985abb553e5666fa10794057c19770e8
------