# JS Asynchronous processing model

- 동기식 처리 모델은 직렬적으로 태스크(task)를 수행함.
- 태스크는 순차적으로 실행되며 어떤 작업이 수행 중이면 다음 작업은 대기하게 됨.
- ex) 서버에서 데이터를 가져와서 화면에 표시하는 작업을 수행할 때, 서버에 데이터를 요청하고 데이터가 응답될 때 까지 이후 태스크들은 블로킹(작업 중단)됨.

![Untitled](https://prod-files-secure.s3.us-west-2.amazonaws.com/510cd684-c9a0-45bd-b45d-b35ad6027628/03f286f2-c8e5-4752-b8d1-07bc940565f7/Untitled.png)

```jsx
//동기식으로 동작하는 코드

function func1() {
  console.log('func1');
  func2();
}

function func2() {
  console.log('func2');
  func3();
}

function func3() {
  console.log('func3');
}

func1();
```

------

- 비동기식 처리 모델은 병렬적으로 태스크를 수행함.
- 태스크가 종료되지 않은 상태라 하더라도 대기하지 않고 다음 태스크를 실행함.
- ex) 서버에서 데이터를 가져와서 화면에 표시하는 태스크를 수행할 때, 서버에 데이터를 요청한 이후 서버로부터 데이터가 응답될 때까지 대기하지 않고 즉시 다음 태스크를 수행함.
- 이후 서버로부터 데이터가 응답되면 이벤트가 발생하고 핸들러가 데이터를 가지고 수행할 때 태스크를 계속해 수행함.

------

- 자바스크립트의 대부분의 DOM 이벤트 핸들러와 Timer 함수, Ajax 요청은 비동기식 처리 모델로 동작함.

![Untitled](https://prod-files-secure.s3.us-west-2.amazonaws.com/510cd684-c9a0-45bd-b45d-b35ad6027628/c2a7bd31-6278-4fad-9c55-8f33160997ad/Untitled.png)

```jsx
// 비동기식으로 동작하는 코드

function func1() {
  console.log('func1');
  func2();
}

function func2() {
  setTimeout(function() {
    console.log('func2');
  }, 0);

  func3();
}

function func3() {
  console.log('func3');
}

func1();
```

- setTimeout 메소드는 비동기 함수임.

![Untitled](https://prod-files-secure.s3.us-west-2.amazonaws.com/510cd684-c9a0-45bd-b45d-b35ad6027628/a67fd7ab-3da5-4a78-9898-189fe763afbd/Untitled.png)

- setTimout의 콜백함수는 즉시 실행되지 않고 지정 대기 시간 만큼 기다리다가 “tick” 이벤트가 발생하면 태스크 큐로 이동한 후 Call Stack이 비어졌을 때 Call Stack으로 이동되어 실행함.

![Untitled](https://prod-files-secure.s3.us-west-2.amazonaws.com/510cd684-c9a0-45bd-b45d-b35ad6027628/fa2bf6c8-c7e8-42b1-ba96-5bb8b1cb00ce/Untitled.png)