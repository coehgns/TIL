# TS - ts명령어

------

```bash
// TypeScript 전역 설치
npm install -g typescript

// TypeScript 설치 확인
$tsc -v
```

- TypeSCript 컴파일러(tsc)는 TypeScript 파일(.ts)을 자바스크립트 파일로 트랜스파일링함. (TypeScript 컴파일러는 TypeScript 파일을 자바스크립트 파일로 변환하므로 컴파일보다는 트랜스파일링(Transpiling)이 보다 적절한 표현임.

------

```tsx
// person.ts
class Person {
  private name: string;

  constructor(name: string) {
    this.name = name;
  }

  sayHello() {
    return "Hello, " + this.name;
  }
}

const person = new Person('Lee');

console.log(person.sayHello());
```

- person.ts 파일을 트랜스파일링하려면 tsc 명령어 뒤에 트랜스파일링 대상 파일명을 지정함.(.ts는 생략 가능.

```bash
$tsc person
```

- 트랜스 파일링 실행결과 같은 디렉터리리에 자바스크립트 파일(person.js)이 생성됨.

```jsx
// person.js
var Person = /** @class */ (function () {
    function Person(name) {
        this.name = name;
    }
    Person.prototype.sayHello = function () {
        return "Hello, " + this.name;
    };
    return Person;
}());
var person = new Person('Lee');
console.log(person.sayHello());
```

- 만약 자바스크립트 버전을 변경하려면 컴파일 옵션에 —target 또는 -t를 사용함.

```bash
// ES6 버전으로 트랜스파일링 실행 옵션
$tsc person -t ES2015
// person.js
class Person {
    constructor(name) {
        this.name = name;
    }
    sayHello() {
        return "Hello, " + this.name;
    }
}
const person = new Person('Lee');
console.log(person.sayHello());
```

- Node.js REPL을 이용해 트랜스파일링된 person.js 실행

```bash
$node person
Hello, Lee
```

- tsc 옵션 설정 파일 생성

```bash
$tsc --init
message TS6071: Successfully created a tsconfig.json file.
```

- tsc 옵션 설정 파일인 tsconfig.json이 생성됨.

```json
{
  "compilerOptions": {
    /* Basic Options */
    // "incremental": true,                   /* Enable incremental compilation */
    "target": "es5",                          /* Specify ECMAScript target version: 'ES3' (default), 'ES5', 'ES2015', 'ES2016', 'ES2017', 'ES2018', 'ES2019' or 'ESNEXT'. */
    "module": "commonjs",                     /* Specify module code generation: 'none', 'commonjs', 'amd', 'system', 'umd', 'es2015', or 'ESNext'. */
    // "lib": [],
```

- tsc 명령어 뒤에 파일명을 지정하면 tsconfig.json이 무시됨.
- tsc 뒤에 파일명을 지정하지 않으면 프로젝트 폴더 내의 모든 TypeScript 파일이 모두 트랜스파일링됨.

```bash
$tsc
```

- --watch 또는 -w 옵션을 사용하면 트랜스파일링 대상 파일의 내용이 변경되었을 때 이를 감지하여 자동으로 트랜스파일링이 실행됨.

```bash
$tsc --watch
```

- tscofing.json에 watch 옵션을 추가할 수도 있음.

```bash
{
  // ...
  "watch": true
}
```

------

## 참고 자료

- https://poiemaweb.com/typescript-introduction

------