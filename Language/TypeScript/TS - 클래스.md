# TS - 클래스

# 클래스 정의 (Class Definition)

------

- ES6 클래스는 클래스 몸체에 메소드만을 포함할 수 있음.
- 클래스 몸체에 클래스 프로퍼티를 선언할 수 없고 반드시 생성자 내부에서 클래스 프로퍼티를 선언하고 초기화함.
- TypeScript 클래스는 클래스 몸체에 클래스 프로퍼티를 사전 선언하여야 함.

```tsx
// person.ts
class Person {
  // 클래스 프로퍼티를 사전 선언해야 함.
  name: string;

  constructor(name: string) {
    // 클래스 프로퍼티수에 값을 할당
    this.name = name;
  }
  walk() {
    console.log('${this.name} is walking.');
  }
}

const person = new Person('Lee');
person.walk(); // Lee is walking
```

# 접근 제한자

------

- TypeScript 클래스는 클래스 기반 객체 지향 언어가 지원하는 접근 제한가 public, private, protected를 지원하며 의미 또한 기본적으로 동일함.
- TypeScript는 접근 제한자를 생략한 클래스 프로퍼티와 메소드는 암묵적으로 pubic이 선언됨.
- public으로 지정하고자 하는 멤버 변수와 메소드는 접근 제한자를 생략함.

| 접근 가능성      | public | protected | private |
| ---------------- | ------ | --------- | ------- |
| 클래스 내부      | ◯      | ◯         | ◯       |
| 자식 클래스 내부 | ◯      | ◯         | ✕       |
| 클래스 인스턴스  | ◯      | ✕         | ✕       |

```tsx
class Foo {
  public x: string;
  protected y: string;
  private z: string;
  
  constructor(x: string, y: string, z: string) {
    // public, protected, private 접근 제한자 모두 클래스 내부에서 참조 가능함.
    this.x = x;
    this.y = y;
    this.z = z;
  }
}

const foo = new Foo('x','y','z');

// public 접근 제한자는 클래스 인스턴스를 통해 클래스 외부에서 참조 가능함.
console.log(foo.x);

// protected 접근 제한자는 클래스 인스턴스를 통해 클래스 외부에서 참조할 수 없음.
console.log(foo.y);
// error TS2445: Property 'y' is protected and only accessible within class 'Foo' and its subclasses.

// private 접근 제한자는 클래스 인스턴스를 통해 클래스 외부에서 참조할 수 없음.
console.log(foo.z);
// error TS2341: Property 'z' is private and only accessible within class 'Foo'.

class Bar extends Foo {
  constructor(x: string, y: string, z: string) {
    super(x, y, z);

    // public 접근 제한자는 자식 클래스 내부에서 참조 가능하다.
    console.log(this.x);

    // protected 접근 제한자는 자식 클래스 내부에서 참조 가능하다.
    console.log(this.y);

    // private 접근 제한자는 자식 클래스 내부에서 참조할 수 없다.
    console.log(this.z);
    // error TS2341: Property 'z' is private and only accessible within class 'Foo'.
  }
}
```

# 생성자 파라미터에 접근 제한자 선언

------

- 접근 제한자는 생성자 파라미터에도 선언할 수 있음.
- 접근 제한자가 사용된 생성자  파라미터는 암묵적으로 클래스 프로퍼티로 선언되고 생성자 내부에서 별도의 초기화가 없어도 암묵적으로 초기화가 수행됨.
- private 접근 제한자가 사용되면 클래스 내부에서만 참조 가능하고 public 접근 제한자가 사용되면 클래스 외부에서도 참조가 가능함.

```tsx
class Foo {
  /*
  접근 제한자가 선언된 생성자 파라미터 x는 클래스 프로퍼티로 선언되고 자동으로 초기화 됨.
  public이 선언되었으므로 x는 클래스 외부에서도 참조가 가능함.
  */
  constructor(public x: string) { }
}

const foo = new Foo('Hello');
console.log(foo);   // Foo { x: 'Hello' }
console.log(foo.x); // Hello

class Bar {
  /* 
  private이 선언되었으므로 x는 클래스 내부에서만 참조 가능함.
  */
  constructor(private x: string) { }
}

const bar = new Bar('Hello');

console.log(bar);  // Bar { x: 'Hello' }

// private이 선언된 bar.x는 클래스 내부에서만 참조 가능함
console.log(bar.x); // Property 'x' is private and only accessible within class 'Bar'.
```

