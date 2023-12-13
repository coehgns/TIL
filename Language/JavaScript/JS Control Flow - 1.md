# JS Control Flow - 1

- 제어문은 주어진 조건에 따라 코드 블록을 실행하거나 반복 실행할 때 사용함.

# 1. 블록문

- 블록문은 0개 이상의 문들을 중괄호로 묶은 것으로 코드 블록 또는 블록이라고 부르기도 함.
- 블록문은 문의 끝에 세미 콜론(;)을 붙이지 않음.

```jsx
// 블록문
{
  var foo = 10;
  console.log(foo);
}

// 제어문
var x = 0;
while (x < 10) {
  x++;
}
console.log(x); // 10

// 함수 선언문
function sum(x, y) {
  return x + y;
}
console.log(sum(1, 2)); // 3
```

# 2. 조건문

- 조건문은 주어진 조건식의 평가 결과에 따라 코드 블럭의 실행을 결정함.(조건식은 불리언 값으로 평가될 수 있는 표현식임.)

## 2.1 if..else 문

- if…else 문은 주어진 조건식의 논리적 참, 거짓에 따라 실행할 코드 블로글 결정함.
- 만약 조건식의 평가 결과가 불리언 값이 아니면 불리언 값으로 갈제 변환되어 구별함.

```jsx
if (조건식) {
  // 조건식이 참이면 이 코드 블록이 실행된다.
} else {
  // 조건식이 거짓이면 이 코드 블록이 실행된다.
}
```

- 조건식의 평과 결과가 참일 경우 if 문 다음의 코드 블록이 실행됨. 거짓일 경우 else 문 다음의 코드 블록이 실행됨.
- 조건식을 추가하고 싶으면 else if 문을 사용하면 됨.

```jsx
if (조건식1) {
  // 조건식1이 참이면 이 코드 블록이 실행된다.
} else if (조건식2) {
  // 조건식2이 참이면 이 코드 블록이 실행된다.
} else {
  // 조건식1과 조건식2가 모두 거짓이면 이 코드 블록이 실행된다.
}
```

- else if 문과 else 문은 옵션으로 사용할 수도 있고 사용하지 않을 수도 있음.(if 문과 else 문은 2번 이상 사용할 수 없지만 else if 문은 여러 번 사용할 수도 있음.)
- 만약 코드 블록 내의 문이 하나뿐이라면 중괄호를 생략할 수도 있음.

```jsx
var num = 2;
var kind;

if (num > 0)      kind = '양수';
else if (num < 0) kind = '음수';
else              kind = '영';

console.log(kind); // 양수
```

- 대부분의 if…else문은 삼향 조건 연산자로 바꿔쓸 수 있음.

```jsx
// x가 짝수이면 ‘짝수'를 홀수이면 ‘홀수'를 반환한다.
var x = 2;
var result;

if (x % 2) { // 2 % 2는 0이고 0은 false로 취급된다.
  result = '홀수';
} else {
  result = '짝수';
}

console.log(result); // 짝수
```

- 위 예제를 삼항 조건 연산자로.

```jsx
// x가 짝수이면 '짝수'를 홀수이면 '홀수'를 반환한다.
var x = 2;

// 0은 false로 취급된다.
var result = x % 2 ? '홀수' : '짝수';
console.log(result); // 짝수
```

- 세가지 경우의 수를 갖는 경우

```jsx
var num = 2;

// 0은 false로 취급된다.
var kind = num ? (num > 0 ? '양수' : '음수') : '영';
console.log(kind); // 양수
```

## 2.2 switch 문

- switch 문은 switch 문의 표현식을 평가하여 그 값과 일치하는 표현식을 갖는 case 문으로 실행 순서를 이동시킴.
- case 문은 상황을 의미하는 표현식을 지정하고 콜론으로 마친 뒤 실행할 문들을 위치시킴.
- case문이 없다면 실행 순서는 default문으로 이동함.

```jsx
CODE
switch (표현식) {
  case 표현식1:
    switch 문의 표현식과 표현식1이 일치하면 실행될 문;
    break;
  case 표현식2:
    switch 문의 표현식과 표현식2가 일치하면 실행될 문;
    break;
  default:
    switch 문의 표현식과 일치하는 표현식을 갖는 case 문이 없을 때 실행될 문;
}
```

- if…else 문의 조건식은 반드시 불리언 값으로 평가되지만 switch 문의 표현식은 불리언 값보다는 문자열, 숫자 값이 경우가 많음.
- switch 문의 표현식, 변수 month의 평가 결과인 숫자 값 11과 일치하는 case 문으로 실행 순서가 이동함.

```jsx
// 월을 영어로 변환한다. (11 → 'November')
var month = 11;
var monthName;

switch (month) {
  case 1:
    monthName = 'January';
  case 2:
    monthName = 'February';
  case 3:
    monthName = 'March';
  case 4:
    monthName = 'April';
  case 5:
    monthName = 'May';
  case 6:
    monthName = 'June';
  case 7:
    monthName = 'July';
  case 8:
    monthName = 'August';
  case 9:
    monthName = 'September';
  case 10:
    monthName = 'October';
  case 11:
    monthName = 'November';
  case 12:
    monthName = 'December';
  default:
    monthName = 'Invalid month';
}

console.log(monthName); // Invalid month
```

- 문을 실행한 후 switch 문을 탈출하지 않고 switch 문이 끝날 때까지 모든 case 문과 default 문을 실행했기 때문에 November가 출력되지 않고 Invalid month가 출력됨.
- case 문에 해당하는 문의 마지막에 break 문을 사용하면 됨.

```jsx
// 월을 영어로 변환한다. (11 → 'November')
var month = 11;
var monthName;

switch (month) {
  case 1:
    monthName = 'January';
    break;
  case 2:
    monthName = 'February';
    break;
  case 3:
    monthName = 'March';
    break;
  case 4:
    monthName = 'April';
    break;
  case 5:
    monthName = 'May';
    break;
  case 6:
    monthName = 'June';
    break;
  case 7:
    monthName = 'July';
    break;
  case 8:
    monthName = 'August';
    break;
  case 9:
    monthName = 'September';
    break;
  case 10:
    monthName = 'October';
    break;
  case 11:
    monthName = 'November';
    break;
  case 12:
    monthName = 'December';
    break;
  default:
    monthName = 'Invalid month';
}

console.log(monthName); // November
```

- default 문에는 break 문을 생략하는 것이 일반적임.