# HTML5 Tag - Link

## 하이퍼링크(hyper link)

- 한 텍스트에서 다른 텍스트로 건너뛰어 읽을 수 있는 기능.
- HTMl link는 hyperlink를 의미하며 a tag가 그 역할을 담당함.

```
<!DOCTYPE html>
<html>
    <body>
        <a href="<http://www.google.com>">Visit google.com!</a>
    </body>
</html>
```

- result
  - [Visit google.com!](http://www.google.com/)

## 1. href 어트리뷰트

- href 어트리뷰트는 이동하고자 하는 파일의 위치(경로)를 값으로 받음.
- 경로(path)란 파일 시스테 상에서 특정 파일의 위치를 의미함.

### 1.1 디렉터리(Directory)

- 디렉터리는 파일과 다른 디렉터리를 갖는 파일 시스템 내의 존재물로서 폴더라고도 불림.

**루트 디렉터리**

파일 시스템 계층 구조 상의 최상위 디렉터리이다. • Unix: / • Windows: C:\

**홈 디렉터리**

시스템의 사용자에게 각각 할당된 개별 디렉터리이다. • Unix: /Users/{계정명} • Windows: C:\Users\{계정명}

**작업 디렉터리**

작업 중인 파일의 위치한 디렉터리이다. • ./

**부모 디렉터리**

작업 디렉터리의 부모 디렉토리이다. • ../

### 1.2 파일 경로(File Path)

- 파일 경로는 파일 시스템에서 파일의 위치를 나타내는 방법임.
- 경로에는 절대경로와 상대경로가 있음.

**절대경로(Absolute path)**

현재 작업 디렉터리와 관계없이 특정 파일의 절대적인 위치를 가리킨다. 루트 디렉터리를 기준으로 파일의 위치를 나타낸다. • http://www.mysite.com/index.html • /Users/leeungmo/Desktop/myImage.jpg • C:\users\leeungmo\Desktop\myImage.jpg • /index.html

**상대경로(Relative path)**

현재 작업 디렉터리를 기준으로 특정 파일의 상대적인 위치를 가리킨다. • ./index.html • ../dist/index.js • ../../dist/index.js • index.html • html/index.html

- href 어트리뷰트에 사용 가능한 값

| Value               | Description                                                  |
| ------------------- | ------------------------------------------------------------ |
| 절대 URL            | 웹사이트 URL (href=”http://www.example.com/default.html”)    |
| 상대 URL            | 자신의 위치를 기준으로한 대상의 URL (href=”html/default.html”) |
| fragment identifier | 페이지 내의 특정 id를 갖는 요소에의 링크 (href=”#top”)       |
| 메일                | mailto:                                                      |
| script              | href=”javascript:alert(‘Hello’);                             |

## 2. target 어트리뷰트

- target 어트리뷰트는 링크를 클릭했을 때 윈도우를 어떻게 열지를 지정함.

| Value  | Description                                                  |
| ------ | ------------------------------------------------------------ |
| _self  | 링크를 클릭했을 때 연결문서를 현재 윈도우에서 오픈한다 (기본값) |
| _blank | 링크를 클릭했을 때 연결문서를 새로운 윈도우나 탭에서 오픈한다 |

```html
<!DOCTYPE html>
<html>
    <body>
        <a href="<http://www.google.com>" target="_blank" rel="noopener noreferrer">Visit google.com!</a>
    </body>
</html>
```

- result
  - [Visit google.com!](http://www.google.com/)