# JS Proto Type

# 1. 프로토타입 객체

- 자바스크립트의 동작 원리를 이해하기 위해서는 프로토타입의 개념을 잘 이해하고 있어야 함.
- 부모 객체를 Prototype 객체 또는 줄여서 Prototype이라고 함.
- ProtoPrototype 객체는 생성자 함수에 의해 생성된 각각의 객체에 공유 프로퍼티를 제공하기 위해 사용함.

```jsx
var student = {
  name: 'Lee',
  score: 90
};

// student에는 hasOwnProperty 메소드가 없지만 아래 구문은 동작한다.
console.log(student.hasOwnProperty('name')); // true

console.dir(student);
```

- ECMAScript spec에서는 자바스크립트의 모든 객체는 [[Prototype]]이라는 인터널 슬롯을 가짐.
  - [[Prototype]]의 값은 null 또는 객체이며 상속을 구현하는데 사용됨.
  - [[Prototype] 객체의 데이터 프로퍼티는 get 액세스를 위해 상속되어 자식 객체의 프로퍼티처럼 사용할 수 있음.
- student 객체는 **proto** 프로퍼티로 자신의 부모 객체(프로토타입 객체)인 Object.prototype을 가리키고 있다.

```jsx
var student = {
  name: 'Lee',
  score: 90
}
console.log(student.__proto__ === Object.prototype); // true
```

# 2. [[Prototype]] vs prototype 프로퍼티

- 함수도 객체이므로 [[Prototype]] 인터널 슬롯을 갖음.(함수 객체는 일반 객체와는 달리 prototype 프로퍼티도 소유하게 됨.
- prototype 프로퍼티와 [[Prototype]]은 모두 프로토타입 객체를 가리키지만 관점의 차이가 있음.

```jsx
function Person(name) {
  this.name = name;
}

var foo = new Person('Lee');

console.dir(Person); // prototype 프로퍼티가 있다.
console.dir(foo);    // prototype 프로퍼티가 없다.
```

- [[Prototype]]

  - 함수를 포함한 모든 객체가 가지고 있는 인터널 슬롯임.
  - 객체의 입장에서 자신의 부모 역할을 하는 프로토타입 객체를 가리키며 함수 객체의 경우 Function.prototype을 가리킴.

  ```jsx
  console.log(Person.__proto__ === Function.prototype);
  ```

- prototype 프로퍼티

- 함수 객체만 가지고 있는 프로퍼티임.

- 함수 객체가 생성자로 사용될 때 이 함수를 통해 생성될 객체의 부모 역할을 하는 객체를 가리킴.

```jsx
console.log(Person.prototype === foo.__proto__);
```

# 3. constructor 프로퍼티

- 프로토타입 객체는 constructor 프로퍼티를 갖음.(constructor 프로퍼티는 객체의 입장에서 자신을 생성한 객체를 가리킴.)

```jsx
function Person(name) {
  this.name = name;
}

var foo = new Person('Lee');

// Person() 생성자 함수에 의해 생성된 객체를 생성한 객체는 Person() 생성자 함수이다.
console.log(Person.prototype.constructor === Person);

// foo 객체를 생성한 객체는 Person() 생성자 함수이다.
console.log(foo.constructor === Person);

// Person() 생성자 함수를 생성한 객체는 Function() 생성자 함수이다.
console.log(Person.constructor === Function);
```

# 4. Prototype chain

- 프로토타입 체인이란 특정 객체의 프로퍼티나 메소드에 접근하려고 할 때 해당 객체에 접근하려는 프로퍼티 또는 메소드가 없다면 [[Prototype]]이 가리키는 링크를 따라 자신의 부모 역할을 하는 프로토타입 객체의 프로퍼티나 메소드를 차례대로 검색하는 것을 말함.

## 4.1 객체 리터럴 방식으로 생성된 객체의 프로토타입 체인

- 객체 생성 방법
  - 객체 리터럴
  - 생성자 함수
  - Object() 생성자 함수
- 자바스크립트 엔진은 객체 리터럴로 객체를 생성하는 코드를 만나면 내부적으로 Object() 생성자 함수를 사용하여 객체를 생성함.
- Object() 생성자 함수도 함수이므로 일반 객체와 달리 prototype 프로퍼티가 있음.
- prototype 프로퍼티는 함수 객체가 생성자로 사용될 때 이 함수를 통해 생성된 객체의 프로토타입 객체를 가리킴.

![object_literal_prototype_chaining.png](https://prod-files-secure.s3.us-west-2.amazonaws.com/510cd684-c9a0-45bd-b45d-b35ad6027628/7945ba07-a278-405e-bdcc-7f04486fd284/object_literal_prototype_chaining.png)

- 객체 리터럴을 사용하여 객체를 생성한 경우 그 객체의 프로토타입 객체는 Object.prototype임.

## 4.2 생성자 함수로 생성된 객체의 프로토타입 체인

- 생성자 함수로 객체를 생성하기 위해서는 생성자 함수를 정의하여야 함.
- 함수 정의 방식
  - 함수선언식
  - 함수표현식
  - Function() 생성자 함수

```jsx
var square = function(number) {
  return number * number;
};
```

- 함수선언식, 함수표현식 모두 함수 리터럴 방식을 사용하는데 함수 리터럴 방식은 Function() 생성자 함수로 함수를 생성하는 것을 단순화 시킴.

| 객체 생성 방식       | 엔진의 객체 생성     | 인스턴스의 prototype 객체  |
| -------------------- | -------------------- | -------------------------- |
| 객체 리터럴          | Object() 생성자 함수 | Object.prototype           |
| Object() 생성자 함수 | Object() 생성자 함수 | Object.prototype           |
| 생성자 함수          | 생성자 함수          | 생성자 함수 이름.prototype |

![constructor_function_prototype_chaining.png](https://prod-files-secure.s3.us-west-2.amazonaws.com/510cd684-c9a0-45bd-b45d-b35ad6027628/c7b9715b-b727-4d51-ae29-4db1d9fbc6c2/constructor_function_prototype_chaining.png)

# 5. 프로토타입 객체의 확장

- 프로토타입도 일반 객체와 같이 프로퍼티를 추가/ 삭제할 수 있음.
- 추가/ 삭제된 프로퍼티는 즉시 프로토타입 체인에 반영됨.

# 6. 원시 타입의 확장

- 자바스크립트에서 원시 타입을 제외한 모든것은 객체임.
- 원시 타입으로 프로퍼티나 메소드를 호출할 때 원시 타입과 연관된 객체로 일시적으로 변환되어 프로토타입 객체를 공유하게 됨.
- 원시타입은 객체가 아니기 때문에 프로퍼티나 메소드를 직접 추가할 수 없음.

# 7. 프로토타입 객체의 변경

- 결전된 프로토타입 객체는 다른 임의의 객체로 변경할 수 있음.(부모 객체인 프로토타입을 동적으로 변경할 수 있다는 의미.)
- 프로토타입 객체를 변경하면
  - 프로토타입 객체 변경 시점 이전에 생성된 객체를 [[Prototype]]에 바인딩함.
  - 프로토타입 객체 변경 시점 이후에 생성된 객체를 [[Prototype]]에 바인딩함.

# 8. 프로토타입 체인 동작 조건

- 해당 객체에 프로퍼티가 없는 경우 프로토타입 체인이 동작함.
- 객체의 프로퍼티에 값을 할당하는 경우 프로토타입 체인이 동작하지 않음.(객체에 해당 프로퍼티가 있는 경우 값을 재할당하고 해당 프로퍼티가 없는 경우는 해당 객체에 프로퍼티를 동적으로 추가하기 때문임.)