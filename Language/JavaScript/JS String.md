# JS String

- String 객체는 원시 타입인 문자열을 다룰 때 유용한 프로퍼티와 메소드를 제공하는 레퍼 객체임.
- 변수 또는 객체 프로퍼티가 문자열을 값으로 가지고 있다면 String 객체의 별도 생성 없이 String 객체의 프로퍼티와 메소드를 사용할 수 있음.
- 원시 타입 wrapeer 객체의 메소드를 사용할 수 있는 이유는 원시 타입으로 프로퍼티나 메소드를 호출할 때 원시 타입과 연관된 wrapper 객체로 일시적으로 변환되어 프로토타입 객체를 공유하게 되기 때문임.

```jsx
const str = 'Hello world!';
console.log(str.toUpperCase()); // 'HELLO WORLD!'
```

- 변수 str의 값이 일시적으로 wrapper 객체로 변환되었기 때문에 변수 str String.prototype.toUpperCase() 메소드를 호출할 수 있는 것임.

# 1. String Constructor

- String 객체는 String 생성자 함수를 통해 생성할 수 있음.(전달된 인자는 모두 문자열로 변환됨.)

```jsx
new String(value);
let strObj = new String('Lee');
console.log(strObj); // String {0: 'L', 1: 'e', 2: 'e', length: 3, [[PrimitiveValue]]: 'Lee'}

strObj = new String(1);
console.log(strObj); // String {0: '1', length: 1, [[PrimitiveValue]]: '1'}

strObj = new String(undefined);
console.log(strObj); // String {0: 'u', 1: 'n', 2: 'd', 3: 'e', 4: 'f', 5: 'i', 6: 'n', 7: 'e', 8: 'd', length: 9, [[PrimitiveValue]]: 'undefined'}
```

- new 연산자를 사용하지 않고 String 생성자 함수를 호출하면 String 객체가 아닌 문자열 리터럴을 반환함.

```jsx
var x = String('Lee');

console.log(typeof x, x); // string Lee
```

- 일반적으로 문자열을 사용할 때는 원시 타입 문자열을 사용함.

```jsx
const str = 'Lee';
const strObj = new String('Lee');

console.log(str == strObj);  // true
console.log(str === strObj); // false

console.log(typeof str);    // string
console.log(typeof strObj); // object
```

# 2. String Property

## 2.1 String.length

- 문자열 내의 문자 갯수를 반환함.(String 객체는 length 프로퍼티를 소유하고 있으므로 유사 배열 객체임.)

```jsx
const str1 = 'Hello';
console.log(str1.length); // 5

const str2 = '안녕하세요!';
console.log(str2.length); // 6
```

# 3. String Method

- String 객체의 모든 메소드는 언제나 새로운 문자열을 반환함.(문자열은 변경 불가능한 원시 값이기 때문.)

## 3.1 ***\*String.prototype.charAt(pos: number): string\****

- 인수로 전달한 index를 사용하여 index에 해당하는 위치의 문자를 반환함.
- index는 0 ~ (문자열의 길이 - 1) 사이의 정수임.
- index가 문자열의 범위를 벗어난 경우 빈문자열을 반환함.

