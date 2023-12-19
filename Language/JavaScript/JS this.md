# JS this

this는 인스턴스 자신을 가리키는 참조변수임.(this가 객체 자신에 대한 참조 값을 가지고 있음.)

this는 주로 매개변수와 객체 자신이 가지고 있는 멤버변수명이 같을 경우 구분하기 위해서 사용됨.

해당 함수 호출 방식에 따라 this에 바인딩되는 객체가 달라짐.

## 함수 호출 방식과 this 바인딩

자바스크립트는 함수 호출 방식에 의해 this에 바인딩할 어떤 객체가 동적으로 결정됨.

함수의 상위 스코프를 결정하는 방식인 렉시컬 스코프는 함수를 선언할 때 결정됨.

함수의 호출하는 방식

함수 호출

메소드 호출

생성자 함수 호출

apply/call/bind 호출

## 1. 함수 호출

전역 객체는 전역 스코프를 갖는 전역변수를 프로퍼티로 소유함.

글로벌 영역에 선언한 함수는 전역객체의 프로퍼티로 접근할 수 있는 전역 변수의 메소드임.

JavaScript

복사

캡션



var ga = 'Global variable'; console.log(ga); console.log(window.ga); function foo() {  console.log('invoked!'); } window.foo();



기본적으로 this는 전역객체에 바인딩됨.

JavaScript

복사

캡션



