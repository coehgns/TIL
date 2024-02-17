# JS - Symbol

# 1. Symbol이란?

- 원시 타입(primitive date type)
  - Boolean
  - null
  - undefined
  - Number
- 객체 타입(Object type)
  - Object
- 심볼은 ES6에서 새롭게 추가된 7번째 타입으로 변경 불가능한 원시 타입의 값임.
- 심볼은 주로 이름의 충돌 위험이 없는 유일한 객체의 프로퍼티 키를 만들기 위해 사용함.

# 2. Symbol의 생성

- Symbol은 Symbol() 함수로 생성함.
- Symbol() 함수는 호출될 때마다 Symbol 값을 생성함. 이때 생성된 Symbol은 변경 불가능한 원시 타입.

```jsx
let mySymbol = Symbol();

console.log(mySymbol);        // Symbol()
console.log(typeof mySymbol); // symbol
```

- Symbol() 함수는 String, Number, Boolean과 같이 래퍼 객체를 생성하는 생성자 함수와는 달리 new 연산자를 사용하지 않음.
- Symbol() 함수에는 문자열을 인자로 전달할 수 있음. 이 문자열은 Symbol 생성에 어떠한 영향을 주지 않으며 다만 생성된 Symbol에 대한 설명으로 디버깅 용도로만 사용됨.

```jsx
let symbolWithDesc = Symbol('ungmo2');

console.log(symbolWithDesc);  // Symbol(ungmo2)
console.log(symbolWithDesc === Symbol('ungmo2'));  // false
```

# 3. Symbol의 사용

- 객체의 프로퍼티 키는 빈 문자열을 포함하는 모든 문자열로 만들 수 있음.
- Symbol 값도 객체의 프로퍼티 키로 사용할 수 있음.
- Symbol 값은 유일한 값이므로 Symbol 값을 키로 갖는 프로퍼티는 다른 어떠한 프로퍼티와도 충돌하지 않음.

# 4. Symbol 객체

- Symbol() 함수로 Symbol 값을 생성할 수 있었음.
- Symbol 객체는 프로퍼티와 메소드를 가지고 있음. Symbol 객체의 프로퍼티 중에 length와 prototype을 제외한 프로퍼티를 Well-known Symbol이라 부름.

## 4.1 Symbol.iterator

- Well-Known Symbol은 자바스크립트 엔진에 상수로 존재하며 자바스크립트 엔진은 Well-Know Symbol을 참조하여 일정한 처리를 함.
- Symbol.iterator를 프로퍼티 key로 사용하여 메소드를 구현하고 있는 빌트인 객체 (이터레이션 프로토콜을 준수하고 있으며 이터러이터를 반환함.)
  - Array Array.prototype[Symbol.iterator]
  - String String.prototype[Symbol.iterator]
  - Map Map.prototype[Symbol.iterator]
  - Set Set.prototype[Symbol.iterator]
  - DOM data structures NodeList.prototype[Symbol.iterator] HTMLCollection.prototype[Symbol.iterator]
  - arguments arguments[Symbol.iterator]

## 4.2 Symbol.for

- Symbol.for 메소드는 인자로 전달받은 문자열을 키로 사용하여 Symbol 값들이 저장되어 있는 전역 Symbol 레지스트리에서 해당 키와 일치하는 저장된 Symbol 값을 검색함.
- 검색에 성공하면 검색된 Symbol 값을 반환하고, 실패하면 새로운 Symbol 값을 생성하여 해당 키로 전역 Symbol 레지스트리에 저장한 후, Symbol 값을 반환함.
- Symbol.for 메소드는 하나의 Symbol을 생성하여 여러 모듈이 키를 통해 같은 Symbol을 공유할 수 있음.
- Symbol.for 메소드를 통해 생성된 Symbol 값은 반드시 키를 갖음.

## 참고 자료

- https://poiemaweb.com/es6-symbol