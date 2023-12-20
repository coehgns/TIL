# JS Closure

# 1. 클로저의 개념

- 클로저는 함수를 일급 객체로 취급하는 함수형 프로그래밍 언어에서 사용되는 중요한 특성임.
- 클로저는 함수와 그 함수가 선언됐을 때의 렉시컬 환경과의 조합임.

```jsx
function outerFunc() {
  var x = 10;
  var innerFunc = function () { console.log(x); };
  innerFunc();
}

outerFunc(); // 10
```

- 내부함수 innerFunc는 자신을 포함하고 있는 외부함수 outerFunc의 변수 x에 접근할 수 있음.(함수는 innerFunc가 함수 outerFunc의 내부에 선언되었기 때문임.)
- 외부 함수 밖에서 내부함수가 호출되더라도 외부함수의 지역 변수에 접근할 수 있는데 이러한 함수를 클로저라고 부름.
- 클로저는 반환된 내부함수가 자신이 선언됐을 때의 환경인 스코프를 기억하여 자신이 선언됐을 때의 환경(스코프) 밖에서 호출되어도 그 환경(스코프)에 접근할 수 있는 함수를 말함.
- 클로저에 의해 참조되는 외부함수의 변수 x를 자유변수라고 부름.

# 2. 클로저의 활용

- 클로저는 자바스크립트의 강력한 기능으로 적극적으로 사용해야 함.

## 2.1 상태 유지

- 클로저가 가장 유용하게 사용되는 상황은 현재 상태를 기억하고 변경된 최신 상태를 유지하는 것임.

## 2.2 전역 변수의 사용 억제

- 버튼이 클릭될 때마다 클릭한 횟수가 누적되어 화면에 표시되는 카운터.

```jsx
<!DOCTYPE html>
<html>
  <body>
  <p>클로저를 사용한 Counting</p>
  <button id="inclease">+</button>
  <p id="count">0</p>
  <script>
    var incleaseBtn = document.getElementById('inclease');
    var count = document.getElementById('count');

    var increase = (function () {
      // 카운트 상태를 유지하기 위한 자유 변수
      var counter = 0;
      // 클로저를 반환
      return function () {
        return ++counter;
      };
    }());

    incleaseBtn.onclick = function () {
      count.innerHTML = increase();
    };
  </script>
</body>
</html>
```

- 즉시실행함수는 호출된 이후 소멸되지만 즉시실행함수가 반환한 함수는 변수 increase에 할당되어 inclease 버튼을 클릭하면 클릭 이벤트 핸들러 내부에서 호출됨.
- 이때 클로저인 이 함수는 자신이 선언됐을 때의 렉시컬 환경인 즉시실행함수의 스코프에 속한 지역변수 counter를 기억함.(즉시실행함수의 변수 counter에 접근할 수 있고 변수 counter는 자신을 참조하는 함수가 소멸될 때까지 유지됨.)

## 2.3 정보의 은닉

- 생성자 함수 Counter를 생성하고 이를 통해 counter 객체를 만들기.

```jsx
function Counter() {
  // 카운트를 유지하기 위한 자유 변수
  var counter = 0;

  // 클로저
  this.increase = function () {
    return ++counter;
  };

  // 클로저
  this.decrease = function () {
    return --counter;
  };
}

const counter = new Counter();

console.log(counter.increase()); // 1
console.log(counter.decrease()); // 0
```