function foo() {  console.log("foo's this: ",  this);  // window  function bar() {    console.log("bar's this: ", this); // window  }  bar(); } foo();



메소드의 내부 함수일 경우에도 this는 전역객체에 바인딩됨.

JavaScript

복사

캡션



var value = 1; var obj = {  value: 100,  foo: function() {    console.log("foo's this: ",  this);  // obj    console.log("foo's this.value: ",  this.value); // 100    function bar() {      console.log("bar's this: ",  this); // window      console.log("bar's this.value: ", this.value); // 1    }    bar();  } }; obj.foo();



내부함수는 일반 함수, 메소드, 콜백함수 어디에서 선언되었든 관계없이 this는 전역객체를 바인딩함.

내ㅁ부함수의 this가 전역ㄱ객체를 참조하는 것을 회피하는 방법

JavaScript

복사

캡션



var value = 1; var obj = {  value: 100,  foo: function() {    var that = this;  // Workaround : this === obj     console.log("foo's this: ",  this);  // obj    console.log("foo's this.value: ",  this.value); // 100    function bar() {      console.log("bar's this: ",  this); // window      console.log("bar's this.value: ", this.value); // 1       console.log("bar's that: ",  that); // obj      console.log("bar's that.value: ", that.value); // 100    }    bar();  } }; obj.foo();



![img](notion://www.notion.so/image/https%3A%2F%2Fprod-files-secure.s3.us-west-2.amazonaws.com%2F510cd684-c9a0-45bd-b45d-b35ad6027628%2Fd29f1aa3-e6aa-4944-995b-1a1207f11890%2FFunction_Invocation_Pattern.png?table=block&id=9f79fa2c-fbaa-46e0-a418-139e6c8c1b6a&spaceId=510cd684-c9a0-45bd-b45d-b35ad6027628&width=2000&userId=f4300f36-5424-46cc-8d1c-b19f0c3dd9c2&cache=v2)









자바스크립트는 this를 명시적으로 바인딩할 수 있는 apply, call, bind 메소드를 제공함.

## 2. 메소드 호출

함수가 객체의 프로퍼티 값이면 메소드로서 호출됨.(ㅁ메소드 내부의 this는 해당 메소드를 소유한 객체에 바인딩됨.

JavaScript

복사

캡션



var obj1 = {  name: 'Lee',  sayName: function() {    console.log(this.name);  } } var obj2 = {  name: 'Kim' } obj2.sayName = obj1.sayName; obj1.sayName(); obj2.sayName();



![img](notion://www.notion.so/image/https%3A%2F%2Fprod-files-secure.s3.us-west-2.amazonaws.com%2F510cd684-c9a0-45bd-b45d-b35ad6027628%2F58c7dbea-4934-42cd-a08f-563ce0e41b9a%2FMethod_Invocation_Pattern.png?table=block&id=4a8e8838-0c6d-46bd-9e9e-2b4cc4f0cf41&spaceId=510cd684-c9a0-45bd-b45d-b35ad6027628&width=2000&userId=f4300f36-5424-46cc-8d1c-b19f0c3dd9c2&cache=v2)









## 3. 생성자 함수 호출

생성자 함수는 객체를 생성하는 역할을 함.(기존 함수에 new 연산자를 붙여서 호출하면 해당 함수는 생성자 함수로 동작함.)

JavaScript

복사

캡션



// 생성자 함수 function Person(name) {  this.name = name; } var me = new Person('Lee'); console.log(me); // Person&nbsp;{name: "Lee"} // new 연산자와 함께 생성자 함수를 호출하지 않으면 생성자 함수로 동작하지 않는다. var you = Person('Kim'); console.log(you); // undefined



new 연산자와 함께 생성자 함수를 호출하면 this 바인딩이 메소드나 함수 호출 떄와는 다르게 동작함.

### 3.1 생성자 함수 동작 방식

new 연산자와 함께 생성자 함수를 호출할 때 동작 순

빈 객체 생성 및 this 바인딩

생성자 함수의 코드가 실행되기 전 빈 객체가 생성됨. 이후 생성자 함수 내에서 사용되는 this는 빈 객체를 가리킴. 생성된 빈 객체는 생성자 함수의 prototype 프로퍼티가 가리키는 객체를 자신의 프로토타입 객체로 설정함.

this를 통한 프로퍼티 생성

생성된 빈 객체에 this를 사용하여 동적으로 프로퍼티나 메소드를 생성할 수 있음.

생성된 객체 반환

반환문이 없는 경우 this에 바인딩된 새로 생성한 객체가 반환됨.

반환문이 this가 아닌 다른 객체를 명시적으로 반환하는 경우 this가 아닌 해당 객체가 반환됨.

### 3.2 객체 리터럴 방식과 생성자 함수 방식의 차이

JavaScript

복사

캡션



// 객체 리터럴 방식 var foo = {  name: 'foo',  gender: 'male' } console.dir(foo); // 생성자 함수 방식 function Person(name, gender) {  this.name = name;  this.gender = gender; } var me  = new Person('Lee', 'male'); console.dir(me); var you = new Person('Kim', 'female'); console.dir(you);



객체 리터럴 방식과 생성자 함수 방식의 차이는 프로토타입 객체에 있음.

객체 리터럴 방식의 경우 생성된 객체의 프로토타입 객체는 Object.prototype임.

생성자 함수 방식의 경우 생성된 객체의 프로토타입 객체는 Person.prototype임.

### 3.3 생성자 함수에 new 연산자를 붙이지 않고 호출할 경우

일반함수와 생성자 함수에 특별한 형식적 차이는 없으며 함수에 new 연산자를 붙여서 호출하면 해당 함수는 생성자 함수로 동작함.

생성자 함수를 new 없이 호출하거나 일반 함수에 new를 붙여 호출하면 오류가 발생할 수 있음.(일반 함수와 생성자 함수의 호출시 this 바인딩 방식이 다르기 때문임.)

일반 함수를 호출하면 this는 전역객체에 바인딩되지만 new 연산자와 함께 생성자 함수를 호출하면 this는 생성자 함수가 암묵적으로 생성한 빈 객체에 바인딩됨.

# 4. apply/call/bind 호출

- this에 바인딩될 객체는 함수 호출 패턴에 의해 결정됨.

```jsx
func.apply(thisArg, [argsArray])

// thisArg: 함수 내부의 this에 바인딩할 객체
// argsArray: 함수에 전달할 argument의 배열
```

- apply() 메소드는 this를 특정 객체에 바인딩할 뿐 본질적인 기능은 함수 호출임.
- call() 메소드의 경우, apply()와 기능은 같지만 apply()의 두번째 인자에서 배열 형태로 넘긴 것을 가각 하나의 인자로 넘김.

```jsx
Person.apply(foo, [1, 2, 3]);

Person.call(foo, 1, 2, 3);
```

- apply()와 call() 메소드는 콜백 함수의 this를 위해서 사용되기도 함.