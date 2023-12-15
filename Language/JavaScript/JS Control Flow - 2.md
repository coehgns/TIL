# JS Control Flow - 2

# 3. 반복문

- 반복문은 주어진 조건식의 평가 결과가 참이 경우 코드 블럭을 실행함.(조건식이 거짓일 때까지 반복됨.)

## 3.1 for 문

- for 문은 조건식이 거짓으로 판별될 때까지 코드 블록을 반복 실행함.

```jsx
CODE
for (초기화식; 조건식; 증감식) {
  조건식이 참이 견우 반복 실행될 문;
}
```

- for 문의 동작 과정

```jsx
for (var i = 0; i < 2; i++) {
  console.log(i);
}
```

![for-statement.png](https://prod-files-secure.s3.us-west-2.amazonaws.com/510cd684-c9a0-45bd-b45d-b35ad6027628/a2c0fe73-95fc-4777-913c-e14528acd322/for-statement.png)

- 위 예제는 i가 0으로 초기화된 상태에서 i가 2보다 작을 때까지 코드 블록을 2번 반복 실행함.
- 동작 과정

1. for 문을 실행하면 가장 먼저 초기화식 var i = 0이 실행됨.(한번만 실행됨.)
2. 초기화식의 실행이 종료되면 조건식으로 실행 순서가 이동함.(i가 0이면 조건식의 평가 결과는 true임.)
3. 조건식의 평가 결과가 true이므로 실행 순서가 코드 블록으로 이동하여 실행됨.(증감문으로 실행 순서가 이동하는 것이 아닌 코드 블록으로 실행 순서가 이동하는 것임.)
4. 코드 블록의 실행이 종료하면 증감식으로 실행 순서가 이동함.( i++이 실행되어 i는 1이됨.)
5. 증감식 실행이 종료되면 다시 조건식으로 실행 순서가 이동함.
6. 조건식의 평가 결과가 true이므로 실행 순서가 코드 블록으로 이동하여 실행됨.
7. 코드 블록의 실행이 종료하면 증감식으로 실행 순서가 이동함.(i++이 실행되어 i는 2가 됨.)
8. 증감식이 실행이 종료되면 다시 조건식으로 실행 순서가 이동함.(i가 2이므로 조건식의 결과는 false. 평가 결과가 false이므로 for 문의 실행이 종료됨.)

- 아래 예제는 위 예제를 역으로 반복하는 for문임.(i가 1로 초기화된 상태에서 시작하여 i가 0보다 같거나 커질 때까지 코드 블록을 2번 반복 실행함.)

```jsx
for (var i = 1; i >= 0; i--) {
  console.log(i);
}
```

- 어떠한 식도 선언하지 않으면 무한 루프가 됨.

```jsx
for (;;) { } // 무한루프
```

- for 문 내에 for 문을 중첩해 사용할 수 있음.

```jsx
// 두 눈의 합이 6이 되는 모든 경우의 수를 출력
for (var i = 1; i <= 6; i++) {
  for (var j = 1; j <= 6; j++) {
    if (i + j === 6) console.log(`[${i}, ${j}]`);
  }
}
```

- 출력 결과

[1, 5] [2, 4] [3, 3] [4, 2] [5, 1]

------

## 3.2 while 문

- while 문은 주어진 조건식의 평가 결과가 참이면 코드 블록을 계속해서 반복 실행함.(결과가 거짓이면 실행 종료. 결과가 불리언 값이 아니면 불리언 값으로 강제 변환되어 논리적 참, 거짓을 구별함.)

```jsx
var count = 0;

// count가 3보다 작을 때까지 코드 블록을 계속 반복 실행한다.
while (count < 3) {
  console.log(count);
  count++;
} // 0 1 2
```

- 결과가 언제나 참이면 무한루프가 됨.

```jsx
// 무한루프
while (true) { }
```

- 무한루프를 탈출하기 위해서는 탈출 조건을 if문에 부여하고 break 문으로 코드 블럭을 탈출함.

```jsx
var count = 0;

// 무한루프
while (true) {
  console.log(count);
  count++;
  // count가 3이면 코드 블록을 탈출한다.
  if (count === 3) break;
} // 0 1 2
```

## 3.3 do…while 문

- do…while 문은 코드 블록을 실행하고 조건식을 평가함.(한번 이상 실행됨.)

```jsx
var count = 0;

// count가 3보다 작을 때까지 코드 블록을 계속 반복 실행한다.
do {
  console.log(count);
  count++;
} while (count < 3); // 0 1 2
```

# 4. break 문

- break 문은 코드 블록을 탈출함.(레이블 문, 반복문 또는 switch 문의 코드 블록을 탈출.(그 이외에 break 문을 사용하면 에러가 발생함.)

```jsx
if (true) {
  break; // Uncaught SyntaxError: Illegal break statement
}
```

- 레이블 문이란 식별자가 붙은 문을 말함.`

```jsx
// foo라는 레이블 식별자가 붙은 레이블 문
foo: console.log('foo');
```

- 레이블 문은 프로그램의 실행 순서를 제어하기 위해 사용함.

```jsx
// foo라는 식별자가 붙은 레이블 블록문
foo: {
  console.log(1);
  break foo; // foo 레이블 블록문을 탈출한다.
  console.log(2);
}

console.log('Done!');
```

- 중첩된 for 문의 내부 for 문에서 break 문을 실행하면 내부 for 문을 탈출하여 외부 for 문으로 진입함.

```jsx
// outer라는 식별자가 붙은 레이블 for 문
outer: for (var i = 0; i < 3; i++) {
  for (var j = 0; j < 3; j++) {
    // i + j === 3이면 외부 for 문을 탈출한다.
    if (i + j === 3) break outer;
  }
}

console.log('Done!');
```

- break 문은 반복문을 더 이상 진행하지 않아도 될 때 불필요한 반복을 회피할 수 있어 유용함.

# 5. continue 문

- continue 문은 반복문의 코드 블록 실행을 현 지점에서 중단하고 반복문의 증감식으로 이동함.(반복문을 탈출하지는 않음.)

```jsx
// 문자열에서 특정 문자의 개수를 카운트하는 예제

var string = 'Hello World.';
var count = 0;

// 문자열은 유사배열이므로 for 문으로 순회할 수 있다.
for (var i = 0; i < string.length; i++) {
  // 'l'이 아니면 현 지점에서 실행을 중단하고 반복문의 증감식으로 이동한다.
  if (string[i] !== 'l') continue;
  count++; // continue 문이 실행되면 이 문은 실행되지 않는다.
}

console.log(count); // 3

// 참고로 String.prototype.match 메소드를 사용해도 같은 동작을 한다.
console.log(string.match(/l/g).length); // 3
```

- 위 예제의 for 문은 아래와 같이 동작함.

```jsx
for (var i = 0; i < string.length; i++) {
  // 'l'이면 카운트를 증가시킨다.
  if (string[i] === 'l') count++;
}
```

- if 문 내에서 실행해야 할 코드가 길다면 들여쓰기가 한 단계 더 깊어지므로 continue 문을 사용하는 것이 가독성이 더 좋음.

```jsx
// continue 문을 사용하지 않으면 if 문 내에 코드를 작성해야 한다.
for (var i = 0; i < string.length; i++) {
  // 'l'이면 카운트를 증가시킨다.
  if (string[i] === 'l') {
    count++;
    // code
    // code
    // code
  }
}

// continue 문을 사용면 if 문 밖에 코드를 작성할 수 있다.
for (var i = 0; i < string.length; i++) {
  // 'l'이 아니면 카운트를 증가시키지 않는다.
  if (string[i] !== 'l') continue;

  count++;
  // code
  // code
  // code
}
```