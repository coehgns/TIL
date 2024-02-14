# JS - 디스트럭처링

# 1. 배열 디스트럭처링(Array destructuring)

- ES6의 배열 디스트럭처링은 배열의 각 요소를 배열로부터 추출하여 변수 리스트에 할당함.(추출/할당 기준은 배열의 인덱스임.)

```jsx
const arr = [1, 2, 3];

const [one, two, three] = arr;

console.log(one, two, three); // 1 2 3
```

- 배열 디스트럭처링을 위해서는 할당 연산자 왼쪽에 배열 형태의 변수 리스트가 필요함.

```jsx
let x, y, z;
[x, y, z] = [1, 2, 3];

// 위와 동일
let [x, y, z] = [1, 2, 3];
```

- 왼쪽의 변수 리스트와 오른쪽의 배열은 배열의 인덱스를 기준으로 할당함.

```jsx
let x, y, z;

[x, y] = [1, 2];
console.log(x, y); // 1 2

[x, y] = [1];
console.log(x, y); // 1 undefined

[x, y] = [1, 2, 3];
console.log(x, y); // 1 2

[x, , z] = [1, 2, 3];
console.log(x, z); // 1 3

// 기본값
[x, y, z = 3] = [1, 2];
console.log(x, y, z); // 1 2 3

[x, y = 10, z = 3] = [1, 2];
console.log(x, y, z); // 1 2 3

// spread 문법
[x, ...y] = [1, 2, 3];
console.log(x, y); // 1 [ 2, 3 ]
```

# 2. 객체 디스트럭처링 (Object destructuring)

- ES6의 객체 디스트럭처링은 객체의 각 프로퍼티를 객체로부터 추출하여 변수 리스트에 할당함.(할당 기준은 프로퍼티 이름(키)임.)

```jsx
const obj = { firstName: 'Ungmo', lastName: 'Lee' };

const { lastName, firstName } = obj;

console.log(firstName, lastName); // Ungmo Lee
```

- 객체 디스트럭처링을 위해서는 할당 연산자 왼쪽에 객체 형태의 변수 리스트가 필요함.

```jsx
// 프로퍼티 키가 prop1인 프로퍼티의 값을 변수 p1에 할당
// 프로퍼티 키가 prop2인 프로퍼티의 값을 변수 p2에 할당
const { prop1: p1, prop2: p2 } = { prop1: 'a', prop2: 'b' };
console.log(p1, p2); // 'a' 'b'
console.log({ prop1: p1, prop2: p2 }); // { prop1: 'a', prop2: 'b' }

// 아래는 위의 축약형이다
const { prop1, prop2 } = { prop1: 'a', prop2: 'b' };
console.log({ prop1, prop2 }); // { prop1: 'a', prop2: 'b' }

const { prop1, prop2, prop3 = 'c' } = { prop1: 'a', prop2: 'b' };
console.log({ prop1, prop2, prop3 }); // { prop1: 'a', prop2: 'b', prop3: 'c'
```

- 객체 디스트럭처링은 객체에서 프로퍼티 이름으로 필요한 프로퍼티 값만을 추추할 수 있음.

## 참고 자료

- https://poiemaweb.com/es6-destructuring