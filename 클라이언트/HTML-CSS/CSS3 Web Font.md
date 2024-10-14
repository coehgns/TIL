# CSS3 Web Font

## 1. CDN(Content Delivery Network) 링크 방식

- 구글에서 제공하는 웹폰트를 사용하는 방법.

```css
@import url(<http://fonts.googleapis.com/earlyaccess/nanumgothic.css>);

* { font-family: 'Nanum Gothic', sans-serif; }
```

Google Font에서 사용하고자 하는 웹폰트를 선택.

아래 구문을 CSS 파일에 추가.

@import rule의 url 함수는 서버에서 혹은 지정된 url에서 파일을 찾아 다운로드.

## 2. 서버 폰트 로딩 방식

- Google Font를 사용하기 위해 CDN 링크를 사용하는 방법은 간편한 방법이지만 로딩 속도가 느린 단점이 있음. 이러한 단점을 보완한 방법이 서버 폰트 로딩 방식임.
- @font-face 규칙으로 폰트를 등록하고 font-family 프로퍼티로 폰트를 선택하여 사용할 수 있음.

```css
/* IE 9~ & all browsers */
@font-face {
  font-family: myFontName;
  src: url("myFont.woff");
}

* { font-family: myFontName, sans-serif; }
```