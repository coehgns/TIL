# JS Operator

# 1. 표현식과 연산자

- 표현식은 리터럴, 식별자, 연산자, 함수 호출 등의 조합을 말함.
- 표현식은 평가되어 하나의 값을 만듦.(표현식은 하나의 값으로 평가될 수 있는 문임.)
- 표현식은 여러 표현식으로 나누어 볼 수 있지만 결국 평가되어 하나의 값을 만든다는 점에서 모두 동일함.

```jsx
// 리터럴 표현식
10

// 식별자 표현식
sum

// 연산자 표현식
10 + 20

// 함수/메소드 호출 표현식
square()
```

- 표현식은 평가되어 결국 하나의 값이 되므로 동치임.(표현식을 값처럼 사용할 수 있음. 값이 위치할 수 있는 자리에는 표현식도 위치할 수 있다는 의미임.)

```jsx
var x = 10;

// 연산자 표현식
x + 30; // 식별자 표현식과 숫자 리터럴과 연산자의 조합
```

# 2. 문과 표현식

- 문은 자바스크립트 엔진에게 내리는 명령임.

```jsx
// 변수 선언문
var x;

// 할당문
x = 5;

// 함수 선언문
function foo () {}

// 조건문
if (x > 5) { … }

// 반복문
for (var i = 0; i < 10; i++) { … }
```

- 문은 리터럴, 연산자, 표현식, 키워드 등으로 구성되며 세미콜론( ; )으로 끝나야 함.

```jsx
// 선언문(Declaration statement)
var x = 5 * 10; // 표현식 x = 5 * 10를 포함하는 문이다.

// 할당문(Assignment statement)
x = 100; // 이 자체가 표현식이지만 완전한 문이기도 하다.
```

- 선언문은 표현식이 아닌 문임. (값으로 평가 X) 선언문은 값처럼 사용할 수 없음.

```jsx
var foo = var x = 5 * 10;
```

- 할당문은 표현식인 문이므로 값처럼 사용할 수 있음.

```jsx
var foo = x = 100;
```

- x = 100 은 변수 x에 할당한 값100으로 평가될 수 있으므로 변수 foo에는 100이 할당됨.

# 3. 연산자란?

- 연산자는 하나 이상의 표현식을 대상으로 산술, 할당, 비교, 논리, 타입 연산 등을 수행해 하나의 값을 만듦.(연산의 대상을 피연산자라고 함.)

```jsx
// 산술 연산자
5 * 4 // 20

// 문자열 연결 연산자
'My name is ' + 'Lee' // "My name is Lee"

// 할당 연산자
var color = 'red'; // "red"

// 비교 연산자
3 > 5 // false

// 논리 연산자
(5 > 3) && (2 < 4)  // true

// 타입 연산자
typeof 'Hi' // "string"
```

- 피연산자는 연산의 대상이 되어야 하므로 값으로 평가할 수 있어야 함. 연산자는 값으로 평가된 피연산자를 연산해 새로운 값을 만듦.

# 4. 산술 연산자

- 산술 연산자는 피연산자를 대상으로 수학적 계산을 수행해 새로운 숫자 값을 만듦.(산술 연산을 할 수 없는 경우에는 NaN을 반환.)

## 4.1 이항 산술 연산자

- 이항 산술 연산자는 2개의 피연산자를 대상으로 연산하여 숫자 타입의 값을 만듦.
- 모든 이항 산술 연산자는 피연산자의 값을 변경하는 부수 효과가 없음.
- 어떤 산술 연산을 해도 피연산자의 값이 바뀌는 경우는 없고 새로운 값을 만듦.

| 이항 산술 연산자 | 의미   |
| ---------------- | ------ |
| +                | 덧셈   |
| -                | 뺄셈   |
| *                | 곱셈   |
| /                | 나눗셈 |
| %                | 나머지 |

```jsx
5 + 2  // 7
5 - 2  // 3
5 * 2  // 10
5 / 2  // 2.5
5 % 2  // 1
```

## 4.2 단항 산술 연산자

- 단항 산술 연산자는 1개의 피연산자를 대상으로 연산함.
- 증감 연산자는 피연산자의 값을 변경하는 부수 효과가 있음.(증감 연산을 하면 피연산자의 값이 바뀜.)

| 단항 산술 연산자 | 의미                                                 |
| ---------------- | ---------------------------------------------------- |
| ++               | 증가                                                 |
| --               | 감소                                                 |
| +                | 어떠한 효과도 없다. 음수를 양수로 반전하지도 않는다. |
| -                | 양수를 음수로 음수를 양수로 반전한 값을 반환한다.    |

- 피연산자 앞에 위치한 전위 증/감 연산자는 먼저 피연산자의 값을 증/감 시킨 후 다른 연산을 수행하고, 피연산자 뒤에 위치한 후위 증/감 연산자는 먼저 다른 연산을 수행한 후 피연산자의 값을 증/감 시킴.

