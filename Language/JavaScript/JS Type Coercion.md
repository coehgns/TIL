# JS Type coercion

# 1. 타입 변환이란?

- 개발자에 의해 의도적으로 값의 타입을 변환하는 것을 명시적 타입 변환 또는 타입 캐스팅이라고 함.

```jsx
var x = 10;

// 명시적 타입 변환
var str = x.toString(); // 숫자를 문자열로 타입 캐스팅한다.
console.log(typeof str); // string
```

- 자바스크립트는 개발자의 의도와는 상관없이 자바스크립트 엔진에 의해 암묵적으로 타입이 자동 변환되는데 이를 암묵적 타입 변환 또는 타입 강제 변환 이라고 함.

```jsx
var x = 10;

// 암묵적 타입 변환
// 숫자 타입 x의 값을 바탕으로 새로운 문자열 타입의 값을 생성해 표현식을 평가한다.
var str = x + '';

console.log(typeof str, str); // string 10

// 변수 x의 값이 변경된 것은 아니다.
console.log(x); // 10
```

- 자신이 작성한 코드에서 암묵적 타입 변환이 발생하는지, 발생한다면 어떤 타입의 어떤 값으로 변환되는지, 그리고 타입 변환된 값으로 표현식은 어떻게 평가될 것인지 예측이 가능해야 하는데 예측하지 못하거나 예측한 내용이 결과와 다르다면 버그를 생산할 가능성이 높음.

# 2. 암묵적 타입 변환

- 자바스크립트 엔진은 표현식을 평가할 때 문맥에 고려하여 암묵적 타입 변환을 실행함.

```jsx
// 표현식이 모두 문자열 타입이여야 하는 컨텍스트
'10' + 2               // '102'
`1 * 10 = ${ 1 * 10 }` // "1 * 10 = 10"

// 표현식이 모두 숫자 타입이여야 하는 컨텍스트
5 * '10' // 50

// 표현식이 불리언 타입이여야 하는 컨텍스트
!0 // true
if (1) { }
```

- 자바스크립트는 가급적 에러를 발생시키지 않도록 암묵적 타입 변환을 통해 표현식을 평가함.
- 암묵적 타입 변환이 발생하면 문자열, 숫자, 불리언과 같은 원시 타입 중 하나로 타입을 자동 변환함.

## 2.1 문자열 타입으로 변환

```jsx
1 + '2' // "12"
```

- 문자열 연결 연산자의 피연산자는 문맥 상 문자열 타입이여야 함.

