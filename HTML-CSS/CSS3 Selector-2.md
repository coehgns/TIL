# CSS3 Selector-2

## 6. 복합 셀렉터 (Combinator)

### 6.1 후손 셀렉터 (Descendant Combinator)

![후속 셀렉터.png](https://prod-files-secure.s3.us-west-2.amazonaws.com/510cd684-c9a0-45bd-b45d-b35ad6027628/d36d7002-f775-4f0c-934c-a5cc4f1819eb/%ED%9B%84%EC%86%8D_%EC%85%80%EB%A0%89%ED%84%B0.png)

- 자신의 1 level 상위에 속하는 요소를 부모 요소, 1 level 하위에 속하는 요소를 자손 요소(자식 요소)라고 함.
- 자신보다 n level 하위에 속하는 요소는 후손 요소(하위 요소)라고 함.
- 후손 셀렉터는 셀렉터 A의 모든 후손(하위) 요소 중 셀렉터 B와 일치하는 요소를 선택함.

```html
셀렉터 A 셀렉터 B
<!DOCTYPE html>
<html>
<head>
  <style>
    /* div 요소의 후손요소 중 p 요소 */
    div p { color: red; }
  </style>
</head>
<body>
  <h1>Heading</h1>
  <div>
    <p>paragraph 1</p>
    <p>paragraph 2</p>
    <span><p>paragraph 3</p></span>
  </div>
  <p>paragraph 4</p>
</body>
</html>
```

- result

  ![후손 셀렉터.png](https://prod-files-secure.s3.us-west-2.amazonaws.com/510cd684-c9a0-45bd-b45d-b35ad6027628/1ed26202-0a3e-455e-a332-a1f4da5e1c6a/%ED%9B%84%EC%86%90_%EC%85%80%EB%A0%89%ED%84%B0.png)

### 6.2 자식 셀렉터 (Child Combinator)

- 자손 셀렉터는 셀렉터 A의 모든 자식 요소 중 셀렉터B와 **일치하는** 요소를 선택함.

```html
셀렉터A > 셀렉터B
<!DOCTYPE html>
<html>
<head>
  <style>
    /* div 요소의 자식요소 중 p 요소 */
    div > p { color: red; }
  </style>
</head>
<body>
  <h1>Heading</h1>
  <div>
    <p>paragraph 1</p>
    <p>paragraph 2</p>
    <span><p>paragraph 3</p></span>
  </div>
  <p>paragraph 4</p>
</body>
</html>
```

- result

  ![자식 셀렉터.png](https://prod-files-secure.s3.us-west-2.amazonaws.com/510cd684-c9a0-45bd-b45d-b35ad6027628/2b7beffd-ab5f-4869-a5db-6b1d39a6beb4/%EC%9E%90%EC%8B%9D_%EC%85%80%EB%A0%89%ED%84%B0.png)

### 6.3 형제(동위) 셀렉터 (Sibling Combinator)

- 형제 셀렉터는 형제 관계에서 뒤에 위치하는 요소를 선택할 때 사용함.

  ![형제 셀렉터.png](https://prod-files-secure.s3.us-west-2.amazonaws.com/510cd684-c9a0-45bd-b45d-b35ad6027628/bf436e29-70cc-4518-9464-43a952fce476/%ED%98%95%EC%A0%9C_%EC%85%80%EB%A0%89%ED%84%B0.png)

### 6.3.1 인접 형제 셀렉터(Adjacent Sibling Combinator)

- 셀렉터A의 형제 요소 중 셀렉터 A 바로 뒤에 위치하는 셀렉터B 요소를 선택함.
- A와 B 사이에 **다른 요소가 존재하면** 선택되지 않음.

```html
셀렉터A + 셀렉터B
<!DOCTYPE html>
<html>
<head>
  <style>
    /* p 요소의 형제 요소 중에 p 요소 바로 뒤에 위치하는 ul 요소를 선택한다. */
    p + ul { color: red; }
  </style>
</head>
<body>
  <div>A div element.</div>
  <ul>
    <li>Coffee</li>
    <li>Tea</li>
    <li>Milk</li>
  </ul>

  <p>The first paragraph.</p>
  <ul>
    <li>Coffee</li>
    <li>Tea</li>
    <li>Milk</li>
  </ul>

  <h2>Another list</h2>
  <ul>
    <li>Coffee</li>
    <li>Tea</li>
    <li>Milk</li>
  </ul>
</body>
</html>
```

- result

  ![인접 형제 셀렉터.png](https://prod-files-secure.s3.us-west-2.amazonaws.com/510cd684-c9a0-45bd-b45d-b35ad6027628/208bb2aa-77a4-4105-9d10-d0c3a70d0b78/%EC%9D%B8%EC%A0%91_%ED%98%95%EC%A0%9C_%EC%85%80%EB%A0%89%ED%84%B0.png)

### 6.3.2 일반 형제 셀렉터(General Sibling Combinator)

- 셀렉터A의 형제 요소 중 셀렉터A 뒤에 위치하는 셀렉터B 요소를 모두 선택함.

```html
셀렉터A ~ 셀렉터 B
<!DOCTYPE html>
<html>
<head>
  <style>
    /* p 요소의 형제 요소 중에 p 요소 뒤에 위치하는 ul 요소를 모두 선택한다.*/
    p ~ ul { color: red; }
  </style>
</head>
<body>
  <div>A div element.</div>
  <ul>
    <li>Coffee</li>
    <li>Tea</li>
    <li>Milk</li>
  </ul>

  <p>The first paragraph.</p>
  <ul>
    <li>Coffee</li>
    <li>Tea</li>
    <li>Milk</li>
  </ul>

  <h2>Another list</h2>
  <ul>
    <li>Coffee</li>
    <li>Tea</li>
    <li>Milk</li>
  </ul>
</body>
</html>
```

- result

  ![일반 형제 셀렉터.png](https://prod-files-secure.s3.us-west-2.amazonaws.com/510cd684-c9a0-45bd-b45d-b35ad6027628/39096d32-c365-4df3-9d0f-ef59a3cdef89/%EC%9D%BC%EB%B0%98_%ED%98%95%EC%A0%9C_%EC%85%80%EB%A0%89%ED%84%B0.png)

## 7.가상 클래스 셀렉터 (Pseudo-Class Selector)

- 가상 클래스는 요소의 특정 상태에 따라 스타일을 정의할 때 사용됨.
  - 특정 상태의 예
    - 마우스가 올라와 있을 때
    - 링크를 방문했을 때와 아직 방문하지 않았을 때
    - 포커스가 들어와 있을 때
- 특정 상태에는 원래 클래스가 존재하지 않지만 가상 클래스를 임의로 지정하여 선택하는 방법.
- 가상 클래스는 마침표 대신 세미콜론을 사용함. CSS 표준에 의해 미리 정의된 이름이 있기 때문에 임의의 이름을 사용할 수 없음.

```css
selector:pseudo-class {
  property: value;
}
div 요소가 hover 상태일 때(마우스가 올라와 있을 때) background-color를 red로 지정하는 예.
<!DOCTYPE html>
<html>
<head>
  <style>
    /* a 요소가 hover 상태일 때 */
    a:hover { background-color: red; }
    /* input 요소가 focus 상태일 때 */
    input:focus { background-color: yellow; }
  </style>
</head>
<body>
  <a href="#">Hover me</a><br><br>
  <input type="text" placeholder="focus me">
</body>
</html>
```

- result

  ![가상 클래스.png](https://prod-files-secure.s3.us-west-2.amazonaws.com/510cd684-c9a0-45bd-b45d-b35ad6027628/8f12b479-123d-410f-9781-9e86edf0414b/%EA%B0%80%EC%83%81_%ED%81%B4%EB%9E%98%EC%8A%A4.png)

## 7.1 링크 셀렉터 (Link pseudo-classes), 동적 셀렉터(User action pseudo-classes)

| pseudo-class | Description                      |
| ------------ | -------------------------------- |
| :link        | 셀렉터가 방문하지 않은 링크일 때 |
| :visited     | 셀렉터가 방문한 링크일 때        |
| :hover       | 셀렉터에 마우스가 올라와 있을 때 |
| :active      | 셀렉터가 클릭된 상태일 때        |
| :focus       | 셀렉터에 포커스가 들어와 있을 때 |

```html
<!DOCTYPE html>
<html>
<head>
  <style>
    /* a 요소가 방문하지 않은 링크일 때 */
    a:link { color: orange; }

    /* a 요소가 방문한 링크일 때 */
    a:visited { color: green; }

    /* a 요소에 마우스가 올라와 있을 때 */
    a:hover { font-weight: bold; }

    /* a 요소가 클릭된 상태일 때 */
    a:active { color: blue; }

    /* text input 요소와 password input 요소에 포커스가 들어와 있을 때 */
    input[type=text]:focus,
    input[type=password]:focus {
      color: red;
    }
    </style>
  </head>
<body>
  <a href="#" target="_blank">This is a link</a><br>
  <input type="text" value="I'll be red when focused"><br>
  <input type="password" value="I'll be red when focused">
</body>
</html>
```

- result

  ![link selector.png](https://prod-files-secure.s3.us-west-2.amazonaws.com/510cd684-c9a0-45bd-b45d-b35ad6027628/0050871b-680a-4394-b50d-0b16fba1d1b2/link_selector.png)

## 7.2 UI 요소 상태 셀렉터(UI element states pseudo-classes)

| pseudo-class | Description                      |
| ------------ | -------------------------------- |
| :checked     | 셀렉터가 체크 상태일 때          |
| :enabled     | 셀렉터가 사용 가능한 상태일 때   |
| :disabled    | 셀렉터가 사용 불가능한 상태일 때 |

```html
<!DOCTYPE html>
<html>
<head>
  <style>
    /* input 요소가 사용 가능한 상태일 때,
       input 요소 바로 뒤에 위치하는 인접 형제 span 요소를 선택 */
    input:enabled + span {
      color: blue;
    }
    /* input 요소가 사용 불가능한 상태일 때,
       input 요소 바로 뒤에 위치하는 인접 형제 span 요소를 선택 */
    input:disabled + span {
      color: gray;
      text-decoration: line-through;
    }
    /* input 요소가 체크 상태일 때,
       input 요소 바로 뒤에 위치하는 인접 형제 span 요소를 선택 */
    input:checked + span {
      color: red;
    }
  </style>
</head>
<body>
  <input type="radio" checked="checked" value="male" name="gender"> <span>Male</span><br>
  <input type="radio" value="female" name="gender"> <span>Female</span><br>
  <input type="radio" value="neuter" name="gender" disabled> <span>Neuter</span><hr>

  <input type="checkbox" checked="checked" value="bicycle"> <span>I have a bicycle</span><br>
  <input type="checkbox" value="car"> <span>I have a car</span><br>
  <input type="checkbox" value="motorcycle" disabled> <span>I have a motorcycle</span>
</body>
</html>
```

- result

  ![UI 요소 셀렉터.png](https://prod-files-secure.s3.us-west-2.amazonaws.com/510cd684-c9a0-45bd-b45d-b35ad6027628/9e1bd1e9-2b2e-4963-98b4-427e01b30fcd/UI_%EC%9A%94%EC%86%8C_%EC%85%80%EB%A0%89%ED%84%B0.png)

## 7.3 구조 가상 클래스 셀렉터(Structural pseudo-classes)

| pseudo-class | Description                                                  |
| ------------ | ------------------------------------------------------------ |
| :first-child | 셀렉터에 해당하는 모든 요소 중 첫번째 자식인 요소를 선택한다. |
| :last-child  | 셀렉터에 해당하는 모든 요소 중 마지막 자식인 요소를 선택한다. |

```html
<!DOCTYPE html>
<html>
<head>
  <style>
    /* p 요소 중에서 첫번째 자식을 선택 */
    p:first-child { color: red; }

    /* p 요소 중에서 마지막 자식을 선택 */
    /* body 요소의 두번째 p 요소는 마지막 자식 요소가 아니다.
       body 요소의 마지막 자식 요소는 div 요소이다. */
    p:last-child { color: blue; }
  </style>
</head>
<body>
  <p>This paragraph is the first child of its parent (body).</p>

  <h1>Welcome to My Homepage</h1>
  <p>This paragraph is not the first child of its parent.</p>

  <div>
    <p>This paragraph is the first child of its parent (div).</p>
    <p>This paragraph is not the first child of its parent.</p>
  </div>
</body>
</html>
```

- result

  ![구조 가상 클래스 셀렉터.png](https://prod-files-secure.s3.us-west-2.amazonaws.com/510cd684-c9a0-45bd-b45d-b35ad6027628/7c28baa1-717f-4ac6-8034-142899a64ba8/%EA%B5%AC%EC%A1%B0_%EA%B0%80%EC%83%81_%ED%81%B4%EB%9E%98%EC%8A%A4_%EC%85%80%EB%A0%89%ED%84%B0.png)

  | pseudo-class       | Description                                                  |
  | ------------------ | ------------------------------------------------------------ |
  | :nth-child(n)      | 셀렉터에 해당하는 모든 요소 중 앞에서 n번째 자식인 요소를 선택한다. |
  | :nth-last-child(n) | 셀렉터에 해당하는 모든 요소 중 뒤에서 n번째 자식인 요소를 선택한다. |

- n은 0부터 시작하는 정수.

| n    | 2n+1 | 2n-1 | 3n-2 | 3n+1 | -n+5 |
| ---- | ---- | ---- | ---- | ---- | ---- |
| 0    | 1    | -1   | -2   | 1    | 5    |
| 1    | 3    | 1    | 1    | 4    | 4    |
| 2    | 5    | 3    | 4    | 7    | 3    |
| 3    | 7    | 5    | 7    | 10   | 2    |
| 4    | 9    | 7    | 10   | 13   | 1    |
| 5    | 11   | 9    | 13   | 16   | 0    |

- 0과 음수는 생략되기 때문에 2n+1과 2n-1, 3n-2와 3n+1은 결과적으로 같은 수열을 생성.

```html
<!DOCTYPE html>
<html>
<head>
  <style>
    /* ol 요소의 자식 요소인 li 요소 중에서 짝수번째 요소만을 선택 */
    ol > li:nth-child(2n)   { color: orange; }
    /* ol 요소의 자식 요소인 li 요소 중에서 홀수번째 요소만을 선택 */
    ol > li:nth-child(2n+1) { color: green; }

    /* ol 요소의 자식 요소인 li 요소 중에서 첫번쨰 요소만을 선택 */
    ol > li:first-child     { color: red; }
    /* ol 요소의 자식 요소인 li 요소 중에서 마지막 요소만을 선택 */
    ol > li:last-child      { color: blue; }

    /* ol 요소의 자식 요소인 li 요소 중에서 4번째 요소 요소만을 선택 */
    ol > li:nth-child(4)    { background: brown; }

    /* ul 요소의 모든 자식 요소 중에서 뒤에서부터 시작하여 홀수번째 요소만을 선택 */
    ul > :nth-last-child(2n+1) { color: red; }
    /* ul 요소의 모든 자식 요소 중에서 뒤에서부터 시작하여 짝수번째 요소만을 선택 */
    ul > :nth-last-child(2n)   { color: blue; }
  </style>
</head>
<body>
  <ol>
    <li>Espresso</li>
    <li>Americano</li>
    <li>Caffe Latte</li>
    <li>Caffe Mocha</li>
    <li>Caramel Latte</li>
    <li>Cappuccino</li>
  </ol>

  <ul>
    <li>Espresso</li>
    <li>Americano</li>
    <li>Caffe Latte</li>
    <li>Caffe Mocha</li>
    <li>Caramel Latte</li>
    <li>Cappuccino</li>
  </ul>
</body>
</html>
```

- result

  ![가상 클래스 셀렉터 -2.png](https://prod-files-secure.s3.us-west-2.amazonaws.com/510cd684-c9a0-45bd-b45d-b35ad6027628/1f830dc2-d593-4d23-a12d-3cd5e8527077/%EA%B0%80%EC%83%81_%ED%81%B4%EB%9E%98%EC%8A%A4_%EC%85%80%EB%A0%89%ED%84%B0_-2.png)

| pseudo-class         | Description                                                  |
| -------------------- | ------------------------------------------------------------ |
| :first-of-type       | 셀렉터에 해당하는 요소의 부모 요소의 자식 요소 중 첫번째 등장하는 요소를 선택한다. |
| :last-of-type        | 셀렉터에 해당하는 요소의 부모 요소의 자식 요소 중 마지막에 등장하는 요소를 선택한다. |
| :nth-of-type(n)      | 셀렉터에 해당하는 요소의 부모 요소의 자식 요소 중 앞에서 n번째에 등장하는 요소를 선택한다. |
| :nth-last-of-type(n) | 셀렉터에 해당하는 요소의 부모 요소의 자식 요소 중 뒤에서 n번째에 등장하는 요소를 선택한다. |

```html
<!DOCTYPE html>
<html>
<head>
  <style>
    /* p 요소의 부모 요소의 자식 요소 중 첫번째 등장하는 p 요소 */
    p:first-of-type  { color: red; }
    /* p 요소의 부모 요소의 자식 요소 중 마지막 등장하는 p 요소 */
    p:last-of-type   { color: blue; }
    /* p 요소의 부모 요소의 자식 요소 중 앞에서 2번째에 등장하는 p 요소 */
    p:nth-of-type(2) { color: green; }
    /* p 요소의 부모 요소의 자식 요소 중 뒤에서 2번째에 등장하는 p 요소 */
    p:nth-last-of-type(2) { color: orange;}

    /* p 요소 중에서 첫번째 자식을 선택 */
    p:first-child { background: brown;}
  </style>
</head>
<body>
  <h1>This is a heading</h1>
  <p>The first paragraph.</p>
  <p>The second paragraph.</p>
  <p>The third paragraph.</p>
  <p>The fourth paragraph.</p>
  <div>
    <h1>This is a heading</h1>
    <p>The first paragraph.</p>
    <p>The second paragraph.</p>
    <p>The third paragraph.</p>
    <p>The fourth paragraph.</p>
  </div>
</body>
</html>
```

- result

  ![구조 가상 클래스 셀렉터 -2.png](https://prod-files-secure.s3.us-west-2.amazonaws.com/510cd684-c9a0-45bd-b45d-b35ad6027628/69e6d166-5e56-4057-9b0c-f55f4a1f7b9e/%EA%B5%AC%EC%A1%B0_%EA%B0%80%EC%83%81_%ED%81%B4%EB%9E%98%EC%8A%A4_%EC%85%80%EB%A0%89%ED%84%B0_-2.png)

### 7.4 부정 셀렉터(Negation pseudo-class)

| pseudo-class | Description                                  |
| ------------ | -------------------------------------------- |
| :not(셀렉터) | 셀렉터에 해당하지 않는 모든 요소를 선택한다. |

```html
<!DOCTYPE html>
<html>
<head>
  <style>
    /* input 요소 중에서 type 어트리뷰트의 값이 password가 아닌 요소를 선택 */
    input:not([type=password]) {
      background: yellow;
    }
  </style>
</head>
<body>
  <input type="text" value="Text input">
  <input type="email" value="email input">
  <input type="password" value="Password input">
</body>
</html>
```

- result

  ![부정 셀렉터.png](https://prod-files-secure.s3.us-west-2.amazonaws.com/510cd684-c9a0-45bd-b45d-b35ad6027628/5eef622d-3ac5-40d1-9d5c-aa2811f8323f/%EB%B6%80%EC%A0%95_%EC%85%80%EB%A0%89%ED%84%B0.png)

```html
<!DOCTYPE html>
<html>
<head>
  <style>
    body {
      margin: 0;
    }
    div {
      float: left;
      width: 32%;
      height: 200px;
      background-color: red;
      /* margin-bottom: 2%; */
      color: #fff;
      font-size: 3em;
      line-height: 200px;
      text-align: center;
    }
    /* div 요소 중에서 1, 4, 7...번째 등장하는 요소가 아닌 요소만을 선택 */
    /* 1, 4, 7... : 공차가 3인 등차수열 */
    div:not(:nth-of-type(3n+1)) {
      margin-left: 2%;
    }
    /* div 요소 중에서 4번째 이후 등장하는 요소가 아닌 요소만을 선택 */
    div:not(:nth-of-type(n+4)) {
      margin-bottom: 2%;
    }
  </style>
</head>
<body>
  <div>1</div>
  <div>2</div>
  <div>3</div>
  <div>4</div>
  <div>5</div>
  <div>6</div>
</body>
</html>
```

- result

  ![부정 셀렉터-2.png](https://prod-files-secure.s3.us-west-2.amazonaws.com/510cd684-c9a0-45bd-b45d-b35ad6027628/cc158c05-b1ff-4f1d-8121-56130ba22f2a/%EB%B6%80%EC%A0%95_%EC%85%80%EB%A0%89%ED%84%B0-2.png)

### 7.5 정합성 체크 셀렉터(validity pseudo-class)

| pseudo-class     | Description                                                |
| ---------------- | ---------------------------------------------------------- |
| :valid(셀렉터)   | 정합성 검증이 성공한 input 요소 또는 form 요소를 선택한다. |
| :invalid(셀렉터) | 정합성 검증이 실패한 input 요소 또는 form 요소를 선택한다. |

```html
<!DOCTYPE html>
<html>
<head>
  <style>
    input[type="text"]:valid {
      background-color: greenyellow;
    }

    input[type="text"]:invalid {
      background-color: red;
    }
  </style>
</head>
<body>
  <label>입력값이 반드시 필요
    <input type="text" required>
  </label>
  <br>
  <label>특수문자를 포함하지 않는 4자리 문자 또는 숫자
    <input type="text" value="ab1!"
      pattern="[a-zA-Z0-9]{4}" required>
  </label>
  <br>
  <label>핸드폰 번호 형식
    <input type="text" value="010-1111-2222"
      pattern="^\\d{3}-\\d{3,4}-\\d{4}$" required>
  </label>
</body>
</html>
```

- result

  ![정합성 체크 셀렉터.png](https://prod-files-secure.s3.us-west-2.amazonaws.com/510cd684-c9a0-45bd-b45d-b35ad6027628/c2218a4e-e4d7-4a4b-ad83-b663d94a5bd6/%EC%A0%95%ED%95%A9%EC%84%B1_%EC%B2%B4%ED%81%AC_%EC%85%80%EB%A0%89%ED%84%B0.png)

## 8. 가상 요소 셀렉터 (Pseudo-Element Selector)

- 가상 요소는 요소의 특정 부분에 스타일을 적용하기 위하여 사용됨.
  - 특정 부분
    - 요소 콘텐츠의 첫 글자 또는 첫 줄
      - 요소 콘텐츠의 앞 또는 뒤
- 가상 요소에는 두 개의 세미콜론(;;)을 사용함.

```css
selector::pseudo-element {
  property:value;
}
```

| pseudo-element | Description                                                  |
| -------------- | ------------------------------------------------------------ |
| ::first-letter | 콘텐츠의 첫글자를 선택한다.                                  |
| ::first-line   | 콘텐츠의 첫줄을 선택한다. 블록 요소에만 적용할 수 있다.      |
| ::after        | 콘텐츠의 뒤에 위치하는 공간을 선택한다. 일반적으로 content 프로퍼티와 함께 사용된다. |
| ::before       | 콘텐츠의 앞에 위치하는 공간을 선택한다. 일반적으로 content 프로퍼티와 함께 사용된다. |
| ::selection    | 드래그한 콘텐츠를 선택한다. iOS Safari 등 일부 브라우저에서 동작 않는다. |

```css
<!DOCTYPE html>
<html>
<head>
  <style>
    /* p 요소 콘텐츠의 첫글자를 선택 */
    p::first-letter { font-size: 3em; }
    /* p 요소 콘텐츠의 첫줄을 선택 */
    p::first-line   { color: red; }

    /* h1 요소 콘텐츠의 앞 공간에 content 어트리뷰트 값을 삽입한다 */
    h1::before {
      content: " HTML!!! ";
      color: blue;
    }
    /* h1 요소 콘텐츠의 뒷 공간에 content 어트리뷰트 값을 삽입한다 */
    h1::after {
      content: " CSS3!!!";
      color: red;
    }

    /* 드래그한 콘텐츠를 선택한다 */
    ::selection {
      color: red;
      background: yellow;
    }
  </style>
</head>
<body>
  <h1>This is a heading</h1>
  <p>Lorem ipsum dolor sit amet, consectetur adipisicing elit. Explicabo illum sunt distinctio sed, tempore, repellat rerum et ea laborum voluptatum! Quisquam error fugiat debitis maiores officiis, tenetur ullam amet in!</p>
</body>
</html>
```

- result

  ![가상 요소 셀렉터.png](https://prod-files-secure.s3.us-west-2.amazonaws.com/510cd684-c9a0-45bd-b45d-b35ad6027628/b0cbc684-f027-4a41-8ab1-57a4c0dd0966/%EA%B0%80%EC%83%81_%EC%9A%94%EC%86%8C_%EC%85%80%EB%A0%89%ED%84%B0.png)