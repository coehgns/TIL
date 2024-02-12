# JS - 객체 리터럴 프로퍼티 기능 확장

# 1. 프로퍼티 축약 표현

- ES6에서는 프로퍼티 값으로 변수를 사용하는 경우, 프로퍼티 이름을 생략할 수 있음. 이때 프로퍼티 이름은 변수의 이름으로 자동 생성됨.

```jsx
// ES6
let x = 1, y = 2;

const obj = { x, y };

console.log(obj); // { x: 1, y:2 }
```

# 2. 프로퍼티 키 동적 생성

- 문자열 또는 문자열로 변환 가능한 값을 반환하는 표현식을 사용해 프로퍼티 키를 동적으로 생성할 수 있음.
- 프로퍼티 키로 사용할 표현식을 대괄호([…])로 묶어야 함. (이를 계산된 프로퍼티 이름이라고 함.)
- ES6에서는 객체 리터럴 내부에서도 프로퍼티 키를 동적으로 생성할 수 있음.

```jsx
// ES6
const prefix = 'prop';
let i = 0;

const obj = {
  [`${prefix}-${++i}`]: i,
  [`${prefix}-${++i}`]: i,
  [`${prefix}-${++i}`]: i
};

console.log(obj); // {prop-1: 1, prop-2: 2, prop-3: 3}
```

# 3. 메소드 축약 표현

- ES6에서는 메소드를 선언할 때, function 키워드를 생략한 축약 표현을 사용할 수 있음.

```jsx
// ES6
const obj = {
  name: 'Lee',
  // 메소드 축약 표현
  sayHi() {
    console.log('Hi! ' + this.name);
  }
};

obj.sayHi(); // Hi! Lee
```

# 4. ***\*proto\**** 프로퍼티에 의한 상속

- ES6에서는 객체 리터럴 내부에서 **proto** 프로퍼티를 직접 설정할 수 있음. (객체 리터럴에 의해 생성된 객체의 **proto** 프로퍼티에 다른 객체를 직접 바인딩하여 상속을 표현할 수 있음을 의미함.

```jsx
// ES6
const parent = {
  name: 'parent',
  sayHi() {
    console.log('Hi! ' + this.name);
  }
};

const child = {
  // child 객체의 프로토타입 객체에 parent 객체를 바인딩하여 상속을 구현한다.
  __proto__: parent,
  name: 'child'
};

parent.sayHi(); // Hi! parent
child.sayHi();  // Hi! child
```

## 참고 자료

- https://poiemaweb.com/es6-enhanced-object-property