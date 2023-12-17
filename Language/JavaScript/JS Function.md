# JS Function

- 함수란 어떤 작업을 수행하기 위해 필요한 문들의 집합을 정의한 코드 블록임.
- 함수는 이름과 매개변수를 갖으며 필요한 떄에 호출하여 코드 블록에 담긴 문들을 일괄적으로 실행할 수 있음.

```jsx
// 함수의 정의(함수 선언문)
function square(number) {
  return number * number;
}
```

- 함수를 여러번 호출 할 수 있음.

```jsx
// 함수의 정의(함수 선언문)
function square(number) {
  return number * number;
}

// 함수의 호출
square(2); // 4
```

- 동일한 작업을 반복적으로 수행해야 한다면 미리 정의된 함수를 재사용하는 것이 효율적임.
- 함수의 일반적 기능은 객체 생성, 객체의 행위 정의, 정보 은닉, 클로저, 모듈화 등의 기능을 수행할 수 있음.
- 자바스크립트의 함수는 객체임.(다른 객체와 달리 호출할 수 있음.)
- 변수나 객체, 배열 등에 저장할 수 있고 다른 함수에 잔될되는 인수로도 사용할 수 있으며 함수의 반환값이 될 수도 있음.

# 1. 함수 정의

- 함수를 정의 하는 방식
  - 함수 선언문
  - 함수 표현식
  - Function 생성자 함수

# 1.1 함수 선언문

- 함수 선언문 방식으로 정의한 함수는 function 키워드와 이하의 내용으로 구성됨.
- **함수명**
  - 함수 선언문의 경우, 함수명은 생략할 수 없다. 함수명은 함수 몸체에서 자신을 재귀적(recursive) 호출하거나 자바스크립트 디버거가 해당 함수를 구분할 수 있는 식별자이다.
- **매개변수 목록**
  - 0개 이상의 목록으로 괄호로 감싸고 콤마로 분리한다. 다른 언어와의 차이점은 매개변수의 타입을 기술하지 않는다는 것이다. 이 때문에 함수 몸체 내에서 매개변수의 타입 체크가 필요할 수 있다.
- **함수 몸체**
  - 함수가 호출되었을 때 실행되는 문들의 집합이다. 중괄호({ })로 문들을 감싸고 `return` 문으로 결과값을 반환할 수 있다. 이를 반환값(return value)라 한다.

```jsx
// 함수 선언문
function square(number) {
  return number * number;
}
```

## 1.2 함수 표현식

- 자바스크립트의 함수는 일급 객체임.
- 함수 특징
  - 무명의 리터럴  표현이 가능함.
  - 변수나 자료 구조(객체, 배열…)에 저장할 수 있음.
  - 함수의 파라미터로 전달할 수 있음.
  - 반환값으로 사용할 수 있음.
- 함수 리터럴 방식으로 함수를 정의하고 변수에 할당할 수 있는데 이러한 방식을 함수 표현식이라고 함.

```jsx
// 함수 선언문으로 정의한 함수 square()
// 함수 표현식
var square = function(number) {
  return number * number;
};
```

- 함수 표현식 방식으로 정의한 함수는 함수명을 생략할 수 있음.(이러한 함수를 익명 함수라고 함.)

```jsx
// 기명 함수 표현식(named function expression)
var foo = function multiply(a, b) {
  return a * b;
};

// 익명 함수 표현식(anonymous function expression)
var bar = function(a, b) {
  return a * b;
};

console.log(foo(10, 5)); // 50
console.log(multiply(10, 5)); // Uncaught ReferenceError: multiply is not defined
```

- 함수 호출시 함수명이 아니라 함수를 가리키는 변수명을 사용해야 함.

```jsx
var foo = function(a, b) {
  return a * b;
};

var bar = foo;

console.log(foo(10, 10)); // 100
console.log(bar(10, 10)); // 100
```