```jsx
console.log('1 + 1 = ${1 + 1}`); // "1 + 1 = 2"
```

- 자바스크립트 엔진은 문자열 타입이 아닌 값을 문자열 타입으로 암묵적 타입 변환을 수행할 때 아래와 같이 동작함.

```jsx
// 숫자 타입
0 + ''              // "0"
-0 + ''             // "0"
1 + ''              // "1"
-1 + ''             // "-1"
NaN + ''            // "NaN"
Infinity + ''       // "Infinity"
-Infinity + ''      // "-Infinity"
// 불리언 타입
true + ''           // "true"
false + ''          // "false"
// null 타입
null + ''           // "null"
// undefined 타입
undefined + ''      // "undefined"
// 심볼 타입
(Symbol()) + ''     // TypeError: Cannot convert a Symbol value to a string
// 객체 타입
({}) + ''           // "[object Object]"
Math + ''           // "[object Math]"
[] + ''             // ""
[10, 20] + ''       // "10,20"
(function(){}) + '' // "function(){}"
Array + ''          // "function Array() { [native code] }"
```

## 2.2 숫자 타입으로 변환

```jsx
1 - '1'    // 0
1 * '10'   // 10
1 / 'one'  // NaN
```

- 위 예제는 산술 연산자인데 산수 연산자의 피연산자는 문맥 상 숫자 타입이여야 함.
- 피연산자를 숫자 타입으로 변환할 수 없는 경우는 산술 연산을 수행할 수 없으므로 NaN을 반환함.
- 피연산자를 숫자 타입으로 변환해야 할 컨텍스트는 산술 연산자 뿐만이 아님.

```jsx
'1' > 0   //true
```

- 비교 연산자의 역할은 불리언 값을 만듦.
- 자바스크립트 엔진은 비교 연산자 표현식을 평가하기 위해 비교 연산자의 피연산자 중에서 숫자 타입이 아닌 피연산자를 숫자 타입으로 암묵적 타입 변환함.
- 숫자 타입 아닌 값을 숫자 타입으로 암묵적 타입 변환을 수행할 때 아래와 같이 동작함.

```jsx
// 문자열 타입
+''             // 0
+'0'            // 0
+'1'            // 1
+'string'       // NaN
// 불리언 타입
+true           // 1
+false          // 0
// null 타입
+null           // 0
// undefined 타입
+undefined      // NaN
// 심볼 타입
+Symbol()       // TypeError: Cannot convert a Symbol value to a number
// 객체 타입
+{}             // NaN
+[]             // 0
+[10, 20]       // NaN
+(function(){}) // NaN
```

- 빈 문자열(‘’), 빈 배열([]), null, false는 0으로, true는 1로 변환됨.(undefined는 변환되지 않아 NaN이 됨.)

## 2.3 불리언 타입으로 변환

```jsx
if ('') console.log(x);
```

- 자바스크립트 엔진은 제어문의 조건식을 평가 결과를 불리언 타입으로 암묵적 타입 변환함.

```jsx
if ('')    console.log('1');
if (true)  console.log('2');
if (0)     console.log('3');
if ('str') console.log('4');
if (null)  console.log('5');

// 2 4
```

- 이때 자바스크립트 엔진은 불리언 타입이 아닌 값을 Truthy 값 또는 Falsy 값으로 구분함.(Truthy 값은 true로, Falsy 값은 false로 변환됨.)
- 아래 값들은 불리언 값으로 평가되어야 할 컨텍스트에서 false로 평가되는 Falsy 값임.
  - false
  - undefined
  - null
  - 0, -0
  - NaN
  - ‘’ (빈문자열)

```jsx
if (!false)     console.log(false + ' is falsy value');
if (!undefined) console.log(undefined + ' is falsy value');
if (!null)      console.log(null + ' is falsy value');
if (!0)         console.log(0 + ' is falsy value');
if (!NaN)       console.log(NaN + ' is falsy value');
if (!'')        console.log('' + ' is falsy value');
```

- 아래 예제는 Truthy/ Flasy 값을 판별하는 함수임.

```jsx
// 주어진 인자가 Falsy 값이면 true, Truthy 값이면 false를 반환한다.
function isFalsy(v) {
  return !v;
}

// 주어진 인자가 Truthy 값이면 true, Falsy 값이면 false를 반환한다.
function isTruthy(v) {
  return !!v;
}

// 모두 true를 반환한다.
console.log(isFalsy(false));
console.log(isFalsy(undefined));
console.log(isFalsy(null));
console.log(isFalsy(0));
console.log(isFalsy(NaN));
console.log(isFalsy(''));

console.log(isTruthy(true));
// 빈 문자열이 아닌 문자열은 Truthy 값이다.
console.log(isTruthy('0'));
console.log(isTruthy({}));
console.log(isTruthy([]));
```

# 3. 명시적 타입 변환

- 명시적으로 타입을 변경하는 방법은 다양함.
- 래퍼 객체를 생성하기 위해 사용하는 래퍼 객체 생성자 함수를 new 연산자 없이 호출하는 방법과 자바스크립트에서 제공하는 빌트인 메소드를 사용하는 방법, 암묵적 타입 변환을 이용하는 방법이 있음.

## 3.1 문자열 타입으로 변환

- 문자열 타입이 아닌 값을 문자열 타입으로 변환하는 방법
  - String 생성자 함수를 new 연산자 없이 호출하는 방법
  - Object,protorype.toString 메소드를 사용하는 방법
  - 문자열 연결 연산자를 이용하는 방법

```jsx
// 1. String 생성자 함수를 new 연산자 없이 호출하는 방법
// 숫자 타입 => 문자열 타입
console.log(String(1));        // "1"
console.log(String(NaN));      // "NaN"
console.log(String(Infinity)); // "Infinity"
// 불리언 타입 => 문자열 타입
console.log(String(true));     // "true"
console.log(String(false));    // "false"