- 생성자 파라미터에 접근 제한자를 선언하지 않으면 생성자 파라미터는 생성자 내부에서만 유효한 지역 변수가 되어 생성자 외부에서 참조가 불가능하게 됨.

```tsx
class Foo {
  // x는 생성자 내부에서만 유효한 지역 변수임.
  constructor(x: string) {
    console.log(x);
  }
}

const foo = new Foo('Hello');
console.log(foo);  // Foo {}
```

# readyonly 키워드

------

- TypeScript는 readonly 키워드를 사용할 수 있음.
- readonly가 선언된 클래스 프로퍼티는 선언 시 또는 생성자 내부에서만 값을 할당할 수 있음. (그 외에 경우에는 값을 할당할 수 없고 오직 읽기만 가능한 상태가 됨. 이를 이용하여 상수의 선언에 사용함.)

```tsx
class Foo {
  private readonly MAX_LEN: number = 5;
  private readonly MSG: string;

  constructor() {
    this.MSG = 'hello';
  }

  log() {
    // readonly가 선언된 프로퍼티는 재할당이 금지됨.
    this.MAX_LEN = 10;
    this.MSG = 'Hi';

    console.log('MAX_LEN: ${this.MAX+LEN}');  // MAX_LEN: 5
    console.log('MSG: ${this.MSG}');  // MSG: hello
  }
}

new Foo().log();
```

# static 키워드

------

- ES6 클래스에서 static 키워드는 클래스의 정적(static) 메소드를 정의함.
- 정적 메소드는 클래스의 인스턴스가 아닌 클래스 이름으로 호출함.
- 클래스의 인스턴스를 생성하지 않아도 호출할 수 있음.

```tsx
class Foo {
  construcrot(prop) {
    this.prop = prop;
  }
 
  static staticMethod() {
    /*
    정적 메소드는 this를 사용할 수 없음.
    정적 메소드는 내부에서 this를 클래스의 인스턴스가 아닌 클래스 자신을 가리킴.
    */
    return 'staticMethod'
  }
  
  prototypeMethod() {
    return this.prop; 
  }
}

// 정적 메소드는 클래스 이름으로 호출함.
console.log(Foo.staticMethod());

const foo = new Foo(123);
// 정적 메소드는 인스턴스로 호출할 수 없음.
console.log(foo.staticMethod()); // Uncaught TypeError: foo.staticMethod is not a function
```

- Typescript에서는 static 키워드를 클래스 프로퍼티에도 사용할 수 있음.

```tsx
class Foo {
  // 생성된 인스턴스의 갯수
  static instanceCounter = 0;
  constructor() {
    // 생성자가 호출될 때마다 카운터를 1씩 증가시킴.
    Foo.instanceCounter++;
  }
}

var foo1 = new Foo();
var foo2 = new Foo();

console.log(Foo.instanceCounter(); // 2
console.log(foo2.instanceCounter(); //error TS2339: Property 'instanceCounter' does not exist on type 'Foo'.
```

# 추상 클래스

------

- 추상 클래스(abstract class)는 하나 이상의 추상 메소드를 포함하며 일반 메소드도 포함할 수 있음.
- 추상 메소드는 내용이 없이 메소드 이름과 타입만이 선언된 메소드를 말함.
- 추상 클래스를 선언할 때와 정의할 때는 abstract 키워드를 사용하며, 직접 인스턴스를 생성할 수 없고 상속만을 위해 사용됨.
- 추상 클래스를 상속한 클래스는 추상 클래스의 추상 메소드를 반드시 구현해야 함.

```tsx
abstract class Animal {
  // 추상 메소드
  abstract makeSound(): void;
  // 일반 메소드
  move(); void {
    console.log('roaming the earth...');
  }
}

// 직접 인스턴스를 생성할 수 없음.
// new Animal();

class Dog extends Animal {
  makeSound() {
    console.log('bowwow~~');
  }
}

const myDog = new Dog();
myDog.makeSound();
myDog.move();
```

------

## 참고 자료

- https://poiemaweb.com/typescript-class

------