# React - arrow function

------

# arrow function

- arrow function은 화살표 기로 =>를 사용함.
- 익명 함수를 선언하여 변수에 대입하는 방법과 유사함.

```jsx
let add = (first,second) => {  // ( ) 안에 파라미터
  return first + second;       // first 더하기 second 반환
};

let add = (first,second) => first + second;   // 바로 반환

let addAndMuliple = (first,second) => ({ add: first + second, multiply: first + second});
                                              // 객체 반환
```

- ( ) 안에는 기존 함수에서 사용하던 파라미터를, => 다음 { } 안에는 return하고 싶은 내용을 적으면 됨.
- arrow function은 콜백 함수의 this 범위로 생기는 오류를 피하기 위해 bind( ) 함수를 사용하여 this 객체 전달하는 과정을 포함함. (this.bind는 쓰지 않아도 됨.)

------

## 참고 자료

- https://coding-hwije.tistory.com/30