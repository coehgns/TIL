# JS - 매개변수 기본값

# 1. 매개변수 기본값(Default Parameter value)

- 함수는 매개변수의 개수와 인수의 개수를 체크하지 않음.
- 인수가 부족한 경우, 매개변수의 값은 undefined임.
- 그러므로 매개변수에 적절한 인수가 전달되었는지 함수 내부에서 확인할 필요가 있음.

```jsx
function sum(x, y) {
  x = x || 0;
  y = y || 0;

  return x + y;
}

console.log(sum(1));    // 1
console.log(sum(1, 2)); // 3
```

- ES6에서는 매개변수 기본값을 사용하여 함수 내에서 수행하던 인수 체크 및 초기화를 간소화할 수 있음.

```jsx
function sum(x = 0, y = 0) ...
```

- 매개변수 기본값은 함수 정의 시 선언한 매개변수 개수를 나타내는 함수 객체의 length 프로퍼티와 arguments 객체에 영향을 주지 않음.

```jsx
function foo(x, y = 0) {
  console.log(arguments);
}

console.log(foo.length);  // 1
 
sum(1);      // Arguments { '0':1 }
sum(1, 2);   // Arguments { '0':1, '1': 2 }
```

## 참고 자료

- https://poiemaweb.com/es6-extended-parameter-handling