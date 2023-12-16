# JS Object

# 1. 객체(Object)란?

- 자바스크립트는 객체 기반의 스크립트 언어이며 자바스크립트를 이루고 있는 거의 모든 것이 객체임.(원시 타입을 제외한 나머지 값들은 모두 객체임.)
- 자바스크립트의 객체는 키와 값으로 구성된 프로퍼티들의 집합임.(프로퍼티의 값으로 자바스크립트에서 사용할 수 있는 모든 값을 사용할 수 있음.)
- 프로퍼티 값으로 함수를 사용할 수도 있으며 프로퍼티 값이 함수일 경우 일반 함수와 구분하기 위해 메소드라고 부름.
- 객체는 데이터를 의미하는 프로퍼티와 데이터를 참조하고 조작할 수 있는 동작을 의미하는 메소드로 구성된 집합임.

## 1.1 프로퍼티

- 프로퍼티는 프로퍼티 키(이름)와 프로퍼티 값으로 구성됨.(프로퍼티 키로 유일하게 식별 가능. 프로퍼티 키는 프로퍼티를 식별하기 위한 식별자.)
- 프로퍼티 키의 명명 규칙과 프로퍼티 값으로 사용할 수 있는 값.
  - 프로퍼티 키 : 빈 문자열을 포함하는 모든 문자열 또는 symbol 값
  - 프로퍼티 값 : 모든 값
- 프로퍼티 키에 문자열이나 symbol 값 이외의 값을 지정하면 암묵적으로 타입이 변환되어 문자열이 됨.
- 객체는 프로퍼티를 열거할 때 순서 보장 X

## 1.2 메소드

- 프로퍼티 값이 함수일 경우, 일반 함수와 구분하기 위해 메소드라고 부름.(객체에 제한되어 있는 함수를 의미.)

# 2. 객체 생성 방법

- 자바스크립트는 프로토타입 기반 객체 지향 언어로서 클래스라는 개념이 없고 별도의 객체 생성 방법이 존재함.

## 2.1 객체 리터럴

- 클래스 기반 객체 지향 언어와 비교할 때 매우 간편하게 객체를 생성할 수 있음.
- 중괄호({})를 사용하여 객체를 생성하는데 {} 내에 1개 이상의 프로퍼티를 기술하면 해당 프로퍼티가 추가된 객체를 생성할 수 있음.( {} 내에 아무것도 기술하지 않으면 빈 객체가 생성됨.)

```jsx
var emptyObject = {};
console.log(typeof emptyObject); // object

var person = {
  name: 'Lee',
  gender: 'male',
  sayHello: function () {
    console.log('Hi! My name is ' + this.name);
  }
};

console.log(typeof person); // object
console.log(person); // {name: "Lee", gender: "male", sayHello: ƒ}

person.sayHello(); // Hi! My name is Lee
```

## 2.2 Object 생성자 함수

- new 연산자와 Object 생성자 함수를 호출하여 빈 객체를 생성할 수 있음.(빈 객체 생성 이후 프로퍼티 또는 메소드를 추가하여 객체를 완성하는 방법임.)
- 생성자(constructor) 함수란 new 키워드와 함께 객체를 생성하고 초기화 하는 함수를 말함.(생성자 함수를 통해 생성된 객체를 인스턴스(instance)라고 함.)
- 일반 함수와 생성자 함수를 구분하기 위해 생성자 함수의 이름은 파스칼 케이스를 사용함.
- 객체가 소유하고 있지 않은 프로퍼티 키에 값을 할당하면 해당 객체에 프로퍼티를 추가하고 값을 할당함.(이미 존재하는 프로퍼티 키에 새로운 값을 할당하면 프로퍼티 값은 할당한 값으로 변경됨.)

```jsx
// 빈 객체의 생성
var person = new Object();
// 프로퍼티 추가
person.name = 'Lee';
person.gender = 'male';
person.sayHello = function () {
  console.log('Hi! My name is ' + this.name);
};

console.log(typeof person); // object
console.log(person); // {name: "Lee", gender: "male", sayHello: ƒ}

person.sayHello(); // Hi! My name is Lee
```