```jsx
var x = 5, result;

// 선대입 후증가 (Postfix increment operator)
result = x++;
console.log(result, x); // 5 6

// 선증가 후대입 (Prefix increment operator)
result = ++x;
console.log(result, x); // 7 7

// 선대입 후감소 (Postfix decrement operator)
result = x--;
console.log(result, x); // 7 6

// 선감소 후대입 (Prefix decrement operator)
result = --x;
console.log(result, x); // 5 5
+10 // 10
+'10' // 10
+true // 1
+false // 0
```

- +단항 연산자는 피연산자에 어떠한 효과도 없음.

```jsx
-10 // -10
-'10' // -10
-true // -1
-false // -0
```

- -단항 연산자는 피연산자의 부호를 반전한 값을 반환함.

## 4.3 문자열 연결 연산자

- - 연산자는 피연산자 중 하나 이상이 문자열인 경우 문자열 연결 연산자로 동작함.(그 외의 경우 덧셈 연산자.)

```jsx
// 문자열 연결 연산자
'1' + '2'      // '12'
'1' + 2       // '12'

// 산술 연산자
1 + 2          // 3
1 + true       // 2 (true → 1)
1 + false      // 1 (false → 0)
true + false    // 1 (true → 1 / false → 0)
1 + null       // 1 (null → 0)
1 + undefined // NaN (undefined → NaN)
```

# 5. 할당 연산자

- 할당 연산자는 우항에 있는 피연산자의 평가 결과를 좌항에 있는 변수에 할당함.(부수 효과가 있음.)

| 할당 연산자 | 사례   | 동일 표현 |
| ----------- | ------ | --------- |
| =           | x = y  | x = y     |
| +=          | x += y | x = x + y |
| -=          | x -= y | x = x - y |
| *=          | x *= y | x = x * y |
| /=          | x /= y | x = x / y |
| %=          | x %= y | x = x % y |

```jsx
var x;

x = 10;   // 10
x += 5;   // 15
x -= 5;   // 10
x *= 5;   // 50
x /= 5;   // 10
x %= 5;   // 0

var str = 'My name is ';
str += 'Lee'; // My name is Lee
```

# 6. 비교 연산자

- 비교 연산자는 좌항과 우항의 피연산자를 비교하여 불리언 값을 반환함.(if 문이나 for 문과 같은 제어문의 조건식에서 주로 사용.)

## 6.1 동등/ 일치 비교 연산자

| 비교 연산자 | 의미        | 사례    | 설명                     |
| ----------- | ----------- | ------- | ------------------------ |
| ==          | 동등 비교   | x == y  | x와 y의 값이 같음        |
| ===         | 일치 비교   | x === y | x와 y의 값과 타입이 같음 |
| !=          | 부등 비교   | x != y  | x와 y의 값이 다름        |
| !==         | 불일치 비교 | x !== y | x와 y의 값과 타입이 다름 |

- 자바스크립트 엔진에 의해 암묵적으로 타입이 자동 변환되는 것을 암묵적 타입 변환이라고 부름.
- 동등 비교 연산자는 좌항과 우항의 피연산자가 타입은 다르더라도 암묵적 타입 변환 후에 같은 값이면 true를 반환함.

```jsx
// 동등 비교
5 == 5    // true
// 타입은 다르지만 암묵적 타입 변환을 통해 타입을 일치시키면 같은 값을 같는다.
5 == '5'   //true
5 == 8    // false
// 일치 비교
5 === 5   // true
5 === '5' // false
```

- 일치 비교(===) 연산자는 좌항과 우항의 피연산자가 타입도 같고 값도 같은 경우에 한하여 true를 반환함.

```jsx
NaN === NaN //false
```

- NaN은 자신과 일치하지 않는 유일한 값임.(숫자가 NaN인지 조사하려면 빌트인 함수 isNaN을 사용함.)

```jsx
isNaN(NaN) // true
0 === -0 //true
```

- 부동등 비교 연산자(!=) 와 불일치 비교 연산자(!==)는 동등 비교 (==) 연산자와 일치 비교(===) 연산자의 반대 개념임.

```jsx
// 부동등 비교
5 != 8    // true
5 != 5    // false
5 != '5'  // false

// 불일치 비교
5 !== 8   // true
5 !== 5   // false
5 !== '5' // true
```

## 6.2 대소 관계 비교 연산자

- 대소 관계 비교 연산자는 피연산자의 크기를 비교하여 불리언 값을 반환함.

| 대소 관계 비교 연산자 | 예제   | 설명                    |
| --------------------- | ------ | ----------------------- |
| >                     | x > y  | x가 y보다 크다 ✕        |
| <                     | x < y  | x가 y보다 작다 ✕        |
| >=                    | x >= y | x가 y보다 같거나 크다 ✕ |
| <=                    | x <= y | x가 y보다 같거나 크다 ✕ |

