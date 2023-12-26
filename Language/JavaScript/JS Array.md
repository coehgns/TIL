# JS Array

- 배열은 1개의 변수에 여러 개의 값을 순차적으로 저장할 때 사용함.(자바스크립트의 배열은 객체이며 유용한 내장 메소드를 포함하고 있음.)
- 배열은 Array 생성자로 생성된 Array 타입의 객체이며 프로토타입 객체는 Array.prototype임.

# 1. 배열의 생성

## 1.1 배열 리터럴

- 0개 이상의 값을 쉼표로 구분하여 대괄호로 묶음.
- 첫번째 값은 인덱스 ‘0’으로 읽을 수 있음.(존재하지 않는 요소에 접근하면 undefined를 반환함.)

```jsx
const emptyArr = [];

console.log(emptyArr[1]); // undefined
console.log(emptyArr.length); // 0

const arr = [
  'zero', 'one', 'two', 'three', 'four',
  'five', 'six', 'seven', 'eight', 'nine'
];

console.log(arr[1]);      // 'one'
console.log(arr.length);  // 10
console.log(typeof arr);  // object
const obj = {
  '0': 'zero',  '1': 'one',   '2': 'two',
  '3': 'three', '4': 'four',  '5': 'five',
  '6': 'six',   '7': 'seven', '8': 'eight',
  '9': 'nine'
};
```

- 배열 리터럴은 객체 리터럴과 달리 프로퍼티명이 없고 각 요소의 값만이 존재함.
- 객체는 프로퍼티 값에 접근하기 위해 대괄호 표기법 또는 마침표 표기법을 사용하여 프로퍼티명을 키로 사용함.
- 배열은 요소에 접근하기 위해 대괄호 표기법만을 사용하며 대괄호 내에 접근하고자 하는 요소의 인덱스를 넣어줌.(인덱스는 0부터 시작함.)

