# JS DOM - 2

# 4. DOM Manipulation (조작)

## 4.1 텍스트 노드의 접근/수정

![Untitled](https://prod-files-secure.s3.us-west-2.amazonaws.com/510cd684-c9a0-45bd-b45d-b35ad6027628/5441cd6d-ce95-4d30-a4cd-3ef334a41ecc/Untitled.png)

- 요소의 텍스트는 텍스트 노드에 저장되어 있음.

------

- 텍스트 노드에 접근하는 방법

1. 해당 텍스트 노드의 부모 노드를 선택함. (텍스트 노드는 요소 노드의 자식임.)
2. firstChild 프로퍼티를 사용하여 텍스트 노드를 탐색함.
3. 텍스트 노드의 유일한 프로퍼티(nodeValue)를 이용하여 텍스트를 취득함.
4. nodeValue를 이용하여 텍스트를 수정함.

------

- nodeValue
  - 노드의 값을 반환함.
  - Return: 텍스트 노드의 경우는 문자열, 요소 노드의 경우 null 반환

------

- nodeName, nodeType을 통해 노드의 정보를 취득할 수 있음.

## 4.2 어트리뷰트 노드의 접근/수정

![Untitled](https://prod-files-secure.s3.us-west-2.amazonaws.com/510cd684-c9a0-45bd-b45d-b35ad6027628/e33330b4-426b-471d-a7ea-202842019562/Untitled.png)

- 어트리뷰트 노드를 조작할 때 사용할 수 있는 프로퍼티와 메소드
  - className
    - class 어트리뷰트의 값을 취득 또는 변경함. className 프로퍼티에 값을 할당하는 경우 class 어트리뷰트가 존재하지 않으면 class 어트리뷰트를 생성하고 지정된 값을 설정함.
    - class 어트리뷰트의 값이 여러 개일 경우 공백으로 구분된 문자열이 반환되므로 String 메소드 split( ‘  ‘)을 사용하여 배열로 변경하여 사용함.
  - classList
    - add, remove, item, toggle, contains, replace 메소드를 제공함.

------

- id
- id 어트리뷰트의 값을 취득 또는 변경함.
- id 프로퍼티에 값을 할당하는 경우 id 어트리뷰트가 존재하지 않으면 id 어트리뷰트를 생성하고 지정된 값을 설정함.

------

**[hasAttribute(attribute)](https://developer.mozilla.org/en-US/docs/Web/API/Element/hasAttribute)**

• 지정한 어트리뷰트를 가지고 있는지 검사함. • Return : Boolean • IE8 이상의 브라우저에서 동작함.

**[getAttribute(attribute)](https://developer.mozilla.org/ko/docs/Web/API/Element/getAttribute)** • 어트리뷰트의 값을 취득함. • Return : 문자열 • 모든 브라우저에서 동작함.

**[setAttribute(attribute, value)](https://developer.mozilla.org/ko/docs/Web/API/Element/setAttribute)** • 어트리뷰트와 어트리뷰트 값을 설정함. • Return : undefined • 모든 브라우저에서 동작함.

**[removeAttribute(attribute)](https://developer.mozilla.org/ko/docs/Web/API/Element/removeAttribute)** • 지정한 어트리뷰트를 제거함. • Return : undefined • 모든 브라우저에서 동작함.

------

## 4.3 HTMl 콘테츠 조작(Manipulation)

![Untitled](https://prod-files-secure.s3.us-west-2.amazonaws.com/510cd684-c9a0-45bd-b45d-b35ad6027628/7a0bf775-3f3c-45bf-a3d0-d081f02ebd9b/Untitled.png)

- HTML 콘텐츠를 조작하기 위해 아래의 프로퍼티 또는 메소드를 사용할 수 있음.

------

- textContent
- 요소의 텍스트 콘텐츠를 취득 또는 변경함.(마크업은 무시됨.)

------

**[innerText](https://developer.mozilla.org/ko/docs/Web/API/Node/innerText)**

• innerText 프로퍼티를 사용하여도 요소의 텍스트 콘텐츠에만 접근할 수 있음. 하지만 아래의 이유로 사용하지 않는 것이 좋음. ◦ 비표준임. ◦ CSS에 순종적이다. 예를 들어 CSS에 의해 비표시(visibility: hidden;)로 지정되어 있다면 텍스트가 반환되지 않음. ◦ CSS를 고려해야 하므로 textContent 프로퍼티보다 느림.

**[innerHTML](https://developer.mozilla.org/ko/docs/Web/API/Element/innerHTML)**

• 해당 요소의 모든 자식 요소를 포함하는 모든 콘텐츠를 하나의 문자열로 취득할 수 있음. 이 문자열은 마크업을 포함함.

------

- innerHTML 프로퍼티를 사용하여 마크업이 포함된 새로운 콘텐츠를 지정하면 새로운 요소를 DOM에 추가할 수 있음.

## 4.4 DOM 조작 방식

- 한 개의 요소를 추가하는 경우 innerHTML 프로퍼티를 사용하지 않고 새로운 콘텐츠를 추가할 수 있는 방법인 DOM을 직접 조작함.
- DOM 직접 조작

1. 요소 노드 생성 createElement() 메소드를 사용하여 새로운 요소 노드를 생성함.(createElement() 메소드의 인자로 태그 이름을 전달함.)
2. 텍스트 노드 생성 createTextNode() 메소드를 사용하여 새로운 텍스트 노드를 생성함.
3. 생성된 요소를 DOM에 추가 appendChild() 메소드를 사용하여 생성된 노드를 DOM tree에 추가함.(removeChild() 메소드를 사용하여 DOM tree에서 노드를 삭제할 수 있음.)

------

**[createElement(tagName)](https://developer.mozilla.org/ko/docs/Web/API/Document/createElement)**

• 태그이름을 인자로 전달하여 요소를 생성함. • Return: HTMLElement를 상속받은 객체 • 모든 브라우저에서 동작함.

**[createTextNode(text)](https://developer.mozilla.org/ko/docs/Web/API/Document/createTextNode)**

• 텍스트를 인자로 전달하여 텍스트 노드를 생성함. • Return: Text 객체 • 모든 브라우저에서 동작함.

**[appendChild(Node)](https://developer.mozilla.org/ko/docs/Web/API/Node/appendChild)**

• 인자로 전달한 노드를 마지막 자식 요소로 DOM 트리에 추가함. • Return: 추가한 노드 • 모든 브라우저에서 동작함.

**[removeChild(Node)](https://developer.mozilla.org/ko/docs/Web/API/Node/removeChild)**

• 인자로 전달한 노드를 DOM 트리에 제거함. • Return: 추가한 노드 • 모든 브라우저에서 동작함.

## 4.5 insertAdjacentHTML()

**[insertAdjacentHTML(position, string)](https://developer.mozilla.org/en-US/docs/Web/API/Element/insertAdjacentHTML)**

- 인자로 전달한 텍스트를 HTML로 파싱하고 그 결과로 생성된 노드를 DOM 트리의 지정된 위치에 삽입함.(첫번째 인자는 삽입 위치, 두번째 인자는 삽입할 요소를 표현한 문자열임.)
- 첫번째 인자로 올 수 있는 값
  - ‘beforebegin’
  - ‘afterbegin’
  - beforeend’
  - ‘afterend’

![Untitled](https://prod-files-secure.s3.us-west-2.amazonaws.com/510cd684-c9a0-45bd-b45d-b35ad6027628/07325fe2-9560-4665-b571-94c1933148c7/Untitled.png)

## 4.6 innnerHTML vs. DOM 조작 방식 vs. insertAdjacentHTML()

- innerHTML

| 장점                                                       | 단점                                                         |
| ---------------------------------------------------------- | ------------------------------------------------------------ |
| DOM 조작 방식에 비해 빠르고 간편함.                        | XSS공격에 취약점이 있기 때문에 사용자로 부터 입력받은 콘텐츠(untrusted data: 댓글, 사용자 이름 등)를 추가할 때 주의하여야 함. |
| 간편하게 문자열로 정의한 여러 요소를 DOM에 추가할 수 있음. | 해당 요소의 내용을 덮어 쓴다. 즉, HTML을 다시 파싱한다. 이것은 비효율적임. |
| 콘텐츠를 취득할 수 있음.                                   |                                                              |

- DOM 조작 방식

| 장점                                                         | 단점                                          |
| ------------------------------------------------------------ | --------------------------------------------- |
| 특정 노드 한 개(노드, 텍스트, 데이터 등)를 DOM에 추가할 때 적합하다. | innerHTML보다 느리고 더 많은 코드가 필요하다. |

- insertAdjacentHTML()

| 장점                                                       | 단점                                                         |
| ---------------------------------------------------------- | ------------------------------------------------------------ |
| 간편하게 문자열로 정의된 여러 요소를 DOM에 추가할 수 있다. | XSS공격에 취약점이 있기 때문에 사용자로 부터 입력받은 콘텐츠(untrusted data: 댓글, 사용자 이름 등)를 추가할 때 주의하여야 한다. |
| 삽입되는 위치를 선정할 수 있다.                            |                                                              |

- innerHTML 과 insertAdjacentHTML()은 크로스 스크립팅 공격에 취약함.
- 텍스트를 추가 또는 변경시에는 textContent, 새로운 요소의 추가 또는 삭제시에는 DOM 조작 방식을 사용하도록 함.

# 5. style

- style 프로퍼티를 사용하면 inline 스타일 선언을 생성함.(특정 요소에 inline 스타일을 지정하는 경우 사용함.)
- style 프로퍼티의 값을 취득하려면 [window.getComputedStyle](https://developer.mozilla.org/ko/docs/Web/API/Window/getComputedStyle)을 사용함.
- window.getComputedStyle 메소드는 인자로 주어진 요소의 모든 CSS 프로퍼티 값을 반환함.