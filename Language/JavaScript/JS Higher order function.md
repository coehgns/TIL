# JS Higher order function

- 고차 함수는 함수를 인자로 전달받거나 함수를 결과로 반환하는 함수를 말함.(인자로 받은 함수를 필요한 시점에 호출하거나 클로저를 생성하여 반환.)

```jsx
// 함수를 인자로 전달받고 함수를 반환하는 고차 함수
function makeCounter(predicate) {
  // 자유 변수. num의 상태는 유지되어야 한다.
  let num = 0;
  // 클로저. num의 상태를 유지한다.
  return function () {
    // predicate는 자유 변수 num의 상태를 변화시킨다.
    num = predicate(num);
    return num;
  };
}

// 보조 함수
function increase(n) {
  return ++n;
}

// 보조 함수
function decrease(n) {
  return --n;
}

// makeCounter는 함수를 인수로 전달받는다. 그리고 클로저를 반환한다.
const increaser = makeCounter(increase);
console.log(increaser()); // 1
console.log(increaser()); // 2

// makeCounter는 함수를 인수로 전달받는다. 그리고 클로저를 반환한다.
const decreaser = makeCounter(decrease);
console.log(decreaser()); // -1
console.log(decreaser()); // -2
```

- 고차 함수는 외부 상태 변경이나 가변 데이터를 피하고 불변성을 지향하는 함수형 프로그래밍에 기반을 두고 있음.
- 함수형 프로그래밍은 순수 함수와 보조 함수의 조합을 통해 로직 내에 존재하는 조건문과 반복문을 제거하여 복잡성을 해결하고 변수의 사용을 억제하여 상태 변경을 피하려는 프로그래밍 패러다임임.
- 함수형 프로그래밍은 결국 순수 함수를 통해 부수 효과를 최대한 억제하여 오류를 피하고 프로그램의 안정성을 높이려는 노력의 한 방법이라고 할 수 있음.

------

- ✏️ 메소드는 `this`(원본 배열)를 변경함.
- 🔒 메소드는 `this`(원본 배열)를 변경하지 않음.

# 1. ***\*Array.prototype.sort(compareFn?: (a: T, b: T) => number): this ✏️\****

- 배열의 요소를 적절하게 정렬함. 원본 배열을 직접 변경하며 정렬된 배열을 반환함.
- 기본 정렬 순서는 문자열 Unicode 코드 포인트 순서에 따름.(배열의 요소를 일시적으로 문자열로 변환한 후 정렬함.)
- ex) 문자열 ‘1’의 Unicode 코드 포인트는 U+0031, 문자열 ‘2’의 Unicode 코드 포인트는 U+0032임.

------

- sort 메소드의 인자로 정렬 순서를 정의하는 비교 함수를 인수로 전달함.
- 비교 함수를 생략하면 배열의 각 요소는 일시적으로 문자열로 변환되어 Unicode 코드 포인트 순서에 따라 정렬됨.

# ***\*2. Array.prototype.forEach(callback: (value: T, index: number, array: T[]) => void, thisArg?: any): void 🔒\****

- forEach 메소드는 for 문 대신 사용할 수 있음.
- 배열을 순회하며 배열의 각 요소에 대하여 인자로 주어진 콜백함수를 실행한다. 반환값은 undefined임.
- 콜백 함수의 매개변수를 통해 배열 요소의 값, 요소 인덱스, forEach 메소드를 호출한 배열, 즉 this를 전달 받을 수 있음.
- forEach 메소드는 원본 배열(this)을 변경하지 않는다. 하지만 콜백 함수는 원본 배열(this)을 변경할 수는 있음.
- forEach 메소드는 for 문과는 달리 break 문을 사용할 수 없다. ****다시 말해, 배열의 모든 요소를 순회하며 중간에 순회를 중단할 수 없음.
- forEach 메소드는 for 문에 비해 성능이 좋지는 않다. 하지만 for 문보다 가독성이 좋으므로 적극 사용을 권장함.
- IE 9 이상에서 정상 동작함.

------

- forEach 메소드에 두번쨰 인자로 this를 전달할 수 있음.

------

ES6의 Arrow function를 사용하면 this를 생략하여도 동일한 동작을 함.

# ***\*3. Array.prototype.map<U>(callbackfn: (value: T, index: number, array: T[]) => U, thisArg?: any): U[] 🔒\****

- 배열을 순회하며 각 요소에 대하여 인자로 주어진 콜백 함수의 반환값(결과값)으로 새로운 배열을 생성하여 반환함. (원본 배열은 변경되지 않음.)
- forEach 메소드는 배열을 순회하며 요소 값을 참조하여 무언가를 하기 위한 함수이며 map 메소드는 배열을 순회하며 요소 값을 다른 값으로 맵핑하기 위한 함수임.

