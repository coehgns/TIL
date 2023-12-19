# JS Strict mode

# 1. strict mode란?

- strict mode는 자바스크립트 언어의 문법을 적용하여 무시되던 오류를 발생시킬 가능성이 높거나 자바스크립트 엔진의 최적화 작업에 문제를 일으킬 수 있는 코드에 대해 명시적인 에러를 발생시킴.

# 2. strict mode의 적용

- strict mode를 적용하려면 전역역의 선두 또는 함수 몸체의 선두에 ‘use strict ‘;를 추가함.
- 전역의 선두에 추가하면 스크립트 전체에 strict mode가 적용됨.

```jsx
// 전역에 strict mode의 적용하는 것은 바람직하지 않다!
'use strict';

function foo() {
  x = 10; // ReferenceError: x is not defined
}
foo();
```

- 함수 몸체의 선두에 추가하면 해당 함수와 중첩된 내부 함수에 strict mode가 적용됨.
- 코드의 선두에 strict mode를 위치시키지 않으면 제대로 동작하지 않음.

# 3. 전역에 strict mode를 적용하는 것은 피해야함.

- 스크립트 단위로 적용된 strict mode는 다른 스크립트에 영향을 주지 않고 자신의 스크립트에 한정되어 적용됨.
- 외부 서드 파티 라이브러리를 사용하는 경우 라이브러리가 non-strict mode일 경우도 있기 때문에 전역에 strict mode를 적용하는 것은 바람직하지 않음.(즉시 실행 함수로 스크립트 전체를 감싸서 스코프를 구분하고 즉시 실행 함수의 선두에 strict mode를 적용하면 됨.)

# 4. 함수 단위로 strict mode를 적용하는 것도 피해야함.

- 함수 단위로 strict mode를 적용할 수 있는데 어떤 함수는 strict mode를 적용하고 어떤 함수는 strict mode를 적용하지 않는 것은 바람직하지 않음.
- strict mode가 적용된 함수가 참조할 함수 외부의 컨텍스트에 strict mode를 적용하지 않는다면 문제가 발생할 수 있음.
- strict mode는 즉시 실행 함수로 감싼 스크립트 단위로 적용하는 것이 바람직함.

# 5. strict mode가 발생시키는 에러

## 5.1 암묵적 전역 변수

- 선언하지 않은 변수를 참조하면  ReferenceError가 발생함.

```jsx
(function () {
  'use strict';

  x = 1;
  console.log(x); // ReferenceError: x is not defined
}());
```

## 5.2 변수, 함수, 매개변수의 삭제

```jsx
(function () {
  'use strict';

  var x = 1;
  delete x;
  // SyntaxError: Delete of an unqualified identifier in strict mode.

  function foo(a) {
    delete a;
    // SyntaxError: Delete of an unqualified identifier in strict mode.
  }
  delete foo;
  // SyntaxError: Delete of an unqualified identifier in strict mode.
}());
```

## 5.3 매개변수 이름의 중복

- 중복된 함수 파라미터 이름을 사용하면 SyntaxError가 발생함.

```jsx
(function () {
  'use strict';

  //SyntaxError: Duplicate parameter name not allowed in this context
  function foo(x, x) {
    return x + x;
  }
  console.log(foo(1, 2));
}());
```

## 5.4 with 문의 사용

- with 문을 사용하면 SyntaxError가 발생함.

```jsx
(function () {
  'use strict';

  // SyntaxError: Strict mode code may not include a with statement
  with({ x: 1 }) {
    console.log(x);
  }
}());
```

## 5.5 일반 함수의 this

- 생성자 함수가 아닌 일반 함수 내부에서는 this를 사용할 필요가 없음.(에러 발생X)