- 객체 리터럴 방식으로 생성된 객체는 결국 빌트인 함수인 Object 생성자 함수로 객체를 생성하는 것을 단순화시킨 축약 표현임.

## 2.3 생성자 함수

- 생성자 함수를 사용하면 마치 객체를 생성하기 위한 템플릿처럼 사용하여 프로퍼티가 동일한 객체 여러 개를 간편하게 생성할 수 있음.

```jsx
// 생성자 함수
function Person(name, gender) {
  this.name = name;
  this.gender = gender;
  this.sayHello = function(){
    console.log('Hi! My name is ' + this.name);
  };
}

// 인스턴스의 생성
var person1 = new Person('Lee', 'male');
var person2 = new Person('Kim', 'female');

console.log('person1: ', typeof person1);
console.log('person2: ', typeof person2);
console.log('person1: ', person1);
console.log('person2: ', person2);

person1.sayHello();
person2.sayHello();
```

- 생성자 함수 이름은 대문자로 시작하여 생성자 함수임을 인식하도록 도움을 줌.
- 프로퍼티 또는 메소드명 앞에 기술한 this는 생성자 함수가 생성한 인스턴스를 가리킴.
- this에 연결되어 있는 프로퍼티와 메소드는 public(외부에서 참조 가능)함.
- 생성자 함수 내에서 선언된 일반 변수는 private(외부에서 참조 불가능)함.(생성자 함수 내부에서는 접근이 가능하나 외부에서 접근할 수 없음.)

```jsx
function Person(name, gender) {
  var married = true;         // private
  this.name = name;           // public
  this.gender = gender;       // public
  this.sayHello = function(){ // public
    console.log('Hi! My name is ' + this.name);
  };
}

var person = new Person('Lee', 'male');

console.log(typeof person); // object
console.log(person); // Person { name: 'Lee', gender: 'male', sayHello: [Function] }

console.log(person.gender);  // 'male'
console.log(person.married); // undefined
```

- 자바스크립트의 생성자 함수는 이름 그대로 객체를 생성하는 함수임.
- 생성자 함수를 선언하고 new 연산자를 붙여서 호출하면 해당 함수는 생성자 함수로 동작함.(생성자 함수가 아닌 일반 함수에 new 연산자를 붙여 호출하면 생성자 함수처럼 동작할 수 있음.)
- new 연산자와 함께 함수를 호출하면 this 바인딩이 다르게 동작함.

# 3. 객체 프로퍼티 접근

## 3.1 프로퍼티 키

- 프로퍼티 키는 문자열을 지정함.(프로퍼티 키에 문자열이나 symbol 값 이외의 값을 지정하면 암묵적으로 타입이 변환되어 문자열이 됨.)
- 프로퍼티 키는 문자열이므로 따옴표를 사용함.
- 프로퍼티 값은 모두 값과 표현식이 올 수 있으며 프로퍼티 값이 함수인 경우 이를 메소드라고 함.

```jsx
var person = {
  'first-name': 'Ung-mo',
  'last-name': 'Lee',
  gender: 'male',
  1: 10,
  function: 1 // OK. 하지만 예약어는 사용하지 말아야 한다.
};

console.log(person);
```

- 프로퍼티 키 first-name에는 반드시 따옴표를 사용해야 하지만 first_name에는 생략 가능함.(fisrt-name은 자바스크립트에서 사용 가능한 유효한 이름이 아니라 ‘-’ 연산자가 있는 표현식이기 때문.)
- 표현식을 프로퍼티 키로 사용하려면 키로 사용할 표현식을 대괄호로 묶어야 함.

## 3.2 프로퍼티 값 읽기