// 2. Object.prototype.toString 메소드를 사용하는 방법
// 숫자 타입 => 문자열 타입
console.log((1).toString());        // "1"
console.log((NaN).toString());      // "NaN"
console.log((Infinity).toString()); // "Infinity"
// 불리언 타입 => 문자열 타입
console.log((true).toString());     // "true"
console.log((false).toString());    // "false"

// 3. 문자열 연결 연산자를 이용하는 방법
// 숫자 타입 => 문자열 타입
console.log(1 + '');        // "1"
console.log(NaN + '');      // "NaN"
console.log(Infinity + ''); // "Infinity"
// 불리언 타입 => 문자열 타입
console.log(true + '');     // "true"
console.log(false + '');    // "false"
```

## 3.2 숫자 타입으로 변환

- 숫자 타입이 아닌 값을 숫자 타입으로 변환하는 방법
  - Number 생성자 함수를 new 연산자 없이 호출하는 방법
  - parseInt, parseFloat 함수를 사용하는 방법(문자열만 변환 가능)
  - 단항 연결 연산자를 이용하는 방법
  - 산술 연산자를 이용하는 방법

```jsx
// 1. Number 생성자 함수를 new 연산자 없이 호출하는 방법
// 문자열 타입 => 숫자 타입
console.log(Number('0'));     // 0
console.log(Number('-1'));    // -1
console.log(Number('10.53')); // 10.53
// 불리언 타입 => 숫자 타입
console.log(Number(true));    // 1
console.log(Number(false));   // 0

// 2. parseInt, parseFloat 함수를 사용하는 방법(문자열만 변환 가능)
// 문자열 타입 => 숫자 타입
console.log(parseInt('0'));       // 0
console.log(parseInt('-1'));      // -1
console.log(parseFloat('10.53')); // 10.53

// 3. + 단항 연결 연산자를 이용하는 방법
// 문자열 타입 => 숫자 타입
console.log(+'0');     // 0
console.log(+'-1');    // -1
console.log(+'10.53'); // 10.53
// 불리언 타입 => 숫자 타입
console.log(+true);    // 1
console.log(+false);   // 0

// 4. * 산술 연산자를 이용하는 방법
// 문자열 타입 => 숫자 타입
console.log('0' * 1);     // 0
console.log('-1' * 1);    // -1
console.log('10.53' * 1); // 10.53
// 불리언 타입 => 숫자 타입
console.log(true * 1);    // 1
console.log(false * 1);   // 0
```

## 3.3 불리언 타입으로 변환

- 불리언 타입이 아닌 값을 불리언 타입으로 변환하는 방법
  - Boolean 생성자 함수를 new 연산자 없이 호출하는 방버
  - ! 부정 논리 연산자를 두번 사용하는 방법

```jsx
// 1. Boolean 생성자 함수를 new 연산자 없이 호출하는 방법
// 문자열 타입 => 불리언 타입
console.log(Boolean('x'));       // true
console.log(Boolean(''));        // false
console.log(Boolean('false'));   // true
// 숫자 타입 => 불리언 타입
console.log(Boolean(0));         // false
console.log(Boolean(1));         // true
console.log(Boolean(NaN));       // false
console.log(Boolean(Infinity));  // true
// null 타입 => 불리언 타입
console.log(Boolean(null));      // false
// undefined 타입 => 불리언 타 입
console.log(Boolean(undefined)); // false
// 객체 타입 => 불리언 타입
console.log(Boolean({}));        // true
console.log(Boolean([]));        // true

