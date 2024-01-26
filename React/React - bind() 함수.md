# React - bind() 함수

------

# bind()

- 함수.bind(this될 변수);
- React에서 바인딩은 컴포넌트 - 이벤트메소드 사이를 연결하는 방법임.
- bind는 ‘함수를 반환’한다는 특징이 있음.
- bind()는 렌더 함수 안에서 컴포넌트인 자기자신 this를 가리킴.
- bind()를 사용 후 다시 호출을 해줘야 함수 속 this를 원하는 객체로 지정한 후 값을 얻을 수 있음.

```jsx
var obj = {name:'james'};   // obj 변수 정의

function bindTest() {  // bindTest 함수 정의
        console.log(this.name);
}
bindTest();   // this가 뭔지 몰라 undefined됨.

var bindTest2 = bindTest.bind(obj);  // bind()를 사용해서 bindTest() 에서 this는 obj가 됨.

bindTest2();  // 다시 한번 호출. this.name === obj.name 이므로 james가 출력됨.
```

------

## 참고 자료

- https://devbirdfeet.tistory.com/14