```jsx
// 대소 관계 비교
5 > 0    // true
5 > 5    // false
5 > 8    // false

5 < 0    // false
5 < 5    // false
5 < 8    // true

5 >= 0   // true
5 >= 5   // true
5 >= 8   // false

5 <= 0   // false
5 <= 5   // true
5 <= 8   // true
```

# 7. 삼항 조건 연산자

- 삼항 조건 연산자는 조건식의 평과 결과에 따라 반환할 값을 결정함.(부수 효과 X)
- 삼항 조건 연산자 표현식
  - CODE: 조건식 ? 조건식이 true일때 반환할 값 : 조건식이 false일 때 반환할 값
    - 물음표 앞의 첫번째 피연산자가 조건식, 즉 불리언 타입의 값으로 평가될 표현식임.(만약 불리언 값이 아니면 불리언 값으로 암묵적 타입 변환됨.)
    - 이때 조건식이 참이면 콜론(:) 앞의 두번째 피연산자가 평가되어 반환되고, 거짓이면 콜론(:)뒤에 세번째 피연산자가 평가 되어 반환됨.

```jsx
var x = 2;

// x가 짝수이면 '짝수'를 홀수이면 '홀수'를 반환한다.
// 2 % 2는 0이고 0은 false로 암묵적 타입 변환된다.
var result = x % 2 ? '홀수' : '짝수';

console.log(result); // 짝수
```

- 삼항 조건 연산자는 if…else 문을 사용해도 동일한 처리를 할 수 있음.

```jsx
var x = 2, result;

// x가 짝수이면 '짝수'를 홀수이면 '홀수'를 반환한다.
// 2 % 2는 0이고 0은 false로 암묵적 타입 변환된다.
if (x % 2) result = '홀수';
else       result = '짝수';

console.log(result); // 짝수
```

# 8. 논리 연산자

- 논리 연산자는 우항과 좌항의 피연산자를 논리 연산함.
- 논리 부정(!) 연산자는 언제나 불리언 값을 반환함.
- 논리합(||)연산자와 논리곱 (&&) 연산자는 일반적으로 불리언 값을 반환하지만 반드시 불리언 값을 반환해야 하는 것은 아님.

| 논리 연산자 | 의미        |
| ----------- | ----------- |
|             |             |
| &&          | 논리곱(AND) |
| !           | 부정(NOT)   |

```jsx
// 논리합(||) 연산자
true || true   // true
true || false  // true
false || true  // true
false || false // false

// 논리곱(&&) 연산자
true && true   // true
true && false  // false
false && true  // false
false && false // false

// 논리 부정(!) 연산자
!true  // false
!false // true
```

- 논리 부정(!) 연산자는 언제나 불리언 값을 반환함.
- 만약 피연산자가 불리언 값이 아니면 불리언 타입으로 암묵적 타입 변환됨.

```jsx
// 암묵적 타입 변환
!0 // true
```

- 논리합(||) 연산자와 논리곱(&&) 연산자의 연산 결과는 불리언 값이 아닐 수도 있음.(두 연산자는 언제나 피연산자 중 어느 한쪾 값을 반환함.)

# 9. 쉼표 연산자

- 쉼표 연산자는 왼쪽 피연산자부터 차례대로 피연산자를 평가하고 마지막 피연산자의 평가가 끝나면 마지막 피연산자의 평과 결과를 반환함.

```jsx
var x, y, z;
x= 1, y = 2, z = 3; //3
```

# 10. 그룹 연산자

- 그룹((…)) 연산자는 그룹 내의 표현식을 최우선으로 평가함.

```jsx
10 * 2 + 3 // 23
10 * (2 + 3) // 50
```

# 11. typeof 연산자

- typeof 연산자는 자신의 뒤에 위치한 피연산자의 데이터 타입을 문자열로 반환함.(null을 반환하는 경우는 없으며 함수의 경우 function을 반환함.

```jsx
typeof ''              // "string"
typeof 1               // "number"
typeof NaN             // "number"
typeof true            // "boolean"
typeof undefined       // "undefined"
typeof Symbol()        // "symbol"
typeof null            // "object"
typeof []              // "object"
typeof {}              // "object"
typeof new Date()      // "object"
typeof /test/gi        // "object"
typeof function () {}  // "function"
```

- 주의 해야할 점은 typeof 연산자로 null 값을 연산하면 null이 아닌 “object”를 반환함.

```jsx
typeof null // "object"
```

- 그러므로 null 타입을 확인할 때는 typeof 연산자를 사용하지 말고 일치 연산자(===)를 사용해야 함.

```jsx
var foo = null;
console.log(typeof foo === null); // false
console.log(foo === null);        // true
```