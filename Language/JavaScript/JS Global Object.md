# JS Global Object

- 전역 객체는 모든 객체의 유일한 최상위 객체를 의미함.

```jsx
// in browser console
this === window // true

// in Terminal
node
this === global // true
```

- 전역 객체는 실행 컨텍스트에 컨트롤이 들어가기 이전에 생성이 되며 constructor가 없기 때문에 new 연산자를 이용하여 새롭게 생성할 수 없음.(개발자가 전역 객체를 생성하는 것은 불가능함.)
- 전역 객체는 전역 스코프를 갖게 됨.
- 전역 객체의 자식 객체를 사용할 때 전역 객체의 기술을 생략할 수 있음.
- 사용자가 정의한 변수와 전역 객체의 자식 객체 이름이 충돌하는 경우 명확히 전역 객체를 기술하여 혼동을 방지할 수 있음.

```jsx
function moveTo(url) {
  var location = {'href':'move to '};
  alert(location.href + url);
  // location.href = url;
  window.location.href = url;
}
moveTo('<http://www.google.com>');
```

- 전역 객체는 전역 변수를 프로퍼티로 가지게 됨.

```jsx
var ga = 'Global variable';
console.log(ga);
console.log(window.ga);
```

- 글로벌 영역에 선언한 함수도 전역 객체의 프로퍼티로 접근할 수 있음.

```jsx
function foo() {
  console.log('invoked!');
}
window.foo();
```

- Standard Built-in Objects도 역시 전역 객체의 자식 객체임.
- 전역 객체의 자식 객체를 사용할 때 전역 객체의 기술은 생략할 수 있으므로 표준 빌트인 객체도 전역 객체의 기술을 생략할 수 있

```jsx
// window.alert('Hello world!');
alert('Hello world!');
```

# 1. 전역 프로퍼티

- 전역 프로퍼티는 전역 객체의 프로퍼티를 의미함.
- 애플리케이션 전역에서 사용하는 값들을 나타내기 위해 사용함.
- 전역 프로퍼티는 간단한 값이 대부분이며 다른 프로퍼티나 메소드를 가지고 있지 않음.

## 1.1 infinity

- infinity 프로퍼티는 양/음의 무한대를 나타내는 숫자값 Infinity를 갖음.

```jsx
console.log(window.Infinity); // Infinity

console.log(3/0);  // Infinity
console.log(-3/0); // -Infinity
console.log(Number.MAX_VALUE * 2); // 1.7976931348623157e+308 * 2
console.log(typeof Infinity); // number
```

## 1.2 NaN

- NaN 프로퍼티는 숫자가 아님을 나타내는 숫자값 NaN을 갖음.
- NaN 프로퍼티는 Number.NaN 프로퍼티와 같음.

```jsx
console.log(window.NaN); // NaN

console.log(Number('xyz')); // NaN
console.log(1 * 'string');  // NaN
console.log(typeof NaN);    // number
```

## 1.3 undefined

- undefined 프로퍼티는 원시 타입 undefined를 값으로 갖음.

```jsx
console.log(window.undefined); // undefined

var foo;
console.log(foo); // undefined
console.log(typeof undefined); // undefined
```

# 2. 전역 함수

- 전역 함수는 애플리케이션 전역에서 호출할 수 있는 함수로서 전역 객체의 메소드임.

## 2.1 eval()

- 매개변수에 전달된 문자열 구문 또는 표현식을 평가 또는 실행함.
- 사용자로 부터 입력 받은 콘텐츠를 eval()로 실행하는 것은 보안에 매우 취약함

```jsx
eval(string)
// string: code 또는 표현식을 나타내는 문자열. 표현식은 존재하는 객체들의 프로퍼티들과 변수들을 포함할 수 있다.
```

## 2.2 isFinite()

- 매개변수에 전달된 값이 정상적인 유한수인지 검사하여 그 결과를 Boolean으로 반환함.
- 매개변수에 전달된 값이 숫자가 아닌 경우 숫자로 변환한 후 검사를 실행함.

```jsx
isFinite(testValue) // testValue: 검사 대상 값
```

## 2.3 isNaN()

- 매개변수에 전달된 값이 NaN인지 검사하여 그 결과를 Boolean으로 반환함.

```jsx
isNaN(testValue) // testValue: 검사 대상 값
```

# 2.4 parseFloat()

- 매개변수에 전달된 문자열을 부동소수점 숫자로 변환하여 반환함.