![Untitled](https://prod-files-secure.s3.us-west-2.amazonaws.com/510cd684-c9a0-45bd-b45d-b35ad6027628/64b47e37-a96e-4c2c-8de2-71024e7d0f7c/Untitled.png)

```jsx
const emptyArr = [];
const emptyObj = {};

console.dir(emptyArr.__proto__);
console.dir(emptyObj.__proto__);
```

![Untitled](https://prod-files-secure.s3.us-west-2.amazonaws.com/510cd684-c9a0-45bd-b45d-b35ad6027628/bc02014d-f223-45cc-8638-db6a64b3f269/Untitled.png)

- 자바스크립트 배열은 어떤 데이터 타입의 조합이라도 포함할 수 있음.

```jsx
const misc = [
  'string',
  10,
  true,
  null,
  undefined,
  NaN,
  Infinity,
  ['nested array'],
  { object: true },
  function () {}
];

console.log(misc.length); // 10
```

## 1.2 Array() 생성자 함수

- 배열은 일반적으로 배열 리터럴 방식으로 생성하지만 배열 리터럴 방식도 결국 내장 함수 Array() 생성자 함수로 배열을 생성하는 것을 단순화시킨 것임.
- Array() 생성자 함수는 매개변수의 갯수에 따라 다르게 동작함.
- 매개변수가 1개이고 숫자인 경우 매개변수로 전달된 숫자를 length 값으로 가지는 빈 배열을 생성함.

```jsx
const arr = new Array(2);
console.log(arr); // (2) [empty × 2]
```

- 그 외의 경우 매개변수로 전달된 값들을 요소로 가지는 배열을 생성함.

```jsx
const arr = new Array(1, 2, 3);
console.log(arr); // [1, 2, 3]
```

# 2. 배열 요소의 추가와 삭제

## 2.1 배열 요소의 추가

- 배열은 동적으로 요소를 추가할 수 있음.
- 이때 순서에 맞게 값을 할당할 필요는 없고 인덱스를 사용하여 필요한 위치에 값을 할당함.
- 배열의 길이는 마지막 인덱스를 기준으로 산정.

```jsx
const arr = [];
console.log(arr[0]); // undefined

arr[1] = 1;
arr[3] = 3;

console.log(arr); // (4) [empty, 1, empty, 3]
console.log(arr.length); // 4
```

- 존재하지 않는 요소를 참조하면 undefined가 반환됨.

```jsx
// 값이 할당되지 않은 인덱스 위치의 요소는 생성되지 않는다.
console.log(Object.keys(arr)); // [ '1', '3' ]

// arr[0]이 undefined를 반환한 이유는 존재하지 않는 프로퍼티에 접근했을 때 undefined를 반환하는 것과 같은 이치다.
console.log(arr[0]); // undefined
```

## 2.2 배열 요소의 삭제

- 배열은 객체이기 때문에 배열의 요소를 삭제하기 위해 delete 연산자를 사용할 수 있음.(length 변함X.)
- 해당 요소를 완전히 삭제하여 length에도 반영되게 하기 위해서는 Array.prototype.splice 메소드를 사용함.

# 3. 배열의 순회

- 객체의 프로퍼티를 순회할 대 for…in 문을 사용함.
- for…in 문을 사용하면 배열 요소뿐만 아니라 불필요한 프로퍼티까지 출력될 수 있고 요소들의 순서를 보장하지 않으므로 배열을 순회하는데 적합하지 않음.
- 배열의 순회에는 forEach 메소드, for 문, for…of 문을 사용하는 것이 좋음.

# 4. Array Property

## 4.1 Array.length

- length 프로퍼티는 요소의 개수(배열의 길이)를 나타냄.(배열 인덱스는 32bit 양의 정수로 처리됨.)

```jsx
const arr = [1, 2, 3, 4, 5];
console.log(arr.length); // 5

arr[4294967294] = 100;
console.log(arr.length); // 4294967295
console.log(arr); // (4294967295) [1, 2, 3, 4, 5, empty × 4294967289, 100]

arr[4294967295] = 1000;
console.log(arr.length); // 4294967295
console.log(arr); // (4294967295) [1, 2, 3, 4, 5, empty × 4294967289, 100, 4294967295: 1000]
```

- 배열 요소의 개수와 length 프로퍼티의 값이 반드시 일치하지 않음.

------

- 배열 요소의 개수와 length 프로퍼티의 값이 일치하지 않는 배열을 **희소 배열**(sparse array)이라 함.
- 희소 배열은 배열ㅇ의 요소 개수보다 length 프로퍼티의 값이 언제나 큼.
- 희소 배열은 일반 배열보다 느리며 메모리를 낭비함.

------

- 현재 length 프로퍼티 값보다 더 큰 인덱스로 요소를 추가하면 새로운 요소를 추가할 수 있도록 자동으로 length 프로퍼티의 값이 늘어남.(length 프로퍼티의 값은 가장 큰 인덱스에 1을 더한 것과 같음.)

------

```jsx
const arr = [];
console.log(arr.length); // 0

arr[1000] = true;

console.log(arr);        // (1001) [empty × 1000, true]
console.log(arr.length); // 1001
console.log(arr[0]);     // undefined
```

- length 프로퍼티의 값은 명시적으로 변경할 수 있음.
- 만약 length 프로퍼티의 값을 현재보다 작게 변경하면 변경된 length 프로퍼티의 값보다 크거나 같은 인덱스에 해당하는 요소는 모두 삭제됨.

------

```jsx
const arr = [ 1, 2, 3, 4, 5 ];

// 배열 길이의 명시적 변경
arr.length = 3;
console.log(arr); // (3) [1, 2, 3]
```

# 5.Array Method

- ✏️ 메소드는 this(원본 배열)를 변경함.
- 🔒 메소드는 this를 변경하지 않음.

## 5.1 ***\*Array.isArray(arg: any): boolean\****

- 정적 메소드 Array.isArray는 주어진 인수가 배열이면 true, 배열이 아니면 false를 반환함.

## 5.2 Array.from

- Array.from 메소드는 유사 배열 객체 또는 이터러블 객체를 변환하여 새로운 배열을 생성함.

## 5.3 Array.of

- Array.of 메소드는 전달된 인수를 요소로 갖는 배열을 생성함.
- Array.of는 Array 생성자 함수와 다르게 전달된 인수가 1개이고 숫자이더라도 인수를 요소로 갖는 배열을 생성함.

## ***\*5.4 Array.prototype.indexOf(searchElement: T, fromIndex?: number): number 🔒\****

- 원본 배열에서 인수로 전달된 요소를 검색하여 인덱스를 반환함.
  - 중복되는 요소가 있는 경우 첫번째 인덱스를 반환함.
  - 해당하는 요소가 없는 경우 -1을 반환함.
- indexOf 메소드는 배열에 요소가 존재하는지 여부를 확인할 때 유용함.

## ***\*5.5 Array.prototype.concat(…items: Array<T[] | T>): T[] 🔒\****

- 인수로 전달된 값들을 원본 배열의 마지막 요소로 추가한 새로운 배열을 반환함.
- 인수로 전달한 값이 배열인 경우 배열을 해체하여 새로운 배열의 요소로 추가함.(원본 배열 변경X.)

## ***\*5.6 Array.prototype.join(separator?: string): string 🔒\****

- 원본 배열의 모든 요소를 문자열로 변환한 후, 인수로 전달받은 값(구분자)로 연결한 문자열을 반환함.
- 구분자는 생략 가능하며 기본 구분자는 , 임.

## ***\*5.7 Array.prototype.push(…items: T[]): number ✏️\****

- 인수로 전달받은 모든 값을 원본 배열의 마지막에 요소로 추가하고 변경된 length 값을 반환함.
- push 메소드는 원본 배열을 직접 변경함.

------

- push 메소드와 concat 메소드는 유사하게 동작하지만 미묘한 차이가 있음.
  - push 메소드는 원본 배열을 직접 변경하지만 concat 메소드는 원본 배열을 변경하지 않고 새로운 배열을 반환.

------

- 인수로 전달 받은 값이 배열인 경우, push 메소드는 배열을 그대로 원본 배열의 마지막 요소로 추가하지만 concat 메소드는 배열을 해체하여 새로운 배열의 마지막 요소로 추가함.

------

- push 메소드는 원본 배열을 직접 변경하는 부수 효과가 있음.

## ***\*5.8 Array.prototype.pop(): T | undefined ✏️\****

- 원본 배열에서 마지막 요소를 제거하고 제거한 요소를 반환함.
- 원본 배열이 빈 배열이면 undefined를 반환함.(pop 메소드는 원본 배열을 직접 변경함.

------

- pop 메소드와 push 메소드를 사용하면 스택을 쉽게 구현할 수 있음.

## ***\*5.9 Array.prototype.reverse(): this ✏️\****

- 배열 요소의 순서를 반대로 변경함.(원본 배열이 변경됨. 반환값은 변경된 배열임.)

## ***\*5.10 Array.prototype.shift(): T | undefined ✏️\****

- 배열의 첫요소를 제거하고 제거한 요소를 반환함.(빈 배열일 경우 undefined를 반환함.)
- shift 메소드는 대상 배열 자체를 변경함.

------

- shift는 push와 함께 배열을 큐(FIFO: Fristh In First Out)처럼 동작하게 함.

------

- Array.prototype.pop()은 마지막 요소를 제거하고 제거한 요소를 반환함.

![Untitled](https://prod-files-secure.s3.us-west-2.amazonaws.com/510cd684-c9a0-45bd-b45d-b35ad6027628/2f762be4-9132-4d76-80a1-d3e307a07a6a/Untitled.png)

## ***\*5.11 Array.prototype.slice(start=0, end=this.length): T[] 🔒\****

- 인자로 지정된 배열의 부분을 복사하여 반환함.(원본 배열 변경X.)
- 첫번째 매개변수 start에 해당하는 인덱스를 갖는 요소부터 매개변수 end에 해당하는 인덱스를 가진 요소 전까지 복사됨.

------

- 매개변수
  - start
    - 복사를 시작할 인텍스. 음수인 경우 배열의 끝에서의 인덱스를 나타냄.
  - end
    - 옵션이며 기본값은 length 값임.

![Untitled](https://prod-files-secure.s3.us-west-2.amazonaws.com/510cd684-c9a0-45bd-b45d-b35ad6027628/b680e946-5dab-49aa-a2be-46ebcf61ac57/Untitled.png)

- slice 메소드에 인자를 전달하지 않으면 원본 배열의 복사본을 생성하여 반환함.

------

- 원본 배열의 각 요소를 얕은 복사(shallow copy)하여 새로운 복사본을 생성함.
- Spread 문법과 Object.assign는 원본을 shallow copy함.
- 이를 이용하여 유사 배열 객체를 배열로 변환할 수 있음.

## ***\*5.12 Array.prototype.splice(start: number, deleteCount=this.length-start, …items: T[]): T[] ✏️\****

- 기존의 배열의 요소를 제거하고 그 위치에 새로운 요소를 추가함.(배열 중간에 새로운 요소를 추가할 때도 사용됨.)

------

- 매개변수
  - start
    - 배열에서의 시작 위치임. start 만을 지정하면 배열의 start 부터 모든 요소를 제거함.
  - deleteCount
    - 시작 위치부터 제거할 요소의 수임.(deleteCount가 0인 경우 아무런 요소도 제거되지 않음.)
  - items
    - 삭제한 위치에 추가될 요소들임.(아무런 요소도 지정하지 않을 경우 삭제만 함.)
- 반환값 삭제한 요소들을 가진 배열임,

------

![Untitled](https://prod-files-secure.s3.us-west-2.amazonaws.com/510cd684-c9a0-45bd-b45d-b35ad6027628/1f697395-ebf3-4237-a1f7-30297456a7c0/Untitled.png)

- 배열에서 요소를 제거하고 제거한 위치에 다른 요소를 추가.

![Untitled](https://prod-files-secure.s3.us-west-2.amazonaws.com/510cd684-c9a0-45bd-b45d-b35ad6027628/956eadb7-4adc-4638-995d-f800ae91a717/Untitled.png)

- 배열 중간에 새로운 요소를 추가할 때와 배열 중간에 배열의 요소들을 해체하여 추가할 때 사용됨.