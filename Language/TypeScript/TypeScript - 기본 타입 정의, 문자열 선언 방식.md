# TypeScript - 기본 타입 정의, 문자열 선언 방식

---

## 변수 & 함수의 타입 정의

| Boolean : 논리형 | Number : 숫자형 | String : 문자형    | Object : 객체        |
| ---------------- | --------------- | ------------------ | -------------------- |
| Array : 배열     | Tuple : 튜플    | Enum : 이넘        | Any : 모든 타입 가능 |
| Void : 반환타입  | Null : 0        | Undefined : 정의 x | Never                |

### 예시

```tsx
// 문자열
let str:string = 'hello';

// 숫자
let num:number = 10;

// 배열
let arr:Array<number> = [1,2,3];
//Array는 첫 글자가 대문자여야 됨.
//<>괄호에는 어떤 타입만 들어올 수 있는지 선언.

let heroes:Array<string> = ['Capt', 'Thor', 'Hulk', 10];
//문자열 타입에 숫자 10이 들어오면 에러 발생.

let items: number[] = [1,2,3];
//[]는 배열 리터럴이란 뜻. []괄호 앞에 number라는 타입을 지정

// 튜플
let address01: [string,number] = ['gangnam',100];
//배열의 각각 인덱스에 타입이 정의됨.

//Object
let obj: object = {};
let person01: object = {
  name:'capt',
  age:100
}
//객체 속성은 어떤 타입이 들어오던 신경X

let person: {name: string, age:number } = {
  name: 'thor',
  age: 1000
}
// 각 인자마다 타입을 지정해주면 이렇게 객체 함수를 나타낼 수 있음.

// boolean 진위값
let show: boolean = true;
```

## 문자열 선언방식

```tsx
// 일반 JS 문자열 선언방식
var str = 'hello';

//TS 문자열 선언방식
let str: string = 'hello';
```

### 함수에 타입을 정의하는 방식

```tsx
// JS
function sum(a,b) {
  return a+b;
}

sum(10,20,30,40,50);

// TS
function sumb3(a:number, b: number): number {
  return a+b;
}

sum(10,20,30,40,50);
```

- JS의 경우 파라미터 값이 2개여도 30,40,50은 자동으로 무시해줌.
- TS의 경우 30,40,50에 에러밑줄이 생기는데 TS가 JS에 비해 파라미터를 엄격하게 체크하기 때문임.
- 인자 갯수보다 sum 파라미터 인자 갯수가 적을 경우에도 에러가 남. 파라미터 인자 갯수와 리턴되는 인자 갯수가 비례해야 됨.

---

## 참고 자료

- https://1eemember.tistory.com/4

---