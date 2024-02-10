# JS - Spread 문법

# Spread 문법

- Spread 문법(Spread Syntax, …)은 대상을 개별 요소로 분리함. Spread 문법의 대상은 이터러블이어야 함.

## 1. 함수의 인수로 사용하는 경우

- ES6의 Spread 문법(…)을 사용한 배열을 인수로 함수에 전달하면 배열의 요소를 분해하여 순차적으로 파라미터에 할당함.

```jsx
// ES6
function foo(x, y, z) {
  console.log(x);  // 1
  console.log(y);  // 2
  console.log(z);  // 3
}

const arr = [1, 2, 3];

/* ...[1, 2, 3]는 [1, 2, 3]을 개별 요소로 분리함.(-> 1, 2, 3)
foo(...arr);
```

- Rest 파라미터는 Spread 문법을 사용하여 파라미터를 정의한 것을 의미함.
- Rest 파라미터는 반드시 마지막 파라미터여야 하지만 Spread 문법을 사용한 인수는 자유롭게 사용할 수 있음.

```jsx
// ES6
function foo(v, w, x, y, z) {
  console.log(v); // 1
  console.log(w); // 2
  console.log(x); // 3
  console.log(y); // 4
  console.log(z); // 5
}

// ...[2, 3]는 [2, 3]을 개별 요소로 분리한다(→ 2, 3)
// spread 문법에 의해 분리된 배열의 요소는 개별적인 인자로서 각각의 매개변수에 전달된다.
foo(1, ...[2, 3], 4, ...[5]);
```

## 2. 배열에서 사용하는 경우

- Spread 문법을 배열에서 사용하면 보다 간결하고 가독성 좋게 표현할 수 있음.

### 2.1 concat

- Spread 문법을 사용하면 배열 리터럴 만으로 기존 배열의 요소를 새로운 배열 요소의 일부로 만들 수 있음.

### 2.2 push

```jsx
// Es6
const arr1 = [1, 2, 3];
const arr2 = [4, 5, 6];

// ...arr2는 [4, 5, 6]을 개별 요소로 분리한다
arr1.push(...arr2); // == arr1.push(4, 5, 6);

console.log(arr1); // [ 1, 2, 3, 4, 5, 6 ]
```

### 2.3 splice

```jsx
// ES6
const arr1 = [1, 2, 3, 6];
const arr2 = [4, 5];

// ...arr2는 [4, 5]을 개별 요소로 분리한다
arr1.splice(3, 0, ...arr2); // == arr1.splice(3, 0, 4, 5);

console.log(arr1); // [ 1, 2, 3, 4, 5, 6 ]
```

### copy

```jsx
// ES6
const arr = [1, 2, 3];
// ...arr은 [1, 2, 3]을 개별 요소로 분리한다
const copy = [...arr];

console.log(copy); // [ 1, 2, 3 ]

// copy를 변경한다.
copy.push(4);

console.log(copy); // [ 1, 2, 3, 4 ]
// arr은 변경되지 않는다.
console.log(arr);  // [ 1, 2, 3 ]
```

- 이때 원본 배열의 각 요소를 얕은 복사(shallow copy)하여 새로운 복사본을 생성함.

## 참고 자료

- https://poiemaweb.com/es6-extended-parameter-handling