// 2. ! 부정 논리 연산자를 두번 사용하는 방법
// 문자열 타입 => 불리언 타입
console.log(!!'x');       // true
console.log(!!'');        // false
console.log(!!'false');   // true
// 숫자 타입 => 불리언 타입
console.log(!!0);         // false
console.log(!!1);         // true
console.log(!!NaN);       // false
console.log(!!Infinity);  // true
// null 타입 => 불리언 타입
console.log(!!null);      // false
// undefined 타입 => 불리언 타입
console.log(!!undefined); // false
// 객체 타입 => 불리언 타입
console.log(!!{});        // true
console.log(!![]);        // true
```

# 4. 단축 평가

```jsx
'Cat' && 'Dog' // “Dog”
```

- 논리곱 연산자 &&는 두개의 피연산자가 모두 true로 평가될 때 true를 반환함.

1. 첫번째 피연산자 ‘Cat’은 Truthy 값이므로 true로 평가됨.(두번째 피연산자까지 평가해 보아야 위 표현식을 평가할 수 있음.)
2. 두번째 피연산자 ‘Dog’는 Truthy 값이므로 true로 평가됨.(논리곱 연산의 결과를 결정한 것은 두번째 피연산자 ‘Dog’임.)
3. 논리곱 연산자 &&는 논리 연산의 결과를 결정한 두번째 피연산자의 평가 결과 문자열 ‘Dog’를 그대로 반환함.

- 논리합 연산자 ||도 논리곱 연산자 &&와 동일하게 동작함.

```jsx
'Cat' || 'Dog' // 'Cat'
```

- 논리합 연산자 ||는 두개의 피연산자 중 하나만 true로 평가되어도 true를 반환함.(대부분의 연산자가 오른쪽에서 왼쪽으로 평가가 진행됨.)

1. 첫번째 피연산자 ‘Cat’은 Truthy 값이므로 true로 평가됨.
2. 논리합 연산자 ||는 논리 연산의 결과를 결정한 첫번째 피연산자의 평가 결과 문자열 ‘Cat’을 그대로 반환함.

- 논리곱 연산자 &&와 논리합 연산자 ||는 논리 평가를 결정한 피연산자의 평가 결과를 그대로 반환함. 이를 단축 평가라 부름.
- 단축 평가의 규칙

| 단축 평가 표현식  | 평가 결과 |
| ----------------- | --------- |
| true              |           |
| false             |           |
| true && anything  | anything  |
| false && anything | false     |

```jsx
// 논리합(||) 연산자
'Cat' || 'Dog'  // 'Cat'
false || 'Dog'  // 'Dog'
'Cat' || false  // 'Cat'

// 논리곱(&&) 연산자
'Cat' && 'Dog'  // Dog
false && 'Dog'  // false
'Cat' && false  // false
```

- 객체가 null인지 확인하고 프로퍼티를 참조할 때

```jsx
var elem = null;

console.log(elem.value); // TypeError: Cannot read property 'value' of null
console.log(elem && elem.value); // null
```

- 객체는 키와 값으로 구성된 프로퍼티들의 집합임.(객체가 null인 경우 객체의 프로퍼티를 참조하면 타입 에러가 발생하는데 단축 평가를 사용하면 에러를 발생시키지 않음.)
- 함수의 인수를 초기화할 때

```jsx
// 단축 평가를 사용한 매개변수의 기본값 설정
function getStringLength(str) {
  str = str || '';
  return str.length;
}

getStringLength();     // 0
getStringLength('hi'); // 2

// ES6의 매개변수의 기본값 설정
function getStringLength(str = '') {
  return str.length;
}

getStringLength();     // 0
getStringLength('hi'); // 2
```