- 변수 bar와 변수 foo는 동일한 익명 함수의 참조값을 갖음.

  ![anonymous_function.png](https://prod-files-secure.s3.us-west-2.amazonaws.com/510cd684-c9a0-45bd-b45d-b35ad6027628/dbb09b24-9eca-47b6-ab48-258844c2f806/anonymous_function.png)

- 함수가 할당된 변수를 사용해 함수를 호출하지 않고 기명 함수의 함수명을 사용해 호출하게 되면 에러가 발생함.(함수 표현식에서 사용한 함수명은 외부 코드에서 접근 불가능하기 때문임.)

## 1.2 Function 생성자 함수

- 함수 선언문과 함수 표현식은 모두 함수 리터럴 방식으로 함수를 정의하는데 이것은 결국 내장 함수 Function 생성자 함수로 함수를 생성하는 것을 단순화 시킨 short-hand(축약법)임.

```jsx
// Function 생성자 함수로 함수를 생성하는 문법
new Function(arg1, arg2, ... argN, functionBody)
var square = new Function('number', 'return number * number');
console.log(square(10)); // 100
```

# 2. 함수 호이스팅

```jsx
var res = square(5);

function square(number) {
  return number * number;
}
```

- 함수 선언문의 경우 함수 선언의 위치와는 상관없이 코드 내 어느 곳에서든지 호출이 가능한데 이것을 함수 호이스팅이라고 함.
- 호이스팅이란 var 선언문이나 funtion 선언문 등 선언문이 해당 Scope의 선두로 옮겨진 것처럼 동작하는 특성을 말함.
- 함수 선언문으로 정의된 함수는 자바스크립트 엔진이 스크립트가 로딩되는 시점에 바로 초기화하고 이를 VO(variable object)에 저장함.(함수 선언, 초기화, 할당이 한번에 이루어짐. 그렇기에 소스 내 어느 곳에서든지 호출이 가능함.)

```jsx
// 함수 표현식으로 함수를 정의한 경우
var res = square(5); // TypeError: square is not a function

var square = function(number) {
  return number * number;
}
```

- 함수 표현식의 경우 함수 호이스팅이 아니라 변수 호이스팅이 발생함.
- 변수 호이스팅은 변수 생성 및 초기화와 할당이 분리되어 진행된다. 호이스팅된 변수는 undefined로 초기화 되고 실제값의 할당은 할당문에서 이루어짐.

# 3. First-class object (일급 객체)

- 일급 객체란 생성, 대입, 연산, 인자 또는 반환값으로서의 전달 등 프로그래밍 언어의 기본적 조작을 제한없이 사용할 수 있는 대상을 의미함.
- 다음 조건을 만족하면 일급 객체로 간주함.
  - 무명의 리터럴로 표현이 가능.
  - 변수나 자료 구조에 저장할 수 있음.
  - 함수의 매개변수에 전달할 수 있음.
  - 반환값으로 사용할 수 있음.

# 4. 매개변수 (Parameter, 인자)

- 함수의 작업 실행을 위해 추가적인 정보가 필요할 경우 매개변수를 지정하는데 매개변수는 함수 내에서 **변수와 동일하게 동작함.**

## 4.1 매개변수 vs 인수(argument)

- 매개변수는 함수 내에서 변수와 동일하게 메모리 공간을 확보하며 함수에 전달한 인수는 매개변수에 할당됨.(인수를 전달하지 않으면 매개변수는 undefined로 초기화됨.)

```jsx
var foo = function (p1, p2) {
  console.log(p1, p2);
};

foo(1); // 1 undefined
```

## 4.2 Call-by-value

- 원시 타입 인수는 Call-by-value로 동작함. (함수 호출 시 원시 타입 인수를 함수에 매개변수로 전달할 때 매개변수에 값을 복사하여 함수로 전달하는 방식임.)
- 이때 함수 내에서 매개변수를 통해 값이 변경되어도 전달이 완료된 원시 타입 값은 변경되지 않음.

```jsx
function foo(primitive) {
  primitive += 1;
  return primitive;
}

var x = 0;

console.log(foo(x)); // 1
console.log(x);      // 0
```

## 4.2 Call-by-reference

- 객체형 인수는 Call-by-reference로 동작함.(함수 호출시 참조 타입 인수를 함수에 매개변수로 전달할 때 매개변수에 값이 복사되지 않고 객체의 참조값이 매개변수에 저장되어 함수로 전달되는 방식.)
- 이때 함수 내에서 매개변수의 참조값이 이용하여 객체의 값을 변경했을 때 전달되어진 참조형의 인수 값도 같이 변경됨.

```jsx
function changeVal(primitive, obj) {
  primitive += 100;
  obj.name = 'Kim';
  obj.gender = 'female';
}

var num = 100;
var obj = {
  name: 'Lee',
  gender: 'male'
};

console.log(num); // 100
console.log(obj); // Object {name: 'Lee', gender: 'male'}

changeVal(num, obj);

console.log(num); // 100
console.log(obj); // Object {name: 'Kim', gender: 'female'}
```

![call-by-val&ref.png](https://prod-files-secure.s3.us-west-2.amazonaws.com/510cd684-c9a0-45bd-b45d-b35ad6027628/1f93cd5a-b32e-4377-b52c-5f3ec68b6df1/call-by-valref.png)

# 5. 반환값

- 함수는 자신을 호출한 코드에게 수행한 겨로가를 반환할 수 있는데 이때 반환된 값을 반환값이라고 함.
- return 키워드는 함수를 호출한 코드에게 값을 반환할 때 사용함.
- 함수는 배열 등을 이용하여 한 번에 여러 개의 값을 반환할 수 있음.
- 함수는 반환을 생략할 수 있음.(함수는 암묵적으로 undefined를 반환함.)
- 자바스크립트 해석기는 return 키워드를 만나면 함수의 실행을 중단한 후 함수를 호출한 코드로 되돌아감.(return 키워드 이후에 다른 구문이 존재하면 그 구문을 실행되지 않음.)

```jsx
function calculateArea(width, height) {
  var area = width * height;
  return area; // 단일 값의 반환
}
console.log(calculateArea(3, 5)); // 15
console.log(calculateArea(8, 5)); // 40

function getSize(width, height, depth) {
  var area = width * height;
  var volume = width * height * depth;
  return [area, volume]; // 복수 값의 반환
}

console.log('area is ' + getSize(3, 2, 3)[0]);   // area is 6
console.log('volume is ' + getSize(3, 2, 3)[1]); // volume is 18
```

# 6. 함수 객체의 프로퍼티

- 함수도 객체이므로 프로퍼티를 가질 수 있음.

```jsx
function square(number) {
  return number * number;
}

square.x = 10;
square.y = 20;

console.log(square.x, square.y);
```

- 함수는 함수만의 프로퍼티를 갖음.

```jsx
function square(number) {
  return number * number;
}
console.dir(square);
```

![function_property.png](https://prod-files-secure.s3.us-west-2.amazonaws.com/510cd684-c9a0-45bd-b45d-b35ad6027628/d922967f-80c4-4b4f-8b9f-480acb18cb3f/function_property.png)

## 6.1 arguments 프로퍼티

- arguments 객체는 함수 호출 시 전달된 인수들의 정보를 담고 있는 순회가능한 유사 배열 객체이며 함수 내부에서 지역변수처럼 사용됨.(함수 외부에서는 사용할 수 없음.)

```jsx
function multiply(x, y) {
  console.log(arguments);
  return x * y;
}

multiply();        // {}
multiply(1);       // { '0': 1 }
multiply(1, 2);    // { '0': 1, '1': 2 }
multiply(1, 2, 3); // { '0': 1, '1': 2, '2': 3 }
```

- 매개변수는 인수로 초기화됨.
- 매개변수의 갯수보다 인수를 적게 전달했을 때 인수가 전달되지 않은 매개변수는 undefined로 초기화됨.
- 매개변수의 갯수보다 인수를 더 많이 전달한 경우 초과된 인수는 무시됨.
- arguments 객체는 매개변수 갯수가 확정되지 않은 가변 인자 함수를 구현할 때 유용하게 사용됨.

```jsx
function sum() {
  var res = 0;

  for (var i = 0; i < arguments.length; i++) {
    res += arguments[i];
  }

  return res;
}

console.log(sum());        // 0
console.log(sum(1, 2));    // 3
console.log(sum(1, 2, 3)); // 6
```

- arguments 객체는 배열의 형태로 인자값 정보를 담고 있지만 실제 배열이 아닌 유사배열객체임.
- 유사배열객체란 length 프로퍼티를 가진 객체를 말함.
- 유사배열객체는 배열이 아니므로 배열 메소드를 사용하는 경우 에러가 발생하게 됨.

## 6.2 caller 프로퍼티

- caller 프로퍼티는 자신을 호출한 함수를 의미함.

```jsx
function foo(func) {
  var res = func();
  return res;
}

function bar() {
  return 'caller : ' + bar.caller;
}

console.log(foo(bar)); // caller : function foo(func) {...}
console.log(bar());    // null (browser에서의 실행 결과)
```

## 6.3 length 프로퍼티

- length 프로퍼티는 함수 정의 시 작성된 매개변수 갯수를 의미함.

## 6.4 name 프로퍼티

- 함수명을 나타냄. 기명함수의 경우 함수명을 값으로 갖고 익명함수의 경우 빈문자열을 값으로 갖음.

```jsx
// 기명 함수 표현식(named function expression)
var namedFunc = function multiply(a, b) {
  return a * b;
};
// 익명 함수 표현식(anonymous function expression)
var anonymousFunc = function(a, b) {
  return a * b;
};

console.log(namedFunc.name);     // multiply
console.log(anonymousFunc.name); // ''
```

## 6.5 **proto** 접근자 프로퍼티

- [[Prototype]] 내부 슬롯은 프로토타입 객체를 가리킴.
- 프로토타입 객체란 프로토타입 기반 객체 지향 프로그래밍의 근간을 이루는 객체로서 객체간의 상속을 구현하기 위해 사용됨.
- ***\*proto**** 프로퍼티는 [[Prototype]] 내부 슬롯이 가리키는 프로토타입 객체에 접근하기 위해 사용하는 접근자 프로퍼티임.

```jsx
// __proto__ 접근자 프로퍼티를 통해 자신의 프로토타입 객체에 접근할 수 있다.
// 객체 리터럴로 셍성한 객체의 프로토타입 객체는 Object.prototype이다.
console.log({}.__proto__ === Object.prototype); // true
```

- ***\**proto\***** 프로퍼티는 객체가 직접 소유하는 프로퍼티가 아니라 모든 객체의 프로토타입 객체인 Object.prototype 객체의 프로퍼티인데 모든 객체는 상속을 통해 **proto** 접근자 프로퍼티는 사용할 수 있다.

```jsx
// 객체는 __proto__ 프로퍼티를 소유하지 않는다.
console.log(Object.getOwnPropertyDescriptor({}, '__proto__'));
// undefined

// __proto__ 프로퍼티는 모든 객체의 프로토타입 객체인 Object.prototype의 접근자 프로퍼티이다.
console.log(Object.getOwnPropertyDescriptor(Object.prototype, '__proto__'));
// {get: ƒ, set: ƒ, enumerable: false, configurable: true}

// 모든 객체는 Object.prototype의 접근자 프로퍼티 __proto__를 상속받아 사용할 수 있다.
console.log({}.__proto__ === Object.prototype); // true
```

- 함수도 객체이므로 ***\**proto**** 접근자 프로퍼티를 토애 프로토타입 객체에 접근할 수 있음.*

```jsx
// 함수 객체의 프로토타입 객체는 Function.prototype이다.
console.log((function() {}).__proto__ === Function.prototype); // true
```

## 6.6 prototype 프로퍼티

- prototype 프로퍼티는 함수 객체만이 소유하는 프로퍼티임.(일반 객체에는 prototype 프로퍼티가 없음.)

```jsx
// 함수 객체는 prototype 프로퍼티를 소유한다.
console.log(Object.getOwnPropertyDescriptor(function() {}, 'prototype'));
// {value: {…}, writable: true, enumerable: false, configurable: false}

// 일반 객체는 prototype 프로퍼티를 소유하지 않는다.
console.log(Object.getOwnPropertyDescriptor({}, 'prototype'));
// undefined
```

# 7.함수의 다양한 형태

## 7.1 즉시 실행 함수

- 함수의 정의와 동시에 실행되는 함수를 즉시 실행 함수라고 함.(다시 호출할 수 없음.)
- 즉시 실행 함수 내에 처리 로직을 모아 두면 혹시 있을 수도 있는 변수명 또는 함수명의 충돌을 방지할 수 있음.

## 7.2 내부 함수

- 함수 내부에 정의된 함수를 내부 함수라고 함.
- 내부함수는 부모함수의 외부에서 접근할 수 없음.

## 7.3 재귀 함수

- 재귀 함수는 자기 자신을 호출하는 함수를 말함.

- 재귀 함수는 자신을 무한히 연쇄 호출하므로 탈출 조건을 반드시 만들어야 함.(탈출 조건이 없으면 무한 호출되어 stackoverflow 에러가 발생함.)

  ![recursive-call.png](https://prod-files-secure.s3.us-west-2.amazonaws.com/510cd684-c9a0-45bd-b45d-b35ad6027628/199f1eee-690a-4454-ba7c-58c6bc23036c/recursive-call.png)

- 재귀 함수는 반복 연산을 간단히 구현할 수 있다는 장점이 있음.

- stackoverflow 에러를 발생 시킬 수 있으므로 주의해야 함.

  ![stackoverflow.png](https://prod-files-secure.s3.us-west-2.amazonaws.com/510cd684-c9a0-45bd-b45d-b35ad6027628/b341bd17-296a-4a69-945b-6badcbcb74cb/stackoverflow.png)

- 대부분의 재귀 함수는 for이나 while 문으로 구현이 가능함.

## 7.4 콜백 함수

- 콜백 함수는 함수를 명시적으로 호출하는 방식이 아니라 특정 이벤트가 발생했을 때 시스템에 의해 호출되는 함수를 말함.
- 콜백 함수는 매개변수를 통해 전달되고 전달받은 함수의 내부에서 어느 특정시점에 실행됨.
- setTimeout()의 콜백 함수에서 두번째 매개변수에 전달된 시간이 경과되면 첫번째 매개변수에 전달한 콜백 함수가 호출됨.

```jsx
setTimeout(function () {
   console.log('1초 후 출력된다.');
}, 1000);
```

![callback.png](https://prod-files-secure.s3.us-west-2.amazonaws.com/510cd684-c9a0-45bd-b45d-b35ad6027628/fbaf9395-8af8-460c-a227-8af6124c2353/callback.png)