![Untitled](https://prod-files-secure.s3.us-west-2.amazonaws.com/510cd684-c9a0-45bd-b45d-b35ad6027628/17943ecc-67f0-472a-b2ce-fc1b4e385a89/Untitled.png)

```jsx
const str = 'Hello';

console.log(str.charAt(0)); // H
console.log(str.charAt(1)); // e
console.log(str.charAt(2)); // l
console.log(str.charAt(3)); // l
console.log(str.charAt(4)); // o
// 지정한 index가 범위(0 ~ str.length-1)를 벗어난 경우 빈문자열을 반환한다.
console.log(str.charAt(5)); // ''

// 문자열 순회. 문자열은 length 프로퍼티를 갖는다.
for (let i = 0; i < str.length; i++) {
  console.log(str.charAt(i));
}

// String 객체는 유사 배열 객체이므로 배열과 유사하게 접근할 수 있다.
for (let i = 0; i < str.length; i++) {
  console.log(str[i]); // str['0']
}
```

## ***\*3.2 String.prototype.concat(…strings: string[]): string\****

- 인수로 전달한 1개 이상의 문자열과 연결하여 새로운 문자열을 반환함.
- concat 메소드를 사용하는 것보다는 + , += 할당 연산자를 사용하는 것이 성능상 유리하마.

```jsx
/**
 * @param {...string} str - 연결할 문자열
 * @return {string}
 */
str.concat(str1[,str2,...,strN])
console.log('Hello '.concat('Lee')); // Hello Lee
```

## ***\*3.3 String.prototype.indexOf(searchString: string, fromIndex=0): number\****

- 인수로 전달한 문자 또는 문자열을 대상 문자열에서 검색하여 처음 발견된 곳의 index를 반환함.(발견하지 못한 경우 -1을 반환함.)

```jsx
/**
 * @param {string} searchString - 검색할 문자 또는 문자열
 * @param {string} [fromIndex=0] - 검색 시작 index (생략할 경우, 0)
 * @return {number}
 */
str.indexOf(searchString[, fromIndex])
const str = 'Hello World';

console.log(str.indexOf('l'));  // 2
console.log(str.indexOf('or')); // 7
console.log(str.indexOf('or' , 8)); // -1

if (str.indexOf('Hello') !== -1) {
  // 문자열 str에 'hello'가 포함되어 있는 경우에 처리할 내용
}

// ES6: String.prototype.includes
if (str.includes('Hello')) {
  // 문자열 str에 'hello'가 포함되어 있는 경우에 처리할 내용
}
```

## ***\*3.4 String.prototype.lastIndexOf(searchString: string, fromIndex=this.length-1): number\****

- 인수로 전달한 문자 또는 문자열을 대상 문자열에서 검색하여 마지막으로 발견된 곳의 index를 반환함.(발견하지 못한 경우 -1을 반환함.)
- 2번째 인수가 전달되면 검색 시작 위치를 fromindex으로 이동하여 역방향으로 검색을 시작함.(검색 범위는 0 ~ fromIndex이며 반환값은 indexOf 메소드와 동일하게 발견된 곳의 index임.)

```jsx
/**
 * @param {string} searchString - 검색할 문자 또는 문자열
 * @param {number} [fromIndex=this.length-1] - 검색 시작 index (생략할 경우, 문자열 길이 - 1)
 * @return {number}
 */
str.lastIndexOf(searchString[, fromIndex])
```

![Untitled](https://prod-files-secure.s3.us-west-2.amazonaws.com/510cd684-c9a0-45bd-b45d-b35ad6027628/1c6e0f04-90b5-424e-bb05-bcdd4177f540/Untitled.png)

## ***\*3.5 String.prototype.replace(searchValue: string | RegExp, replaceValue: string | replacer: (substring: string, …args: any[]) => string): string): string\****

- 첫번째 인수로 전달한 문자열 또는 정규표현식을 대상 문자열에서 검색하여 두번째 인수로 전달한 문자열로 대체함.
- 원본 문자열은 변경되지 않고 결과가 반영된 새로운 문자열을 반환함.
- 검색된 문자열이 여럿 존재할 경우 첫번째로 검색된 문자열만 대체됨.

```jsx
/**
 * @param {string | RegExp} searchValue - 검색 대상 문자열 또는 정규표현식
 * @param {string | Function} replacer - 치환 문자열 또는 치환 함수
 * @return {string}
 */
str.replace(searchValue, replacer)
```

## ***\*3.6 String.prototype.split(separator: string | RegExp, limit?: number): string[]\****

- 첫번째 인수로 전달한 문자열 또는 정규표현식을 대상 문자열에서 검색하여 문자열을 구분한 후 분리된 각 문자열로 이루어진 배열을 반환함.(원본 문자열은 변경X)
- 인수가 없는 경우 대상 문자열 전체를 단일 요소로 하는 배열을 반환함.

```jsx
/**
 * @param {string | RegExp} [separator] - 구분 대상 문자열 또는 정규표현식
 * @param {number} [limit] - 구분 대상수의 한계를 나타내는 정수
 * @return {string[]}
 */
str.split([separator[, limit]])
```

## ***\*3.7 String.prototype.substring(start: number, end=this.length): string\****

- 첫번째 인수로 전달한 start 인덱스에 해당하는 문자부터 두번째 인자에 전달된 end 인덱스에 해당하는 문자의 바로 이전 문자까지를 모두 반환함.(첫번째 인수 < 두번째 인수의 관계가 성립됨.)

![Untitled](https://prod-files-secure.s3.us-west-2.amazonaws.com/510cd684-c9a0-45bd-b45d-b35ad6027628/7e9a0350-fd7f-4a08-ac3d-8dfc185be11c/Untitled.png)

- 첫번째 인수 > 두번째 인수 : 두 인수는 교환된다.
- 두번째 인수가 생략된 경우 : 해당 문자열의 끝까지 반환한다.
- 인수 < 0 또는 NaN인 경우 : 0으로 취급된다.
- 인수 > 문자열의 길이(str.length) : 인수는 문자열의 길이(str.length)으로 취급된다.

```jsx
/**
 * @param {number} start - 0 ~ 해당문자열 길이 -1 까지의 정수
 * @param {number} [end=this.length] - 0 ~ 해당문자열 길이까지의 정수
 * @return {string}
 */
str.substring(start[, end])
```

## ***\*3.8 String.prototype.slice(start?: number, end?: number): string\****

- String.prototype.substring과 동일함.(String.prototype.slice는 음수의 인수를 전달할 수 있음.)

## ***\*3.9 String.prototype.toLowerCase(): string\****

- 대상 문자열의 모든 문자를 소문자로 변경함.

```jsx
console.log('Hello World!'.toLowerCase()); // hello world!
```

## ***\*3.10 String.prototype.toUpperCase(): string\****

- 대상 문자열의 모든 문자를 대문자로 변경함.

```jsx
console.log('Hello World!'.toUpperCase()); // HELLO WORLD!
```

## 3.11 ***\*String.prototype.trim(): string\****

- 대상 문자열 양쪽 끝에 있는 공백 문자를 제거한 문자열을 반환함.

```jsx
const str = '   foo  ';

console.log(str.trim()); // 'foo'

// String.prototype.replace
console.log(str.replace(/\\s/g, ''));   // 'foo'
console.log(str.replace(/^\\s+/g, '')); // 'foo  '
console.log(str.replace(/\\s+$/g, '')); // '   foo'

// String.prototype.{trimStart,trimEnd} : Proposal stage 3
console.log(str.trimStart()); // 'foo  '
console.log(str.trimEnd());   // '   foo'
```

## 3.12 ***\*String.prototype.repeat(count: number): string\****

- 인수로 전달한 숫자만큼 반복해 연결한 새로운 문자열을 반환함.
- count가 0이면 빈 문자열을 반환하고 음수이면 RangeError를 발생시킴.

```jsx
console.log('abc'.repeat(0));   // ''
console.log('abc'.repeat(1));   // 'abc'
console.log('abc'.repeat(2));   // 'abcabc'
console.log('abc'.repeat(2.5)); // 'abcabc' (2.5 → 2)
console.log('abc'.repeat(-1));  // RangeError: Invalid count value
```

## ***\*3.13 String.prototype.includes(searchString: string, position?: number): boolean\****

- 인수로 전달한 문자열이 포함되어 있는지를 검사하고 결과를 불리언 값으로 반환함.
- 두번째 인수는 옵션으로 검색할 위치를 나타내는 정수임.

```jsx
const str = 'hello world';

console.log(str.includes('hello')); // true
console.log(str.includes(' '));     // true
console.log(str.includes('wo'));    // true
console.log(str.includes('wow'));   // false
console.log(str.includes(''));      // true
console.log(str.includes());        // false

// String.prototype.indexOf 메소드로 대체할 수 있다.
console.log(str.indexOf('hello')); // 0
```