```jsx
parseFloat(string)
// string: 변환 대상 문자열
```

- 문자열의 첫 숫자만 반환되며 전후 공백은 무시됨.
- 첫문자를 숫자로 변환할 수 없다면 NaN을 반환함.

## 2.5 parselnt()

- 매개변수에 전달된 문자열을 정수형 숫자로 해석하여 반환함.(반환값은 언제나 10진수임.)

```jsx
parseInt(string, radix);
// string: 파싱 대상 문자열
// radix: 진법을 나타내는 기수(2 ~ 36, 기본값 10)
```

- 첫번째 매개변수에 전달된 값이 문자열이 아니면 문자열로 변환한 후 숫자로 해석하여 반환함.

```jsx
parseInt(10);     // 10
parseInt(10.123); // 10
```

- 2번째 매개변수에는 진법을 나타내는 기수를 지정할 수 있음.
- 기수를 생략하면 첫번째 매개변수에 전달된 문자열을 10진수로 해석하여 반환함.

```jsx
parseInt('10');     // 10
parseInt('10.123'); // 10
```

- 두번째 매개변수에 진법을 나타내는 기수를 지정하면 첫번째 매개변수에 전달된 문자열을 해당 기수의 숫자로 해석하여 반환함.

```jsx
parseInt('10', 2);  // 2진수 10 → 10진수 2
parseInt('10', 8);  // 8진수 10 → 10진수 8
parseInt('10', 16); // 16진수 10 → 10진수 16
```

- 두번쨰 매개변수에 진법을 나타내는 기수를 지정하지 않더라도 첫번째 매개변수에 전달된 문자열이 “0x” 또는 “0X”로 시작한다면 16진수로 해석하여 반환함.

```jsx
parseInt('0x10'); // 16진수 10 → 10진수 16
```

- 두번째 매개변수에 진법을 나타내는 기수를 지정하지 않더라도 첫번째 매개변수에 전달된 문자열이 “0”로 시작한다면 8진수로 해석하지 않고 10진수로 해석함.
- 문자열을 8진수로 해석하려면 지수를 반드시 지정하여야 함.

```jsx
parseInt('010'); // 8진수 10으로 인식하지 않는다.
parseInt('010', 8); // 8진수 10 → 10진수 8
parseInt('10', 8); // 8진수 10 → 10진수 8
```

- parseInt는 첫번째 매개변수에 전달된 문자열의 첫번째 문자가 해당 지수의 숫자로 변환될 수 없다면 NaN을 반환함.

```jsx
parseInt('A0'));   // NaN
parseInt('20', 2); // NaN
```

## 2.6 encodeURI() / decodeURI()

- encodeURI()는 매개변수로 전달된 URI를 인코딩함.

  ![uri.png](https://prod-files-secure.s3.us-west-2.amazonaws.com/510cd684-c9a0-45bd-b45d-b35ad6027628/3eeb6490-cd6a-44e6-ab86-18fefaa16725/uri.png)

- 인코딩이란 URI의 문자들을 이스케이프 처리하는 것을 의미함.

- 이스케이프 처리

  - 네트워크를 통해 정보를 공유할 때 어떤 시스템에서도 읽을 수 있는 ASCII Character-set로 반환하는 것임.

- 이스케이프 처리 이유

  - URL 내에서 의미를 갖고 있는 문자나 URL에 올 수 없는 문자 또는 시스템에 의해 해석될 수 있는 문자를 이스케이프 처리하여 야기될 수 있는 문제를 예방하기 위함임.

- 알파벳, 0~9의 숫자, - _ . ! ~ * ‘ ( ) 들은 이스케이프 처리에서 제외됨.

## 2.7 ***\*encodeURIComponent() / decodeURIComponent()\****

- encodeURIComponent()는 매개변수로 전달된 URI component를 인코딩함.
- decodeURIComponent()는 매개변수로 전달된 URI component를 디코딩함.
- encodeURIComponent()는 인수를 쿼리스트링의 일부라고 간주해서 =, ?, &를 인코딩함.
- encodeURI()는 인수를 URI 전체라고 간주하며 파라미터 구분자인 =, ?, &를 인코딩하지 않음.

```jsx
encodeURIComponent(URI)
// URI: URI component(구성 요소)
decodeURIComponent(encodedURI)
// encodedURI: 인코딩된 URI component(구성 요소)
```