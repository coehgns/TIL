# JS Data type & Variable

- 변수란 값이 위치하고 있는 메모리 주소에 접근하기 위해 사람이 이해할 수 있는 언어로 명명한 식별자임.

  ![memory_address.png](https://prod-files-secure.s3.us-west-2.amazonaws.com/510cd684-c9a0-45bd-b45d-b35ad6027628/ff2f50aa-e0ea-4787-9ac7-b446d4df9d80/memory_address.png)

- 메모리에 값을 지정하기 위해서는 먼저 메모리 공간을 확보해야 할 메모리의 크기를 알아야함.(값의 종류에 따라 확보해야 할 메모리의 크기가 다르기 때문.)

- 데이터의 종류를 데이터 타입(Data Type)이라 함.

- C나 Java 같은 C-fmaily 언어는 정적 타입 언어로 변수 선언 시 변수에 저장할 값의 종류를 사전에 타입 지정하여야 함.

```c
// 1byte 정수형: -128 ~ 127
char c;

// 4byte 정수형: -2, 124, 483, 648 ~ 2, 124, 483, 647
int num;
```

![int_num.png](https://prod-files-secure.s3.us-west-2.amazonaws.com/510cd684-c9a0-45bd-b45d-b35ad6027628/b842daac-73d3-4075-a89b-203d9140d4bd/int_num.png)

- C 언어의 경우, 4byte 정수형인 int형 변수 선언을 만나면 시스템은 이후 할당된 값과는 상관없이 4byte의 메모리 영역을 확보함. 이후 int형 변수에 할당할 때에는 int형 값을 할당해야 함.

```jsx
var str = 'Hello';
var num = 1;
var bool = true;

var foo = 'string';
colsole.log(typeof foo); // string
foo = 1;
console.log(typeof foo); // number
```

- 자바스크립트는 동적 타임 언어임.
- 변수의 타입 지정 없이 값이 할당되는 과정에서 자동으로 변수의 타입이 결정됨.(변수는 고정된 타입이 없음. 그러므로 같은 변수에 여러 타입의 값을 자유롭게 할당할 수 있음.)

# 1. 데이터 타입

- 데이터 타입은 프로그래밍 언어에서 사용할 수 있은 데이터의 종류를 말함.
- 코드에서 사용되는 모든 데이터는 메모리에 저장하고 참조할 수 있어야 함.
- 데이터 타입은 데이터를 메모리에 저장할 때 확보해야 하는 메모리 공간의 크기와 할당할 수 있는 유효한 값에 대한 정보, 그리고 메모리에 저장되어 있는 2진수 데이터를 어떻게 해석할 지에 대한 정보를 컴퓨터와 개발자에게 제공함.
- 자바스크립트의 모든 값은 데이터 타입을 갖음.
- 원시 타입
  - boolean
  - null
  - undefined
  - number
  - string
- symbol
  - 객체 타입 object
- 숫자 타입의 값은 주로 산술 연산을 위해 만들지만 문자열 타입의 값은 주로 텍스트로 출력하기 위해 만듦.

## 1.1 원시 타입

- 원시 타입의 값은 변경 불가능한 값이며 pass-by-value(값에 의한 전달)임.

### 1.1.1 number

- 자바스크립트는 독특하게 하나의 숫자 타입만 존재함.
- 모든 수를 실수를 처리하며 정수만을 표현하기 위한 특별한 데이터 타입은 없음.

```jsx
var integer = 10;        // 정수
var double = 10.12;      // 실수
var negative = -20;      // 음의 정수
var binary = 0b01000001; // 2진수
var octal = 0o101;       // 8진수
var hex = 0x41;          // 16진수
```

- 자바스크립트는 2진수 , 8진수, 16진수 데이터 타입을 제공하지 않음.

```jsx
console.log(binary); // 65
console.log(octal);  // 65
console.log(hex);    // 65

// 표기법만 다를뿐 같은 값이다.
console.log(binary === octal); // true
console.log(octal === hex);    // true
```

- 자바스크립트의 숫자 타입은 정수만을 위한 타입이 없고 모든 수를 실수 처리함.(정수로 표시된다해도 사실은 실수임.)

```jsx
console.log(1 === 1.0); // true

var result = 4 / 2;
console.log(result); // 2
result = 3 /2;
console.log(result); // 1.5
```

- Infinity: 양의 무한대
- -Infinity: 음의 무한대
- NaN: 산술 연산 불가(not-a-number)

```jsx
var pInf = 10 / 0;  // 양의 무한대
console.log(pInf);  // Infinity

var nInf = 10 / -0; // 음의 무한대
console.log(nInf);  // -Infinity

var nan = 1 * 'string'; // 산술 연산 불가
console.log(nan);       // NaN
```

### 1.1.2 string

- 문자열(string) 타입은 텍스트 데이터를 나타내는데 사용함.
- 문자열은 0개 이상의 16bit 유니코드 문자(UTF-16)들의 집합으로 대부분의 전세계의 문자를 표현할 수 있음.

```jsx
var str = "string"; // 큰 따옴표
str = 'string';     // 작은 따옴표
str = `string`;     // 백틱(ES6 템플릿 리터럴)

str = "큰 따옴표로 감싼 문자열 내의 '작은 따옴표'는 문자열이다.";
str = '작은 따옴표로 감싼 문자열 내의 "큰 따옴표"는 문자열이다.';
```

- 자바스크립트의 문자열은 원시 타입이며 변경 불가능함.(한 번 문자열이 생성되면 그 문자열을 변경할 수 없음.)

```jsx
var str = 'Hello';
str = 'world';
```

- 첫번째 구문이 실행되면 메모리에 문자열 ‘Hello’가 생성되고 식별자 str은 메모리에 생성된 문자열 ‘Hello’의 메모리 주소를 가리킴.
- 두번째 구문이 실행되면 이전에 생성된 문자열 ‘Hello’를 수정하는 것이 아니라 새로운 문자열 ‘world’를 메모리에 생성하고 식별자 str은 이것을 가리킴.(이때 문장려 ‘Hello’와 ‘world’는 모두 메모리에 존재하고 있음.)
- 변수 str은 문자열 ‘Hello’를 가리키고 있다가 문자열 ‘world’를 가리키도록 변경됨.

```jsx
var str = 'string';
// 문자열은 유사배열이다.
for (var i = 0; i < str.length; i++) {
  console.log(str[i]);
}

// 문자열을 변경할 수 없다.
str[0] = 'S';
console.log(str); // string
```

- 문자열은 배열 처럼 인덱스를 통해 접근할 수 있는데 이와 같은 특성을 갖는 데이터를 유사 배열이라 함.
- 한번 생성된 문자열은 ready only로서 변경할 수 없음.
- 새로운 문자열을 재할당하는 것은 가능함.

```jsx
var str = 'string';
console.log(str); // string

str = 'String';
console.log(str); // String

str += ' test';
console.log(str); // String test

str = str.substring(0, 3);
console.log(str); // Str

str = str.toUpperCase();
console.log(str); // STR
```

### 1.1.3 boolean

- 불리언 타입의 값은 논리적 참, 거짓을 나타내는 true와 false 뿐임.

```jsx
var foo = true;
var bar = false;

// typeof 연산자는 타입을 나타내는 문자열을 반환한다.
console.log(typeof foo); // boolean
console.log(typeof bar); // boolean
```

- 불리언 타입의 값은 참과 거짓으로 구분되는 조건에 의해 조건문에서 자주 사용함.
- 비어있는 문자열과 null, undefined, 숫자 0은 false로 간주됨.

### 1.1.4 undefined

- undefined 타입의 값은 undefined가 유일한데 선언 이후 값을 할당하지 않은 변수는 undefined 값을 가짐.(선언은 되었지만 값을 할당하지 않은 변수에 접근하거나 존재하지 않는 객체 프로퍼티에 접근할 경우 undefined가 반환됨.)
- 변수 선언에 의해 확보된 메모리 공간을 처음 할당이 이루어질 때까지 빈 상태로 내버려두지 않고 자바스크립트 엔진이 undefined로 초기화하기 때문임.

```jsx
var foo;
console.log(foo); // undefined
```

### 1.1.5 null

- null 타입의 값은 null이 유일함.
- 자바스크립티는 대소문자를 구별하므로 null은 Null, NULL 등과 다름.
- 프로그래밍 언어에서 null은 의도적으로 변수에 값이 없다는 것을 명시할 때 사용함.(변수가 기억하는 메모리 어드레스의 참조 정보를 제거하는 것을 의미함.)

```jsx
var foo = 'Lee';
foo = null; // 참조 정보가 제거됨
```

- 함수가 호출되었으나 유효한 값을 반환할 수 없는 경우, 명시적으로 null을 반환하기도 함.
- 타입을 나타내는 문자열을 반환하는 typeof 연산자로 null 값을 연산해 보면 null이 아닌 object가 나옴.

```jsx
var foo = null;
console.log(typeof foo); // object
```

- null 타입을 확인할 때 typeof 연산자를 사용하면 안되고 일치 연산자를 사용하여야 함.

```jsx
var foo = null;
console.log(typeof foo == null); // false
console.log(foo == null);        // true
```

### 1.1.6 symbol

- 심볼은 주로 이름의 충돌 위험이 없는 유일한 객체의 프로퍼티 키를 만들기 위해 사용함.
- 심볼은 Symbol 함수를 호출해 생성함.

```jsx
// 심볼 key는 이름의 충돌 위험이 없는 유일한 객체의 프로퍼티 키
var key = Symbol('key');
console.log(typeof key); // symbol

var obj = {};
obj[key] = 'value';
console.log(obj[key]); // value
```

## 1.2 객체 타입

- 객체는 데이터와 그 데이터에 관련한 동작을 모두 포함할 수 있는 개념적 존재임.(이름과 값을 가지는 데이터를 의미하는 프로퍼티와 동작을 의미하는 메소드를 포함할 수 있는 독립적 주체임.)
- 자바스크립트는 객체 기반의 스크립트 언어로서 자바스크립트를 이루고 있는 거의 모든 것이 객체임.
- 원시 타입을 제외한 나머지 값들은 모두 객체.

# 2. 변수

- 변수는 프로그램에서 사용되는 데이터를 일정 기간 동안 기억하여 필요한 때에 다시 사용하기 위해 식별자를 명시한 것임.(변수에 명시한 고유한 식별자를 변수명이라 하고 변수로 참조할 수 있는 데이터를 변수값이라고 함.)
- 변수는 var, let, const 키워드를 사용하여 선언하고 할당 연산자를 사용해 값을 할당함. 그리고 식별자인 변수명을 사용해 변수에 저장된 값을 참조함.

```jsx
var score;  // 변수의 선언
score = 80; // 값의 할당
score = 90; // 값의 재할당
score;      // 변수의 참조

// 변수의 선언과 할당
var average = (50 + 100) / 2;
```

## 2.1 변수의 선언

- 변수를 사용하면 값의 의미가 명확해져서 코드의 가독성이 좋아짐.
- 변수의 존재 목적을 쉽게 이해할 수 있도록 의미있는 변수명을 지정해야 함.

```jsx
var x = 3;       //NG
var score = 100; //OK
```

- 변수명은 식별자로 불리기도 하며 명명 규칙이 존재함.
- 반드시 영문자(특수문자 제외), underscore ( _ ), 또는 달러 기호($)로 시작하여야 함.
- 자바스크립트는 대/소문자를 구별하므로 사용할 수 있는 문자는 “A” ~ “Z”와 “a”~ “z” 임.
- 변수를 선언할 때는 var 키워드를 사용함.(등호는 변수에 값을 할당하는 할당 연산자임.)

```jsx
var name;     // 선언
name = 'Lee'; // 할당

var age = 30; // 선언과 할당

var person = 'Lee',
    address = 'Seoul',
    price = 200;

var price = 10;
var tax   = 1;
var total = price + tax;
```

- 값을 할당하지 않은 변수 즉 선언만 되어 있는 변수는 undefined로 초기값을 갖음.(선언하지 않은 변수에 접근하면 ReferenceError가 발생함.)

```jsx
var x;
console.log(x); // undefined
console.log(y); // ReferenceError
```

## 2.1 변수의 중복 선언

- var 키워드로 선언한 변수는 중복 선언이 가능함.

```jsx
var x = 1;
console.log(x); // 1

// 변수의 중복 선언
var x = 100;
console.log(x); // 100
```

## 2.2 동적 타이핑

- 변수의 타입 지정 없이 값이 할당되는 과정에서 값의 타입에 의해 자동으로 타입이 결정됨.

```jsx
var foo;

console.log(typeof foo);  // undefined

foo = null;
console.log(typeof foo);  // object

foo = {};
console.log(typeof foo);  // object

foo = 3;
console.log(typeof foo);  // number

foo = 3.14;
console.log(typeof foo);  // number

foo = 'Hi';
console.log(typeof foo);  // string

foo = true;
console.log(typeof foo);  // boolean
```

## 2.3 변수 호이스팅

- 호이스팅이란 var 선언문이나 function 선언문 등 모든 선언문이 해당 Scope의 선두로 옮겨진 것처럼 동작하는 특성을 말함.

- 변수가 생성되는 과정과 호이스팅이 이루어지는 과정

  - 선언 단계:변수 객체에 변수를 등록함. 이 변수 객체는 스코프가 참조하는 대상이 됨.
  - 초기화 단계: 변수 객체에 등록된 변수를 메모리에 할당함. 이 단계에서 변수는 undefined로 초기화됨.
  - 할당 단계: undefined로 초기화된 변수에 실제값을 할당함.

- var 키워드로 선언된 변수는 선언 단계와 초기화 단계가 한번에 이루어짐.(스코프에 변수가 등록되고 변수는 메모리에 공간을 확보한 후 undefined로 초기화됨.)

  ![var-lifecycle.png](https://prod-files-secure.s3.us-west-2.amazonaws.com/510cd684-c9a0-45bd-b45d-b35ad6027628/01e801b3-04d6-43a6-854f-21b17727b310/var-lifecycle.png)

- Scope

- 함수 레벨 스코프:함수 내에서 선언된 변수는 함수 내에서만 유효하며 함수 외부에서는 참조할 수 없음. 즉, 함수 내부에서 선언한 변수는 지역 변수이며 함수 외부에서 선언한 변수는 모두 전역 변수임.

- 블록 레벨 스코프:코드 블록 내에서 선언된 변수는 코드 블록 내에서만 유효하며 코드 블록 외부에서는 참조할 수 없음.