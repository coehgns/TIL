# JS - Arrow function

# 1. 화살표 함수의 선언

- 화살표 함수는 function 키워드 대신 화살표(=>)를 사용하여 보다 간략한 방법으로 함수를 선언할 수 있음.
- 모든 경우 화살표 함수를 사용할 수 있는 것은 아님.

```jsx
// 기본 문법

// 매개 변수 지정 방법
     () => { ... }  // 매개변수가 없을 때
      x => { ... }  // 매개변수가 없을 때
   x,y) => { ... }  // 매개변수가 없을 때

// 함수 몸체 지정 방법
x => { return x * x }  // single line block
x => x * x             /* 함수 몸체가 한줄의 구문이라면 중괄호를 생략할 수 있으며
                       암묵적으로 return 됨. 위 표현과 동일. */

() => { return { a: 1 }; }
() => ({ a:1 })  // 위 표현과 동일. 객체 반환시 소괄호를 사용함.

() => {          //multi line block.
  const x = 10;
  return x * x;
};
```

# 2. 화살표 함수의 호출

- 화살표 함수는 익명함수로만 사용할 수 있음.
- 화살표 함수를 호출하기 위해서는 함수 표현식을 사용함.

```jsx
// ES5
var pow = function (x) { return x * x; };
console.log(pow(10)); // 100
// ES6
const pow = x => x * X;
console.log(pow(10)); // 100
```

- 또는 콜백 함수로 사용할 수 있음.

```jsx
// ES5
var arr = [1, 2, 3];
var pow = arr.map(function (x) { // x는 요소값
  return x * x;
});

console.log(pow); // [ 1, 4 ,9 ]
// ES6
const arr = [ 1, 2, 3 ]
const pow = arr.map(x => x * x);

console.log(pow); // [ 1, 4, 9 ] 
```

# 3. this

- function 키워드로 생성한 일반 함수와 화살표 함수의 가장 큰 차이점은 this임.

## 3.1 일반 함수의 this

- 자바스크립트의 경우 함수 호출 방식에 의해 this에 바인딩할 어떤 객체가 동적으로 결정됨.
- 함수를 선언할 때 this에 바인딩할 객체가 정적으로 결정되는 것이 아닌, **함수를 호출할 때 함수가 어떻게 호출되었는지에 따라** this에 바인딩할 객체가 동적으로 결정됨.
- 콜백 함수 내부의 this는 전역 객체 window를 가리킴.

## 3.2 화살표 함수의 this

- 화살표 함수는 함수를 선언할 때 this에 바인딩할 객체가 정적으로 결정됨.
- 화살표 함수의 this는 언제나 상위 스코프의 this를 가리킴. 이를 Lexical this라고 함.
- 화살표 함수는 call, apply, bind 메소드를 사용하여 this를 변경할 수 없음.

# 4. 화살표 함수를 사용해서는 안되는 경우

## 4.1 메소드

```jsx
// Bad
const person = {
  name: 'Lee',
  sayHi: () => console.log(`Hi ${this.name}`)
};

person.sayHi();  // Hi undefined
```

- 메소드로 정의한 화살표 함수 내부의 this는 메소드를 호출한 객체를 가리키지 않고 전역 객체 window를 가리킴. (화살표 함수로 메소드를 정의하는 것은 바람직하지 않음.)

```jsx
// Good
const person = {
  name: 'Lee',
  sayHi() { // === sayHi: function() {
    conesole.log(`Hi ${this.name}`);
  }
};

person.sayHi();  // Hi Lee
```

## 4.2 prototype

- 화살표 함수로 정의된 메소드를 prototype에 할당하는 경우도 동일한 문제가 발생함.

```jsx
// Bad
const person = {
  name: 'Lee',
};

Object.prototype.sayHi = () => console.log(`Hi ${this.name}`);

person.sayHi(); // Hi undefined
```

- 객체의 메소드를 정의하였을 때와 같은 문제가 발생함.
- prototype에 메소드를 할당하는 경우, 일반 함수를 할당함.

```jsx
// Good
const person = {
  name: 'Lee',
};

Object.prototype.sayHi = function() {
  console.log(`Hi ${this.name}`);
};

person.sayHi(); // Hi Lee
```

## 4.3 생성자 함수

- 화살표 함수는 생성자 함수로 사용할 수 없음.
- 생성자 함수는 prototype 프로퍼티를 가지며 prototype 프로퍼티가 가리키는 프로토타입 객체의 constructor를 사용함. 하지만 화살표 함수는 prototype 프로퍼티를 가지고 있지 않음.

```jsx
const Foo = () => {};

// 화살표 함수는 prototype 프로퍼티가 없다
console.log(Foo.hasOwnProperty('prototype')); // false

const foo = new Foo(); // TypeError: Foo is not a constructor
```

## 4.4 addEventListener 함수의 콜백 함수

- addEventListener 함수의 콜백 함수를 화살표 함수로 정의하면 this가 상위 컨택스트인 전역 객체 window를 가리킴.

## 참고 자료

- https://poiemaweb.com/es6-arrow-function