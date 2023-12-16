# JS Immuntability

- Immuntability(변경불가성)는 객체가 생성된 이후 그 상태를 변경할 수 없는 디자인 패턴을 의미함.(Immutability는 함수형 프로그래밍의 핵심 원리임.)
- 객체는 참조 형태로 전달하고 전달 받음.

# 1. immutable value vs. mutable value

- javascript의 원시 타입은 변경 불가능한 값임.
  - boolean
  - null
  - undefined
  - number
  - string
  - symbol
- 원시 타입 이외의 모든 값은 객체 타입이며 객체 타입은 변경 가능한 값임.(객체는 새로운 값을 다시 만들 필요 없이 직접 변경이 가능함.)

```jsx
var str = 'Hello';
str = 'world';
```

- 첫번째 구문이 실행되면 메모리에 문자열 ‘Hello’가 생성되고 식별자 str은 메모리에 생성된 문자열 ‘Hello’의 메모리 주소를 가리킴.
- 두번째 구문이 실행되면 이전에 생성된 문자열 ‘Hello’를 수정하는 것이 아닌 새로운 문자열 ‘world’를 메모리에 생성하고 식별자 str을 이것을 가리킴.

```jsx
var statement = 'I am an immutable value'; // string은 immutable value

var otherStr = statement.slice(8, 17);

console.log(otherStr);   // 'immutable'
console.log(statement);  // 'I am an immutable value'
```

- 2행에서 string 객체의 slice() 메소드는 statement 변수에 저장된 문자열을 변경하는 것이 아니라 새로운 문자열을 생성하여 반환하고 있음.(문자열은 변경할 수 없는 immutable value이기 때문)

```jsx
var arr = [];
console.log(arr.length); // 0

var v2 = arr.push(2);    // arr.push()는 메소드 실행 후 arr의 length를 반환
console.log(arr.length); // 1
```

- v는 새로운 배열을 가지게 될 것인데 객체인 arr은 push 메소드에 의해 update되고 v2에는 배열의 새로운 length 값이 반환됨.
- 처리 후 배열의 메소드 push()는 직접 대상 배열을 변경함.(배열은 객체이고 객체는 immutable value가 아닌 변경 가능한 값이기 때문.)

```jsx
var user = {
  name: 'Lee',
  address: {
    city: 'Seoul'
  }
};

var myName = user.name; // 변수 myName은 string 타입이다.

user.name = 'Kim';
console.log(myName); // Lee

myName = user.name;  // 재할당
console.log(myName); // Kim
```

- user.name의 값을 변경했지만 변수 myName의 값은 변경되지 않음. 변수 myName에 user.name을 할당했을 때 user.name의 참조를 할당하는 것이 아니라 immutable한 값’Lee’가 메모리에 새로 생성되고 myName은 이것을 참조하기 때문임.

```jsx
var user1 = {
  name: 'Lee',
  address: {
    city: 'Seoul'
  }
};

var user2 = user1; // 변수 user2는 객체 타입이다.

user2.name = 'Kim';

console.log(user1.name); // Kim
console.log(user2.name); // Kim
```

- 위의 경우 객체 user2의 name 프로퍼티에 새로운 값을 할당하면 객체는 변경 불가능한 값이 아니므로 객체 user2는 변경됨.

  ![immutability.png](https://prod-files-secure.s3.us-west-2.amazonaws.com/510cd684-c9a0-45bd-b45d-b35ad6027628/fb714118-84a7-493e-bca3-2a5e59201fd6/immutability.png)

# 2. 불변 데이터 패턴 (immutable dat pattern)

- 객체의 방어적 복사(defensive copy)

  ```
  Object.assign
  ```

- 불변객체화를 통한 객체 변경 방지

  ```
  Object.freeze
  ```

## 2.1 Object.assign

- Object.assign은 타킷 객체로 소스 객체의 프로퍼티를 복사함.(소스 객체의 프로퍼티와 동일한 프로퍼티를 가진 타켓 객체의 프로퍼티들은 소스 객체의 프로퍼티를 덮어쓰기됨.)

```jsx
// Syntax
Object.assign(target, ...sources)
// Copy
const obj = { a: 1 };
const copy = Object.assign({}, obj);
console.log(copy); // { a: 1 }
console.log(obj == copy); // false

// Merge
const o1 = { a: 1 };
const o2 = { b: 2 };
const o3 = { c: 3 };

const merge1 = Object.assign(o1, o2, o3);

console.log(merge1); // { a: 1, b: 2, c: 3 }
console.log(o1);     // { a: 1, b: 2, c: 3 }, 타겟 객체가 변경된다!

// Merge
const o4 = { a: 1 };
const o5 = { b: 2 };
const o6 = { c: 3 };

const merge2 = Object.assign({}, o4, o5, o6);

console.log(merge2); // { a: 1, b: 2, c: 3 }
console.log(o4);     // { a: 1 }
```

- Object.assign을 사용하여 기존 객체를 변경하지 않고 객체를 복사하여 사용할 수 있음.
- 객체 내부의 객체는 Shallow copy됨.

```jsx
const user1 = {
  name: 'Lee',
  address: {
    city: 'Seoul'
  }
};

// 새로운 빈 객체에 user1을 copy한다.
const user2 = Object.assign({}, user1);
// user1과 user2는 참조값이 다르다.
console.log(user1 === user2); // false

user2.name = 'Kim';
console.log(user1.name); // Lee
console.log(user2.name); // Kim

// 객체 내부의 객체(Nested Object)는 Shallow copy된다.
console.log(user1.address === user2.address); // true

user1.address.city = 'Busan';
console.log(user1.address.city); // Busan
console.log(user2.address.city); // Busan
```

- user1과 user2는 어드레스를 공유하지 않았으므로 한 객체를 변경하여도 다른 객체에 아무런 영향을 주지 않음.

## 2.2 Object.freeze

- Object.freeze()를 사용하여 불변 객체로 만들 수 있음.

```jsx
const user1 = {
  name: 'Lee',
  address: {
    city: 'Seoul'
  }
};

// Object.assign은 완전한 deep copy를 지원하지 않는다.
const user2 = Object.assign({}, user1, {name: 'Kim'});

console.log(user1.name); // Lee
console.log(user2.name); // Kim

Object.freeze(user1);

user1.name = 'Kim'; // 무시된다!

console.log(user1); // { name: 'Lee', address: { city: 'Seoul' } }

console.log(Object.isFrozen(user1)); // true
```

- 객체 내부의 객체는 변경 가능함.

```jsx
const user = {
  name: 'Lee',
  address: {
    city: 'Seoul'
  }
};

Object.freeze(user);

user.address.city = 'Busan'; // 변경된다!
console.log(user); // { name: 'Lee', address: { city: 'Busan' } }
```

- 내부 객체까지 변경 불가능하게 만들려면 Deep freeze를 해야 함.

```jsx
function deepFreeze(obj) {
  const props = Object.getOwnPropertyNames(obj);

  props.forEach((name) => {
    const prop = obj[name];
    if(typeof prop === 'object' && prop !== null) {
      deepFreeze(prop);
    }
  });
  return Object.freeze(obj);
}

const user = {
  name: 'Lee',
  address: {
    city: 'Seoul'
  }
};

deepFreeze(user);

user.name = 'Kim';           // 무시된다
user.address.city = 'Busan'; // 무시된다

console.log(user); // { name: 'Lee', address: { city: 'Seoul' } }
```

## 2.3 immutable.js

- immutable.js는 영구 불변 데이터 구조를 제공함.