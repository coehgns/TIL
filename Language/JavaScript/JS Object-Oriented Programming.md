# JS Object-Oriented Programming

# 1. 객체지향 프로그래밍 개요

- 객체지향 프로그래밍은 관계성있는 객체들의 집합이라는 관점으로 접근하는 소프트웨어 디자인으로 볼 수 있음.
- 각 객체는 메시지를 받을 수도 있고, 데이터를 처리할 수도 있으며, 또 다른 객체에게 메시지를 전달할 수도 있음.
- 객체지향 프로그래밍은 보다 유연하고 유지보수하기 쉬우며 확장성 측면에서도 유리한 프로그래밍을 하도록 의도되었고, 대규모 소프트웨어 개발에 널리 사용되고 있음.

# 2. 클래스 기반 vs. 프로토타입 기반

## 2.1 클래스 기반 언어

- 클래스 기반 언어는 클래스로 객체의 자료구조와 기능을 정의하고 생성자를 통해 인스턴스를 생성함.
- 클래스란 같은 종류의 집단에 속하는 속성과 행위를 정의한 것으로 객체지향 프로그램의 기본적인 사용자 정의 데이터형이라고 할 수 있음.

## 2.2 프로토타입 기반 언어

- 자바스크립트는 간혹 클래스가 없어서 객체지향이 아니라고 생각하는 사람들도 있으나 프로토타입 기반의 객체지향 언어임.
- 객체 생성 방법
  - 객체 리터럴
  - Object() 생성자 함수
  - 생성자 함수

```jsx
// 객체 리터럴
var obj1 = {};
obj1.name = 'Lee';

// Object() 생성자 함수
var obj2 = new Object();
obj2.name = 'Lee';

// 생성자 함수
function F() {}
var obj3 = new F();
obj3.name = 'Lee';
```

# 3. 생성자 함수와 인스턴스의 생성

- 자바스크립트는 생성자 함수와 new 연산자를 통해 인스턴스를 생성할 수 있음.

```jsx
// 생성자 함수(Constructor)
function Person(name) {
  // 프로퍼티
  this.name = name;

  // 메소드
  this.setName = function (name) {
    this.name = name;
  };

  // 메소드
  this.getName = function () {
    return this.name;
  };
}

// 인스턴스의 생성
var me = new Person('Lee');
console.log(me.getName()); // Lee

// 메소드 호출
me.setName('Kim');
console.log(me.getName()); // Kim
var me  = new Person('Lee');
var you = new Person('Kim');
var him = new Person('Choi');

console.log(me);  // Person { name: 'Lee', setName: [Function], getName: [Function] }
console.log(you); // Person { name: 'Kim', setName: [Function], getName: [Function] }
console.log(him); // Person { name: 'Choi', setName: [Function], getName: [Function] }
```

- 위와 같이 인스턴스를 생성하면 각각의 인스턴스에 메소드 setName, getName이 중복되어 생성됨.

# 4. 프로토타입 체인과 메소드의 정의

- 모든 객체는 프로토타입이라는 다른 객체를 가리키는 내부 링크를 가지고 있음.(프로토타입을 통해 직접 객체를 연결하는 것을 프로토타입 체인이라고 함.)
- 프로토타입을 이용하면 생성자 함수에 의해 생성된 모든 인스턴스는 프로토타입 체인을 통해 프로토타입 객체의 메소드를 참조할 수 있음.

# 5. 상속

- 상속은 코드 재사용의 관점에서 매우 유용함. 새롭게 정의할 클래스가 기존에 있는 클래스와 유사하다면 상속을 통해 다른 점만 구현하면 됨.
- 클래스 기반 언어에서 객체는 클래스의 인스턴스이며 클래스는 다른 클래스로 상속될 수 있음.
- 자바스크립트의 상속 구현 방식은 두 가지로 구분할 수 있는데 하나는 클래스 기반 언어의 상속 방식을 흉내 내는 것이고, 두번째는 프로토타입으로 상속을 구현하는 것임.

## 5.1 의사 클래스 패턴 상속

- 의사 클래스 패턴은 자식 생성자 함수의 prototype 프로퍼티를 부모 생성자 함수의 인스턴스로 교체하여 상속을 구현하는 방법임.(부모와 자식 모두 생성자 함수를 정의하여야 함.)

## 5.2 프로토타입 패턴 상속

- 프로토타입 패턴 상속은 Object.create 함수를 사용하여 객체에서 다른 객체로 직접 상속을 구현하는 방식임.
- 프로토타입 패턴은 new 연산자가 필요없으며, 생성자 링크도 파괴되지 않으며 객체 리터럴에도 사용할 수 있음.

# 6. 캡슐화(Encapsulation)와 모듈 패턴(Module Pattern)

- 캡슐화는 관련있는 멤버 변수와 메소드를 클래스와 같은 하나의 틀 안에 담고 외부에 공개될 필요가 없는 정보는 숨기는 것을 말함.(다른 말로 정보 은닉이라고도 함.)
- Java의 경우 클래스를 정의하고 그 클래스를 구성하는 멤버에 대하여 public 또는 private 등으로 한정할 수 있음.
- public으로 선언된 메소드 또는 데이터는 외부에서 사용이 가능하며 private으로 선언된 경우는 외부에서 참조할 수 없고 내부에서만 사용됨.