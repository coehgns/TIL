# CSS3 Layout

- layout의 핵심은 블록 레벨 요소들을 원하는 위치에 배열하는 것.

- CSS를 사용하여 layout을 구성할 때에 자주 사용되는 핵심 기술은 float임.

- 전형적인 웹사이트의 layout

  ![layout-default.png](https://prod-files-secure.s3.us-west-2.amazonaws.com/510cd684-c9a0-45bd-b45d-b35ad6027628/29427901-fa21-430f-9c90-4fe9b6416eed/layout-default.png)

- layout이란 웹사이트를 구성하는 요소들을 배치할 공간을 분할하고 정렬하는 것임.

- 공간을 분할할 때는 먼저 행을 구분한 후, 행 내부 요소를 분리하는 것이 일반적임.

```html
<!DOCTYPE html>
<html>
<body>
  <div id="wrap">
    <header>
      <nav>
        <ul>
          <li>...</li>
          <li>...</li>
        </ul>
      </nav>
    </header>
    <div id="content-wrap">
      <aside>
        <ul>
          <li>...</li>
          <li>...</li>
        </ul>
      </aside>
      <section>
        <article>...</article>
        <article>...</article>
      </section>
    </div>
    <footer></footer>
  </div>
</body>
</html>
```

- result

  ![column layout.png](https://prod-files-secure.s3.us-west-2.amazonaws.com/510cd684-c9a0-45bd-b45d-b35ad6027628/2054d60b-5942-43f2-9152-52c7367971ab/column_layout.png)

## 1. Header & Navigation Bar

- 대부분의 웹사이트느 Navigation Bar를 가지고 있음. Navigation Bar는 웹사이트의 필수 구성 요소라고 할 수 있음.
- Navigation Bar는 기본적으로 링크들의 리스트임. 따라서 ul, li tag를 이용하여 작성하는 것이 일반적임.

## 2. Section & Aside

- 콘텐츠의 영역을 Section, 콘텐츠에 대한 Navigation item이나 부가 정보 영역을 Aside라 함.
- Section 영역은 다시 article 영역으로 구분할 수 있음.
- header 요소 뒤에 asdie, section, article을 포함하는 content-wrap 요소를 정의함.

```html
<div id="content-wrap">
  <aside>
    <h1>Aside</h1>
    <ul>
      <li><a href="#" class="active">London</a></li>
      <li><a href="#">Paris</a></li>
      <li><a href="#">Tokyo</a></li>
      <li><a href="#">Newyork</a></li>
    </ul>
  </aside>
  <section>
    <article id="london">
      <h1>London</h1>
      <p>...</p>
    </article>
    <article id="paris">
      <h1>Paris</h1>
      <p>...</p>
    </article>
    <article id="tokyo">
      <h1>Tokyo</h1>
      <p>...</p>
    </article>
    <article id="newyork">
      <h1>Newyork</h1>
      <p>...</p>
    </article>
  </section>
<!-- end of content-wrap   -->
</div>
```

- result

  ![section & aside.png](https://prod-files-secure.s3.us-west-2.amazonaws.com/510cd684-c9a0-45bd-b45d-b35ad6027628/7b92b69c-800b-477e-9361-fc3163c16778/section__aside.png)

## 3. footer

- content-wrap 영역 다음에 footer를 배치함.

```html
<footer>© Copyright 2016 ungmo2</footer>
```

- footer는 absolute 프로퍼티를 설정함. absolute를 사용하면 다른 요소가 먼저 위치를 점유하고 있어도 뒤로 밀리지 않고 덮어쓰게 됨.

```css
/*footer의 style 정의*/
footer {
  /* footer를 aside위에 올리기 위해 사용(부유객체) */
  position: absolute;
  height: 60px;
  width: 100%;
  padding: 0 25px;
  line-height: 60px;
  color: #8a8c8f;
  border-top: 1px solid #dee5e7;
  background-color: #f2f2f2;
}
```