![Untitled](https://prod-files-secure.s3.us-west-2.amazonaws.com/510cd684-c9a0-45bd-b45d-b35ad6027628/6160950f-a770-4c8e-bdd6-ce54b099e163/Untitled.png)

- 콜백 함수의 매개변수를 통해 배열 요소의 값, 요소 인덱스, map 메소드를 호출한 배열, 즉 this를 전달 받을 수 있음.
- IE 9 이상에서 정상 동작함.

# 4. ***\*Array.prototype.filter(callback: (value: T, index: number, array: Array) => any, thisArg?: any): T[] 🔒\****

- filter 메소드를 사용하면 if 문을 대체할 수 있음.
- 배열을 순회하며 각 요소에 대하여 인자로 주어진 콜백함수의 실행 결과가 true인 배열 요소의 값만을 추출한 새로운 배열을 반환함.
- 배열에서 특정 케이스만 필터링 조건으로 추출하여 새로운 배열을 만들고 싶을 때 사용한다. 이때 원본 배열은 변경되지 않음.
- 콜백 함수의 매개변수를 통해 배열 요소의 값, 요소 인덱스, filter 메소드를 호출한 배열, 즉 this를 전달 받을 수 있음.
- IE 9 이상에서 정상 동작함.

# ***\*5. Array.prototype.reduce<U>(callback: (state: U, element: T, index: number, array: T[]) => U, firstState?: U): U 🔒\****

- 배열을 순회하며 각 요소에 대하여 이전의 콜백함수 실행 반환값을 전달하여 콜백함수를 실행하고 그 결과를 반환함.

```jsx
const arr = [1, 2, 3, 4, 5];

/*
previousValue: 이전 콜백의 반환값
currentValue : 배열 요소의 값
currentIndex : 인덱스
array        : 메소드를 호출한 배열, 즉 this
*/
// 합산
const sum = arr.reduce(function (previousValue, currentValue, currentIndex, self) {
  console.log(previousValue + '+' + currentValue + '=' + (previousValue + currentValue));
  return previousValue + currentValue; // 결과는 다음 콜백의 첫번째 인자로 전달된다
});

console.log(sum); // 15: 1~5까지의 합
/*
1: 1+2=3
2: 3+3=6
3: 6+4=10
4: 10+5=15
15
*/

// 최대값 취득
const max = arr.reduce(function (pre, cur) {
  return pre > cur ? pre : cur;
});

console.log(max); // 5: 최대값
```

![Untitled](https://prod-files-secure.s3.us-west-2.amazonaws.com/510cd684-c9a0-45bd-b45d-b35ad6027628/abeac716-797c-4e9f-9221-067b27c63a3f/Untitled.png)

- Array.prototype.reduce의 두번째 인수로 초기값을 전달할 수 있음.(이 값이 콜백 함수에 최초로 전달됨.)
- 초기값을 전달하면 에러를 회피할 수 있으므로 reduce를 호출할 때는 언제나 초기값을 전달하는 것이 안전함.

# ***\*6. Array.prototype.some(callback: (value: T, index: number, array: Array) => boolean, thisArg?: any): boolean 🔒\****

- 배열 내 일부 요소가 콜백 함수의 테스트를 통과하는지 확인하여 그 결과를 boolean으로 반환함.
- 콜백함수의 매개변수를 통해 배열 요소의 값, 요소 인덱스, 메소드를 호출한 배열을 전달 받을 수 있음.

```jsx
// 배열 내 요소 중 10보다 큰 값이 1개 이상 존재하는지 확인
let res = [2, 5, 8, 1, 4].some(function (item) {
  return item > 10;
});
console.log(res); // false

res = [12, 5, 8, 1, 4].some(function (item) {
  return item > 10;
});
console.log(res); // true

// 배열 내 요소 중 특정 값이 1개 이상 존재하는지 확인
res = ['apple', 'banana', 'mango'].some(function (item) {
  return item === 'banana';
});
console.log(res); // true
```

- some()도 map(), forEach()와 같이 두번째 인자로 this를 전달할 수 있음.

------

# ***\*7. Array.prototype.every(callback: (value: T, index: number, array: Array) => boolean, thisArg?: any): boolean 🔒\****

- 배열 내 일부 요소가 콜백 함수의 테스트를 통과하는지 확인하여 그 결과를 boolean으로 반환함.
- 콜백함수의 매개변수를 통해 배열 요소의 값, 요소 인덱스, 메소드를 호출한 배열을 전달 받을 수 있음.

```jsx
// 배열 내 모든 요소가 10보다 큰 값인지 확인
let res = [21, 15, 89, 1, 44].every(function (item) {
  return item > 10;
});
console.log(res); // false

res = [21, 15, 89, 100, 44].every(function (item) {
  return item > 10;
});
console.log(res); // true
```

- ever()도 map(), forEach(0와 같이 두번째 인자로 this를 전달할 수 있음.

# ***\*8. Array.prototype.find(predicate: (value: T, index: number, obj: T[]) => boolean, thisArg?: any): T | undefined 🔒\****

- 배열을 순회하며 각 요소에 대하여 인자로 주어진 콜백함수를 실행하여 그 결과가 참인 첫번째 요소를 반환함.
- filter는 콜백 함수의 실행 결과가 true인 배열 요소의 값만을 추출한 새로운 배열을 반환함.
- find는 콜백함수를 실행하여 그 결과가 참인 첫번째 요소를 반환하므로 find의 결과값은 해당 요소값임.

# ***\*9. Array.prototype.findIndex(predicate: (value: T, index: number, obj: T[]) => boolean, thisArg?: any): number 🔒\****

- 배열을 순회하며 각 요소에 대하여 인자로 주어진 콜백함수를 실행하여 그 결과가 참인 첫번째 요소의 인덱스를 반환함.(콜백함수의 실행 결과가 참인 요소가 존재하지 않는다면 -1을 반환함.)