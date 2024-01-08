# React - 댓글 컴포넌트 만들기

------

```jsx
// 댓글 컴포넌트

import React from "react";

function Comment(props) {
    return (
        <div>
            <h1>제가 만든 첫 컴포넌트입니다.</h1>
        </div>
    );
}

export default Comment;
// 댓글 목록 컴포넌트

import React from "react";
import Comment from "./Comment";

function CommentList(props) {
    return (
        <div>
            <Comment />
        </div>
    );
}

export default CommentList;
```

------

### Comment 컴포넌트에 스타일 입히기

```jsx
// 스타일 입히기

import React from "react";

const styles = {
    wrapper: {
        margin: 8,
        padding: 8,
        display: "flex",
        flexDeirection: "row",
        border: "1px solid grey",
        borderRadius: 16,
    },
    imageContainer: {},
    image: {
        width: 50,
        height: 50,
        borderRadius: 25,
    },
    contentContainer: {
        marginLeft: 8,
        display: "flex",
        flexDirection: "column",
        justifyContent: "center",
    },
    nameText: {
        color: "black",
        fontSize: 16,
        fontWeiht: "bold",
    },
    commentText: {
        color: "black",
        fontSize: 16,
    },
};
function Comment(props) {
    return (
        <div style={styles.wrapper}>
            <div style={styles.imageContainer}>
                <img
                src="<https://upload.wikimedia.org/wikipedia/commons/8/89/Portrait_Placeholder.png>"
                style={styles.image}
                />
            </div>

            <div style={styles.contentContainer}>
                <span style={styles.nameText}>홍길동</span>
                <span style={styles.commentText}>
                    제가 만든 첫 컴포넌트입니다.
                </span>
            </div>
        </div>
    )
    };
export default Comment;
```

------

## Component 컴포넌트에 Props 추가하기

```jsx
// 작성자, 댓글을 변경

<div style={styles.contentContainer}>
                <span style={styles.nameText}>{props.name}</span>
                <span style={styles.commentText}>{props.comment}</span>
            </div>
// comment list 컴포넌트에 props 추가

function CommentList(props) {
    return (
        <div>
            <Comment name={"홍길동"} comment={"안녕하세요."} />
            <Comment name={"이순신"} comment={"반갑습니다."} />
        </div>
    );
}
```

------

## Comment 데이터를 별도의 객체로 분리하기

```jsx
import React from "react";
import Comment from "./Comment";

const comments = [
    {
        name: "이인제",
        comment: "안녕하세요, 이인제입니다.",
    },
    {
        name: "이순신",
        comment: "리액트 재밌네요!",
    },
    {
        name: "세종대왕",
        comment: "리액트 공부 열심히!",
    },
];

function CommentList(props) {
    return (
        <div>
            {comments.map((comment) => {
                return (
                    <Comment name={comment.name} comment={comment.comment} />
                );
            })}
        </div>
    );
}

export default CommentList;
```

------

## 참고 자료

- https://www.inflearn.com/course/lecture?courseSlug=처음-만난-리액트&unitId=113273

------