- 객체의 프로퍼티 값에 접근하는 방법은 마칩표 표기법과 대괄호 표기법이 있음.
- 프로퍼티 이름이 유효한 자바스크립트 이름이 아니거나 예약어인 경우 프로퍼티 값은 대괄호 표기법으로 읽어야 함.(대괄호 내에 들어가는 포르퍼티 이름은 반드시 문자열이어야 함.)
- 객체에 존재하지 않는 프로퍼티를 참조하면 undefined를 반환함.

```jsx
var person = {
  'first-name': 'Ung-mo',
  'last-name': 'Lee',
  gender: 'male',
};

console.log(person.age); // undefined
```

## 3.3 프로퍼티 값 갱신

- 객체가 소유하고 있는 프로퍼티에 새로운 값을 할당하면 프로퍼티 값은 갱신됨.

```jsx
var person = {
  'first-name': 'Ung-mo',
  'last-name': 'Lee',
  gender: 'male',
};

person['first-name'] = 'Kim';
console.log(person['first-name'] ); // 'Kim'
```

## 3.4 프로퍼티 동적 생성

- 객체가 소유하고 있지 않은 프로퍼티 키에 값을 할당하면 주어진 키와 값으로 프로퍼티를 생성하여 객체에 추가함.

```jsx
var person = {
  'first-name': 'Ung-mo',
  'last-name': 'Lee',
  gender: 'male',
};

person.age = 20;
console.log(person.age); // 20
```

## 3.5 프로퍼티 삭제

- delete 연산자를 사용하면 객체의 프로퍼티를 삭제할 수 있음.(피연산자가 프로퍼티 키여야 함.)

```jsx
var person = {
  'first-name': 'Ung-mo',
  'last-name': 'Lee',
  gender: 'male',
};

delete person.gender;
console.log(person.gender); // undefined

delete person;
console.log(person); // Object {first-name: 'Ung-mo', last-name: 'Lee'}
```

## 3.6 for-in 문

- for-in 문을 사용ㅎ아면 객체에 포함된 모든 프로퍼티에 대해 루프를 수행할 수 있음.)

```jsx
var person = {
  'first-name': 'Ung-mo',
  'last-name': 'Lee',
  gender: 'male'
};

// prop에 객체의 프로퍼티 이름이 반환된다. 단, 순서는 보장되지 않는다.
for (var prop in person) {
  console.log(prop + ': ' + person[prop]);
}

/*
first-name: Ung-mo
last-name: Lee
gender: male
*/

var array = ['one', 'two'];

// index에 배열의 경우 인덱스가 반환된다
for (var index in array) {
  console.log(index + ': ' + array[index]);
}

/*
0: one
1: two
*/
```

- for-in 문은 객체의 문자열 키를 순회하기 위한 문법임.
- for-in 문을 배열에 사용하지 않는 것이 좋은 이유.
  - 객체의 경우 프로퍼티의 순서가 보장되지 않음.(원래 객체의 프로퍼티에는 순서가 없기 때문.)
  - 배열 요소들만 순회하지 않음.

```jsx
// 배열 요소들만을 순회하지 않는다.
var array = ['one', 'two'];
array.name = 'my array';

for (var index in array) {
  console.log(index + ': ' + array[index]);
}

/*
0: one
1: two
name: my array
*/
```

- for-in 문의 단점을 극복하기 위해 ES6에서 for-of 문이 추가 됨.

```jsx
const array = [1, 2, 3];
array.name = 'my array';

for (const value of array) {
  console.log(value);
}

/*
1
2
3
*/

for (const [index, value] of array.entries()) {
  console.log(index, value);
}

/*
0 1
1 2
2 3
*/
```

- for-in 문은 객체의 프로퍼티를 순회하기 위해 사용하고 for-of 문은 배열의 요소를 순회하기 위해 사용함.

# 4. Pass-by-reference

- object type을 객체 타입 또는 참조 타입이라고 함.
- 참조 타입이란 객체의 모든 연산이 실제 값이 아닌 참조값으로 처리됨을 의미함.
- 객체는 프로퍼티를 변경, 추가, 삭제가 가능하므로 변경 가능한 값이라고 할 수 있음.
- 객체 타입은 런타임에 메모리 공간을 확보하고 메모리의 힙 영역에 저장됨.
- 원시 타입은 값으로 복사되어 전달되는데 이를 pass-by-value라고 함.

