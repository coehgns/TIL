# JS DOM - 1

# 1. DOM (Document Object Model)

- 텍스트 파일로 만들어져 있는 웹 문서를 브라우저에 렌더링하려면 웹 문서를 브라우저가 이해할 수 있는 구조로 메모리에 올려야 함.
- 브라우저의 렌더링 엔진은 웹 문서를 로드한 후, 피싱하여 웹 문서를 브라우저가 이해할 수 있는 구조로 구성하여 메모리에 적재하는 것을 DOM이라고 함.
- 모든 요소와 요소의 어트리뷰트, 텍스트를 각각의 객체로 만들고 이들 객체를 부자 관계로 표현할 수 있는 트리 구조로 구성한 것이 DOM임.

![Untitled](https://prod-files-secure.s3.us-west-2.amazonaws.com/510cd684-c9a0-45bd-b45d-b35ad6027628/1a117fe9-91af-4b95-a234-68f7ccb045c1/Untitled.png)

- 웹 문서의 동적 변경을 위해 DOM은 프로그래밍 언어가 자신에 접근하고 수정할 수 있는 방법을 제공함. 일반적으로 프로퍼티와 메소드를 갖는 자바스크립트 객체로 제공되는데 이를 DOM API라고 부름.

------

- DOM 담당 기능
  - HTML 문서에 대한 모델 구성
    - 브라우저는 HTML 문서를 로드한 후 해당 문서에 대한 모델을 메모리에 생성함.(모델은 객체의 트리로 구성되는데 이것을 DOM tree라고 함.)
  - HTML 문서 내의 각 요소에 접근 / 수정
    - DOM은 모델 내의 각 객체에 접근하고 수정할 수 있는 프로퍼티와 메소드를 제공함.(DOM이 수정되면 브라우저를 통해 사용자가 보게 될 내용 또한 변경됨.)

------

# 2. DOM tree

- DOM tree는 브라우저가 HTML 문서를 로드한 후 파싱하여 생성하는 모델을 의미함.

![Untitled](https://prod-files-secure.s3.us-west-2.amazonaws.com/510cd684-c9a0-45bd-b45d-b35ad6027628/b0e84ac3-8fbd-48ce-b382-318dc5b6104c/Untitled.png)

- DOM에서 모든 요소, 어트리뷰트, 텍스트는 하나의 객체이며 Document 객체의 자식임.(요소의 중첩관계는 객체의 트리로 구조화하여 부자관계를 표현함.)
- DOM tree의 진입접은 document 객체이고 최종점은 요소의 텍스트를 나타내는 객체임.

------

- DOM tree 구성(네 종류의 노드)
  - 문서 노드(Document Node)
    - 트리의 최상위에 존재하며 각각 요소, 어트리뷰트, 텍스트 노드에 접근하려면 문서 노드를 통해야 함.(DOM tree에 접근하기 위한 시작점임.)
  - 요소 노드(Element Node)
    - 요소 노드는 HTML 요소를 표현함. HTML 요소는 중첩에 의해 부자 관계를 가지며 부자 관계를 통해 정보를 구조화함.
    - 어트리뷰트, 텍스트 노드에 접근하려면 먼저 요소 노드를 찾아 접근해야 함.
    - 모든 요소 노드는 요소별 특성을 표현하기 위해 HTMLElement 객체를 상속한 객체로 구성됨.
  - 어트리뷰트 노드(Attribute Node)
    - 어트리뷰트 노드는 HTML 요소의 어트리뷰트를 표현함.
    - 어트리뷰트 노드는 해당 요소의 일부로 표현됨.(해당 요소 노드를 찾아 접근하면 어트리뷰트를 참조, 수정할 수 있음.)
  - 텍스트 노드(Text Node)
    - 텍스트 노드는 HTML 요소의 텍스트를 표현함.
    - 텍스트 노드는 요소 노드의 자식이며 자신의 자식 노드를 가질 수 없음.(텍스트 노드는 DOM tree의 최종단임.)

![Untitled](https://prod-files-secure.s3.us-west-2.amazonaws.com/510cd684-c9a0-45bd-b45d-b35ad6027628/0d54ea9e-5495-473c-bd78-e2330093533b/Untitled.png)

# 3. DOM Query / Traversing (요소에 접근)

## 3.1 하나의 요소 노드 선택(DOM Query)

![Untitled](https://prod-files-secure.s3.us-west-2.amazonaws.com/510cd684-c9a0-45bd-b45d-b35ad6027628/4bc38592-7178-45e3-9c5c-1d3c3363cddf/Untitled.png)

- [document.getElementById(id)](https://developer.mozilla.org/ko/docs/Web/API/Document/getElementById)
  - id 어트리뷰트 값으로 요소 노드를 한 개 선택함. 복수개가 선택된 경우 첫번째 요소만 반환함.
  - Return: HTMLElement를 상속받은 객체
  - 모든 브라우저에서 동작

```jsx
// id로 하나의 요소를 선택한다.
const elem = document.getElementById('one');
// 클래스 어트리뷰트의 값을 변경한다.
elem.className = 'blue';

// 그림: DOM tree의 객체 구성 참고
console.log(elem); // <li id="one" class="blue">Seoul</li>
console.log(elem.__proto__);           // HTMLLIElement
console.log(elem.__proto__.__proto__); // HTMLElement
console.log(elem.__proto__.__proto__.__proto__);           // Element
console.log(elem.__proto__.__proto__.__proto__.__proto__); // Node
```

- [document.querySelector(cssSelector)](https://developer.mozilla.org/ko/docs/Web/API/Document/querySelector)
  - CSS 셀렉터를 사용하여 요소 노드를 한 개 선택함.
  - Return: HTMLElement를 상속받은 객체

```jsx
// CSS 셀렉터를 이용해 요소를 선택한다
const elem = document.querySelector('li.red');
// 클래스 어트리뷰트의 값을 변경한다.
elem.className = 'blue';
```

## 3.2 여러 개의 요소 노드 선택

![Untitled](https://prod-files-secure.s3.us-west-2.amazonaws.com/510cd684-c9a0-45bd-b45d-b35ad6027628/81157f22-aeca-4313-a89f-33d5cd943a28/Untitled.png)

- [document.getElementsByClassName(class)](https://developer.mozilla.org/ko/docs/Web/API/Document/getElementsByClassName)
  - class 어트리뷰트 값으로 요소 노드를 모두 선택함. 공백으로 구분하여 여러 개의 class를 지정할 수 있음.
  - Return: HTMLCollection (live)

------

- [document.getElementsByTagName(tagName)](https://developer.mozilla.org/ko/docs/Web/API/Element/getElementsByTagName)
  - 태그명으로 요소 노드를 모두 선택함.
  - Return: HTMLCollection (live)
  - 모든 브라우저에서 동작

------

- [document.querySelectorAll(selector)](https://developer.mozilla.org/ko/docs/Web/API/Document/querySelectorAll)
  - 지정된 CSS 선택자를 사용하여 요소 노드를 모두 선택함.
  - Return: [NodeList](https://developer.mozilla.org/ko/docs/Web/API/NodeList) (non-live)
  - IE8 이상의 브라우저에서 동작

## 3.3 DOM Traversing(탐색)

![Untitled](https://prod-files-secure.s3.us-west-2.amazonaws.com/510cd684-c9a0-45bd-b45d-b35ad6027628/cf8ab291-e1f2-4d77-86d3-d294303a3ee4/Untitled.png)

- [parentNode](https://developer.mozilla.org/ko/docs/Web/API/Node/parentNode)
  - 부모 노드를 탐색함.
  - Return: HTMLElement를 상속받은 객체
  - 모든 브라우저에서 동작

------

- [firstChild](https://developer.mozilla.org/ko/docs/Web/API/Node/firstChild), [lastChild](https://developer.mozilla.org/ko/docs/Web/API/Node/lastChild)
  - 자식 노드를 탐색함.
  - Return: HTMLElement를 상속받은 객체
  - IE9 이상의 브라우저에서 동작

------

- **[hasChildNodes()](https://developer.mozilla.org/ko/docs/Web/API/Node/hasChildNodes)**

• 자식 노드가 있는지 확인하고 Boolean 값을 반환함. • Return: Boolean 값 • 모든 브라우저에서 동작

------

- **[childNodes](https://developer.mozilla.org/ko/docs/Web/API/Node/childNodes)**

• 자식 노드의 컬렉션을 반환함. 텍스트 요소를 포함한 모든 자식 요소를 반환함. • Return: [NodeList](https://developer.mozilla.org/ko/docs/Web/API/NodeList) (non-live) • 모든 브라우저에서 동작

------

- **[children](https://developer.mozilla.org/ko/docs/Web/API/ParentNode/children)**

• 자식 노드의 컬렉션을 반환함. 자식 요소 중에서 Element type 요소만을 반환함. • Return: [HTMLCollection](https://developer.mozilla.org/ko/docs/Web/API/HTMLCollection) (live) • IE9 이상의 브라우저에서 동작

------

- **[previousSibling](https://developer.mozilla.org/ko/docs/Web/API/Node/previousSibling), [nextSibling](https://developer.mozilla.org/ko/docs/Web/API/Node/nextSibling)**

• 형제 노드를 탐색함. text node를 포함한 모든 형제 노드를 탐색함. • Return: HTMLElement를 상속받은 객체 • 모든 브라우저에서 동작

------

- **[previousElementSibling](https://developer.mozilla.org/en-US/docs/Web/API/NonDocumentTypeChildNode/previousElementSibling), [nextElementSibling](https://developer.mozilla.org/en-US/docs/Web/API/NonDocumentTypeChildNode/nextElementSibling)**

• 형제 노드를 탐색함. 형제 노드 중에서 Element type 요소만을 탐색함. • Return: HTMLElement를 상속받은 객체 • IE9 이상의 브라우저에서 동작