# JS Built-in Object

- 자바스크립트의 객체는 다음과 같이 3개의 객체로 분류할 수 있음.

  ![objects.png](https://prod-files-secure.s3.us-west-2.amazonaws.com/510cd684-c9a0-45bd-b45d-b35ad6027628/1c5a233c-1fee-4343-9277-cd7f65923174/objects.png)

# 1. 네이티브 객체

- 네이티브 객체는 애플리케이션 전역의 공통 기능을 제공함.(애플리케이션의 환경과 관계없이 언제나 사용할 수 있음.)
- 객체 생성에 관계가 있는 함수 객체와 메소드로 구성됨.

## 1.1 Object

- Object() 생성자 함수는 객체를 생성함.(생성자 인수값이 null이거나 undefined이면 빈 객체를 반환함.)

```jsx
// 변수 o에 빈 객체를 저장한다
var o = new Object();
console.log(typeof o + ': ', o);

o = new Object(undefined);
console.log(typeof o + ': ', o);

o = new Object(null);
console.log(typeof o + ': ', o);
```

- 생성자 함수의 인수값에 따라 강제 형변호나된 객체가 반환되는데 반환된 객체의 [[Prototype]] 프로퍼티에 바인딩된 객체는 Object.prototype이 아님.

```jsx
// String 객체를 반환한다
// var obj = new String('String');과 동치이다
var obj = new Object('String');
console.log(typeof obj + ': ', obj);
console.dir(obj);

var strObj = new String('String');
console.log(typeof strObj + ': ', strObj);

// Number 객체를 반환한다
// var obj = new Number(123);과 동치이다
var obj = new Object(123);
console.log(typeof obj + ': ', obj);

var numObj = new Number(123);
console.log(typeof numObj + ': ', numObj);

// Boolean 객체를 반환한다.
// var obj = new Boolean(true);과 동치이다
var obj = new Object(true);
console.log(typeof obj + ': ', obj);

var boolObj = new Boolean(123);
console.log(typeof boolObj + ': ', boolObj);
```

## 1.2 Function

- 자바스크립트의 모든 함수는 Function 객체임.(Function 객체는 new 연산자를 사용해 생성할 수 있음.)

```jsx
var adder = new Function('a', 'b', 'return a + b');

adder(2, 6);  // 8
```

## 1.3 Boolean

- Boolean 객체는 원시 타입 boolean을 위한 래퍼 객체임.(Boolean 생성자 함수로 Boolean 객체를 생성할 수 있음.)

```jsx
var foo = new Boolean(true);    // true
var foo = new Boolean('false'); // true

var foo = new Boolean(false); // false
var foo = new Boolean();      // false
var foo = new Boolean('');    // false
var foo = new Boolean(0);     // false
var foo = new Boolean(null);  // false
```

- Boolean 객체와 원시 타입 boolean을 혼동하기 쉬움.(Boolean 객체는 true/false를 포함하고 있는 객체임.)

```jsx
var x = new Boolean(false);
if (x) { // x는 객체로서 존재한다. 따라서 참으로 간주된다.
  // . . . 이 코드는 실행된다.
}
```

## **1.4 Number**

- [Number](https://poiemaweb.com/js-number)

## **1.5 Math**

- [Math](https://poiemaweb.com/js-math)

## **1.6 Date**

- [Date](https://poiemaweb.com/js-date)

## **1.7 String**

- [Date](https://poiemaweb.com/js-string)

## **1.8 RegExp**

- [RegExp](https://poiemaweb.com/js-regexp)

## **1.9 Array**

- [Array](https://poiemaweb.com/js-array)

## **1.10 Error**

- Error 생성자는 error 객체를 생성함.
- error 객체의 인스턴스는 런타임 에러가 발생하였을 때 throw됨.

```jsx
try {
  // foo();
  throw new Error('Whoops!');
} catch (e) {
  console.log(e.name + ': ' + e.message);
}
```

- Error에 관련한 객체
  - EvalError
  - InternalError
  - RangeError
  - ReferenceError
  - SyntaxError
  - TypeError
  - URIError

## 1.11 Symbol

- Symbol은 변경 불가능한 원시 타입으로 Symbol 객체는 원시 타입 Symbol 값을 생성함.

## 1.12 원시 타입과 래퍼객체

- 정적 프로퍼티, 메소드는 해당 인스턴스를 생성하지 않아도 사용할 수 있고 prototype에 속해있는 메소드는 해당 prototype을 상속받은 인스턴스가 있어야만 사용할 수 있음.
  - 하지만 원시 타입 값에 대해 표준 빌트인 객체의 메소드를 호출하면 정상적으로 작동함.

```jsx
var str = 'Hello world!';
var res = str.toUpperCase();
console.log(res); // 'HELLO WORLD!'

var num = 1.5;
console.log(num.toFixed()); // 2
```

- 원시 타입 값에 대해 표준 빌트인 객체의 메소드를 호출할 때 원시 타입 값은 연관된 객체(Wrapper 객체)로 일시 변환되기 때문에 가능함.(메소드 호출이 종료되면 객체로 변환된 원시 타입 값은 다시 원시 타입 값으로 복귀함.)
- Wrapper 객체는 String, Number, Boolean이 있음.

# 2. 호스트 객체

- 호스트 객체는 브라우저 환경에서 제공하는 window, XmlHttpRequest, HTMLElement 등의 DOM 노드 객체와 같이 호스트 환경에 정의된 객체를 말함.
- 브라우저에서 동작하는 환경과 브라우저 외부에서 동작하는 환경의 자바스크립트는 다른 호스트 객체를 사용할 수 있음.

## 2.1 전역 객체

- 전역 객체는 모든 객체의 유일한 최상위 객체를 의미함.

## 2.2 BOM

- 브라우저 객체 모델은 브라우저 탭 또는 브라우저 창의 모델을 생성함.

- 최상위 객체는 window 객체로 현재 브라우저 창 또는 탭을 표현하는 객체임.(이 객체의 자식 객체 들은 브라우저의 다른 기능들을 표현함.)

  ![BOM.png](https://prod-files-secure.s3.us-west-2.amazonaws.com/510cd684-c9a0-45bd-b45d-b35ad6027628/514bccef-e738-4cb2-be25-6ffcc4da8329/BOM.png)

## 2.3 DOM

- 문서 객체 모델은 현재 웹페이지의 모델을 생성함.

- 최상위 객체는 document 객체로 전체 문서를 표현함.(이 객체의 자식 객체들은 문서의 다른 요소들을 표현함.)

  ![DOM.png](https://prod-files-secure.s3.us-west-2.amazonaws.com/510cd684-c9a0-45bd-b45d-b35ad6027628/6d86078e-9fe6-4aa4-8d7b-14c3ac36a736/DOM.png)