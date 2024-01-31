# TypeScript - 정의와 장점

------

# 타입스크립트란?

- 자바스크립트에서 타입을 부여한 언어 (자바스크립트의 확장된 언어)
- 타입스크립트는 자바스크립트와 다르게 브라우저에서 실행하기 위해 파일을 변환해주어야 함.(변환 과정을 컴파일이라고 함.)

------

# 타입스크립트의 장점

- 함수 타입을 직접 정의하여 에러를 최소화 시킬 수 있음.
- 내가 지정한 타입의 api 리스트를 제공해줌.
- 오탈자를 방지함.

```jsx
function add(a:number, b: number) :number {
return a+b;
}
add(10,20);
```

- function add(a:number, b: number) :number = function 함수명(속성: 타입, 속성: 타입): 반환 될 타입. 직접 함수 타입을 정의해줌으로써 자바스크립트처럼 PropTypes 없어도 됨.
- add를 호출해 줄 때는 파라미터 안에 들어있는 타입들과 일치하게 호출해줘야 함.
- result라는 변수를 만들고 result를 불러올 때 . 만 찍어도 number에 관한 api 리스트가 나옴.
- api 리스트 중에서 toloca만 치고 tap키를 누르면 자동완성으로 toLocalString 키워드가 완벽하게 입력됨.
- 타입스크립트는 알아서 자동완성 기능이 있기 때문에 오탈자 방지를 할 수 있음.

------

## 참고 자료

- https://1eemember.tistory.com/2