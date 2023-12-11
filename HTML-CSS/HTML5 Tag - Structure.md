- 웹페이지의 레이아웃을 구성하기 위해서 공간을 분할할 필요가 있음.

![html-layout.png](https://prod-files-secure.s3.us-west-2.amazonaws.com/510cd684-c9a0-45bd-b45d-b35ad6027628/7eab0f83-ce93-4307-8c6a-06c3fef71faa/html-layout.png)

- 공간을 분할할 수 있는 태그는 div, span, table 등이 있는데, 과거에는 table 태그를 사용하여 레이아웃을 구성하기도 하였을나 모던 웹에서는 주로 div를 사용하여 레이아웃을 구성함.
- div 태그는 의미론적으로 어떠한 의미도 가지고 있지 않으므로 HTML5에서 새롭게 추가된 시맨틱 태그를 사용하는 것이 더 나은 방법임.
- IE에서 작동하지 않으므로 주의 필요.

| tag     | Description                                          |
| ------- | ---------------------------------------------------- |
| header  | 헤더를 의미한다                                      |
| nav     | 내비게이션을 의미한다                                |
| aside   | 사이드에 위치하는 공간을 의미한다                    |
| section | 본문의 여러 내용(article)을 포함하는 공간을 의미한다 |
| article | 분문의 주내용이 들어가는 공간을 의미한다             |
| footer  | 푸터를 의미한다                                      |