```jsx
// Pass-by-reference
var foo = {
  val: 10
}

var bar = foo;
console.log(foo.val, bar.val); // 10 10
console.log(foo === bar);      // true

bar.val = 20;
console.log(foo.val, bar.val); // 20 20
console.log(foo === bar);      // true
```

- 변수 foo는 객체 자체를 저장하고 있는 것이 아니라 생성된 객체의 참조값을 저장하고 있음.

- 변수 foo, bar 모두 동일한 객체를 참조하고 있음. 두 변수 모두 변경된 객체의 프로퍼티 값을 참조하게 됨.

  ![pass-by-ref.png](https://prod-files-secure.s3.us-west-2.amazonaws.com/510cd684-c9a0-45bd-b45d-b35ad6027628/42f92f12-232f-4fbb-8e83-21f9b172f237/pass-by-ref.png)

  ```jsx
  var foo = { val: 10 };
  var bar = { val: 10 };
  
  console.log(foo.val, bar.val); // 10 10
  console.log(foo === bar);      // false
  
  var baz = bar;
  
  console.log(baz.val, bar.val); // 10 10
  console.log(baz === bar);      // true
  ```

  - 변수 foo와 변수 bar는 내용은 같지만 별개의 객체를 생성하여 참조값을 할당하였으므로 두 변수의 어드레스는 동일하지 않음.

  - 변수 baz에는 변수 bar의 값을 할당하였으므로 두 변수 baz와 bar는 동일한 참조값을 저장하고 있음.

    ![pass-by-ref-2.png](https://prod-files-secure.s3.us-west-2.amazonaws.com/510cd684-c9a0-45bd-b45d-b35ad6027628/74beafd2-ebba-47a2-ae13-5955d025da9e/pass-by-ref-2.png)

  ```jsx
  var foo = { val: 10 };
  var bar = { val: 10 };
  
  console.log(foo.val, bar.val); // 10 10
  console.log(foo === bar);      // false
  
  var baz = bar;
  
  console.log(baz.val, bar.val); // 10 10
  console.log(baz === bar);      // true
  ```

# 5. Pass-by-value

- 원시 타입은 값으로 전달됨.(값이 복사되어 전달) 이를 pass-by-value라고 함.(원시 타입은 값이 한번 정해지면 변경할 수 없음.)
- 이들 값은 런타임에 메모리의 스택 영역에 고정된 메모리 영역을 점유하고 저장됨.

```jsx
// Pass-by-value
var a = 1;
var b = a;

console.log(a, b);    // 1  1
console.log(a === b); // true

a = 10;
console.log(a, b);    // 1  10
console.log(a === b); // false
```

- 변수 a는 원시 타입인 숫자 타입 1을 저장하고 있음.
- 참조 타입으로 저장되는 것이 아니라 값 자체가 저장되게 됨. 변수 b에 변수 a를 할당할 경우, 변수 a의 값 1은 복사되어 변수 b에 저장됨.

# 6. 객체의 분류

![object.png](https://prod-files-secure.s3.us-west-2.amazonaws.com/510cd684-c9a0-45bd-b45d-b35ad6027628/3aadc1b3-3150-48f9-b5d8-7100f8e718d3/object.png)

- Built-in Object는 웹페이지 등을 표현하기 위한 공통의 기능을 제공함.(웹페이지가 브라우저에 의해 로드되자마자 바로 사용 가능.)
- Built-in Object 구분
  - Standard Built-in Objects (or Global Objects)
  - BOM(Browser Object Model)
  - DOM(Document Object Model)
- Standard Built-in Objects를 제외한 BOM과 DOM을 Natibe object라고 분류하기도 함.
- 사용자가 생성한 객체를 Host Object라고 함.