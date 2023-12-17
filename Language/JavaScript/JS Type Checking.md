# JS Type Checking

# 1. typeof

- 타입 연산자 typeof는 피연산자의 데이터 타입을 문자열로 반환함.

```jsx
typeof '';              // string
typeof 1;               // number
typeof NaN;             // number
typeof true;            // boolean
typeof [];              // object
typeof {};              // object
typeof new String();    // object
typeof new Date();      // object
typeof /test/gi;        // object
typeof function () {};  // function
typeof undefined;       // undefined
typeof null;            // object (설계적 결함)
typeof undeclared;      // undefined (설계적 결함)
```

# 2. Object.prototype.toString

- Object.prototype.toString 메소드는 객체를 나타내는 문자열을 반환함.

```jsx
var obj = new Object();
obj.toString(); // [object Object]
```

- [Function.prototype.call](http://Function.prototype.call) 메소드를 사용하면 모든 타입의 값의 타입을 알아낼 수 있음.

# 3. instanceof

- instanceof 연산자는 피연산자인 객체가 우항에 명시한 타입의 인스턴스인지 여부를 알려줌.
- 타입 연산자에는 instanceof를 제공함.

# 4. 유사 배열 객체

- 배열인지 체크하기 위해서는 Array.isaArray 메소드를 사용함.

```jsx
console.log(Array.isArray([]));    // true
console.log(Array.isArray({}));    // false
console.log(Array.isArray('123')); // false
```

- 유사 배열 겍체는 length 프로퍼티가 있으므로 순회할 수 있으며 call, apply 함수를 사용하여 배열의 메소드를 사용할 수도 있음.