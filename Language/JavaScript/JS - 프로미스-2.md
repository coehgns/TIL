# JS - 프로미스-2

# 1. 프로미스의 후속 처리 메소드

- Promise로 구현된 비동기 함수는 Promise 객체를 반환해야 함.
- Promise로 구현된 비동기 함수를 호출하는 측(promise consumer)에서는 Promise 객체의 후속 처리 메소드(then, catch)를 통해 비동기 처리 결과 또는 에러 메시지를 전달 받아 처리함.

### Promise의 후속 처리 메소드

- then
  - then 메소드는 두 개의 콜백 함수를 인자로 전달 받음.
  - 첫 번째 콜백 함수는 성공(fulfilled, resolve 함수가 호출된 상태) 시 호출되고 두 번째 함수는 실패(rejected, reject 함수가 호출된 상태) 시 호출됨.
  - then 메소드는 Promise를 반환함.
- catch
  - 예외(비동기 처리에서 발생한 에러와 then 메소드에서 발생한 에러)가 발생하면 호출됨.
  - catch 메소드는 Promise를 반환함.

# 2. 프로미스의 에러 처리

- 비동기 함수 get은 Promise 객체를 반환함.
- 비동기 처리 결과에 대한 후속 처리는 Promise 객체가 제공하는 후속 처리 메서드를 사용하여 수행함.
- 비동기 처리 시에 발생한 에러는 then 메서드의 두 번째 콜백 함수와 메서드 catch를 사용해서 처리 가능.
- catch 메서드를 호출하면 내부적으로 then을 호출함.
- catch 메서드를 모든 then 메서드를 호출한 이후에 호출하면 비동기 처리에서 발생한 에러뿐만 아니라 then 메서드 내부에서 발생한 에러까지 모두 캐치할 수 있음.

# 3. 프로미스 체이닝

- 프로미스는 후속 처리 메소드를 체이닝하여 여러 개의 프로미스를 연결하여 사용할 수 있음. (콜백 헬 해결)
- then 메소드가 Promise 객체를 반환하도록 하면 여러 개의 프로미스를 연결하여 사용할 수 있음.

# 4. 프로미스의 정적 메소드

- Promise는 주로 생성자 함수로 사용되지만 함수도 객체이므로 메소드를 갖을 수 있음. (Promise 객체는 4가지 정적 메소드를 제공함.)

## 4.1 Promise.resolve/Promise.reject

- Promise.resolve와 Promise.reject 메소드는 존재하는 값을 Promise로 래핑하기 위해 사용함.
- Promise.resolve 메소드는 인자로 전달된 값을 resolve하는 Promise를 생성함.
- Promise.reject 메소드는 인자로 전달된 값을 reject하는 프로미스를 생성함.

## 4.2 Promise.all

- Promise.all 메소드는 프로미스가 담겨 있는 배열 등의 이터러블을 인자로 받음.
- 전달 받은 모든 프로미스를 병렬로 처리하고 그 처리 결과를 resolve하는 새로운 프로미스를 반환함.
- 모든 프로미스의 처리가 종료될 때까지 기다린 후 모든 처리 결과를 resolve 또는 reject함.
- 모든 프로미스의 처리가 성공하면 각각의 프로미스가 resolve한 처리 결과를 배열에 담아 resolve하는 새로운 프로미스를 반환함. (첫번째 프로미스가 가장 나중에 처리되어도 Promise.all 메소드가 반환하는 프로미스는 첫번째 프로미스가 resolve한 처리 결과부터 차례대로 배열에 담아 그 배열을 resolve하는 새로운 프로미스를 반환함.)

## 4.3 Promise.race

- Promise.race 메소드는 Promise.all 메소드와 동일하게 프로미스가 담겨 있는 배열 등의 이터러블을 인자로 전달 받음.
- 가장 먼저 처리된 프로미스가 resolve한 처리 결과를 resolve하는 새로운 프로미스를 반환함.
- 에러가 발생하는 경우는 Promise.all 메소드와 동일하게 처리됨.

## 참고 자료

- https://poiemaweb.com/es6-promise