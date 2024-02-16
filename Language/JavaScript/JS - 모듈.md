# JS - 모듈

# 모듈

- 모듈이란 애플리케이션을 구성하는 개별적 요소로서 재사용 가능한 코드 조각을 말함.
- 모듈은 세부 사항을 캡슐화하고 공개가 필요한 API만을 외부에 노출함.
- 모듈은 파일 단위로 분리되어 있으며 애플리케이션은 필요에 따라 명시적으로 모듈을 로드하여 재사용함.

# 1. 모듈 스코프

- ES6의 모듈 기능을 사용하지 않으면 분리된 자바스크립트 파일에 독자적인 스코프를 갖지 않고 하나의 전역을 공유함.
- ES6 모듈은 파일 자체의 스코프를 제공함. (독자적인 모듈 스코프를 갖음.)
- 모듈 내에서 var 키워드로 선언한 변수는 더 이상 전역 변수가 아니며 window 객체의 프로퍼티도 아님.

# 2. export 키워드

- 모듈은 독자적인 스코프를 갖기 때문에 모듈 안에 선언한 모든 식별자는 기본적으로 해당 모듈 내부에서만 참조할 수 있음.
- 모듈 안에 선언한 식별자를 외부에 공개하여 다른 모듈들이 참조할 수 있게 하고 싶다면 export 키워드를 사용함. (선언된 변수, 함수, 클래스 모두 export할 수 있음.)
- 모듈을 공개하기 위해서는 선언문 앞에 export 키워드를 사용함. (각각의 export는 이름으로 구별.)

```jsx
// lib.mjs
// 변수의 공개
export const pi = Math.PI;

// 함수의 공개
export function square(x) {
  return x * x;
}

// 클래스의 공개
export class Person {
  constructor(name) {
    this.name = name;
  }
}
```

- 선언문 앞에 매번 export 키워드를 붙이는 것이 싫다면 export 대상을 모아 하나의 객체로 구성하여 한번에 export할 수도 있음.

```jsx
// lib.mjs
const pi = Math.PI;

function square(x) {
  return x * x;
}

class Person {
  constructor(name) {
    this.name = name;
  }
}

// 변수, 함수 클래스를 하나의 객체로 구성하여 공개
	export { pi, square, Person };
```

# 3. import 키워드

- 모듈에서 export한 대상을 로드하려면 import 키워드를 사용함.
- 모듈이 export한 식별자로 import하면 ES6 모듈의 파일 확장자를 생략할 수 없음.
- 모듈이 export한 식별자를 각각 지정하지 않고 하나의 이름으로 한꺼번에 import할 수도 있음. (이때 import되는 식별자는 as 뒤에 지정한 이름의 객체에 프로퍼티로 할당됨.)
- 모듈에서 하나만을 export할 때는 default 키워드를 사용할 수 있음.(default를 사용하는 경우 var, let, const는 사용할 수 없음.)

## 참고 자료

- https://poiemaweb.com/es6-module