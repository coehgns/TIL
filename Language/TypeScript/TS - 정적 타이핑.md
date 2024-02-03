# TS - 정적 타이핑

------

# 타입 선언

- 타입은 소문자, 대문자를 구별하므로 주의가 필요함.

```tsx
// string: 원시 타입 문자열 타입
let primieveStr: string;
primitevStr = 'hello';  // OK
// 원시 타입 문자열 타입에 객체를 할당함.
primiteveStr = new String('hello');  //Error

//String: String 생성자 함수로 생성된 String 래퍼 객체 타입
let objectStr: String;
objecStr = 'hello';  // OK
objectStr = new String('hello');  //OK
```

- string 타입은 원시 타입인 문자열 타입을 의미함.
- 대문자로 시작하는 String 타입은 String 생성자 함수로 생성된 String 래퍼 객체 타입을 의미함.
- string 타입에 String 타입을 할당하면 에러가 발생함. (String 타입에는 string 타입을 할당할 수 있음.)

```tsx
// Date 타입
const today: Date = new Date();

// HTMLElement 타입
const elem: HTMLElement - document.getElementById('myId');

class Person { }
// Person 타입
const person: Person = new Person();
```

------

# 정적 타이핑

- 변수를 선언할 때 변수에 할당할 값의 타입에 따라 사전에 타입을 명시적으로 선언하여야 하며 선언한 타입에 맞는 값을 할당해야하는 것을 정적 타이핑이라고 함.
- (자바스크립트는 동적타입언어 혹은 느슨한 타입 언어임. 동적 타입 언어는 타입 추론에 의해 변수의 타입이 결정된 후에도 같은 변수에 여러 타입의 값을 교차하여 할당하는데 이를 동적 타이핑이라고 함.

```jsx
var foo;

console.log(typeof foo);  // undifend

foo = null;
console.log(typeof foo);  // object

foo = {};
console.log(typeof foo);  // object

foo = 3;
console.log(typeof foo);  // number

foo = 3.14;
console.log(typeof foo);  // number

foo = "Hi there";
console.log(typeof foo);  // string

foo = true;
console.log(typeof foo);  // boolean
```

- TypeScript의 가장 독특한 특징은 정적 타이핑을 지원한다는 것임.
- 정적 타입 언언느 타입을 명시적으로 선언하며, 타입이 결정된 후에는 타입을 변경할 수 없음.

```tsx
let foo: string,    // 문자열 타입
    bar: number,    // 숫자 타입
    baz: boolean;   // 불리언 타입

foo = 'Hello';
bar = 123;
baz = 'true';   // error: Type '"true"' is not assignable to type 'boolean'.
```

- 정적 타이핑은 변수는 물론 함수의 매개변수와 반환값에도 사용할 수 있음.

```tsx
function add(x: number, y: number): number {
  return x + y;
}

console.log(add(10, 10)); //20
console.log(add('10', '10'));
// error TS2345: Argument of type '"10"' is not assignable to parameter of type 'number'.
```

------

# 타입 추론

- 타입 선언을 생략하면 값이 할당되는 과정에서 동적으로 타입이 결정되는데 이를 타입 추론이라고 함.

```tsx
let foo = 123; // foo는 number 타입
```

- TypeScript는 정적 타입 언어이므로 타입 추론으로 타입이 결정된 이후, 다른 타입의 값을 할당하면 에러가 발생함.

```tsx
let foo = 123; // foo는 number 타입
foo = 'hi';    // error: Type '"hi"' is not assignable to type 'number'.
```

- 타입 선언을 생략하고 값도 할당하지 않아서 타입을 추론할 수 없으면 any타입이 됨.
- any타입의 변수는 어떤 타입의 값도 재할당이 가능함.

```tsx
let foo;  // let foo: any와 동치

foo = 'Hello';
console.log(typeof foo); // string

foo = true;
console.log(typeof foo); // boolean
```

------

# 타입 캐스팅

- 기존의 타입에서 다른 타입으로 캐스팅하려면 as 키워드를 사용하거나 <> 연산자를 사용할 수 있음.

```tsx
const $input = document.querySelector('input["type="text"]');
// => $input: Element | null

const val = $input.value;
// TS2339: Property 'value' does not exist on type 'Element'.
```

- document.querySelector 메서드는 Element | null 타입의 값을 반환함. 위 예제의 $input은 Element | null 타입임.
- 이때 $input.value를 실행하면 Element 또는 null 타입에는 value라는 프로퍼티가 존재하지 않으므로 컴파일 에러가 발생함.
- value 프로퍼티는 Element 타입의 하위 타입인 HTMLInputElement 타입에만 존재함. 따라서 타입 캐스팅이 필요함

```tsx
const $input = document.querySelector('input["type="text"]') as HTMLInputElement;
const val = $input.value;
```

- 또는 타입 캐스팅을 위해 as 키워드 대신 <> 연산자를 사용할 수도 있음.

```tsx
const $input = <HTMLInputElement>document.querySelector('input["type="text"]');
const val = $input.value;
```

------

## 참고 자료

- https://poiemaweb.com/typescript-typing

------