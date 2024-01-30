# Webpack

------

# Webpack

- 모던 JavaScript 애플리케이션을 위한 정적 모듈 번들러임.
- 여러 파일을 하나 이상의 파일로 합쳐주는 자바스크립트 번들러.

------

# Webpack의 필요성

## 성능 최적화 & 자동화

- 코드 축소와 더불어 사용하지 않는 코드를 제거하는 tree shaking과 같은 최적화를 수행함으로써 HTTP 요청 수를 감소하여 웹사이트 성능을 궁극적으로 향상시키고, 로딩 속도를

## 파일 단위의 자바스크립트 모듈 관리

- HTML, CSS, JS, Image, Font 등 모든 파일 하나 하나 나눠서 모듈화하여, 웹 애플리케이션을 구성할 수 있게 해줌.

## 번들러가 제공하는 편의성

- CSS가 아니 Sass나 Stylus 등을 사용할 경우, 또는 TypeScript 사용 시 번들러가 컴파일 과정에서 필요한 플러그인을 추가하고 번들러를 실행해줌.

## Dependency Issue(종속성 문제) 해결

- 서버와 브라우저 모두에서 최대한 원활하게 작동할 수 있는 코드의 상당 부분을 빌드 시 모든 종속성과 함께 번들하는데 도움을 줌.

------

# Webpack의 핵심 요소

## Entry

- 엔트리 속성은 웹팩에서 웹 자원을 변환하기 위해 필요한 최초 진입점임.
- entry로 묶고자하는 파일의 첫번째 진입점을 설정해주면 됨.

```jsx
// webpack.config.js

//Single Page Application(SPA)
module.exports = {
  entry: './src/index.js'
}

//Multi Page Application (MPA)
module.exports = {
  entry: {
    login: './src/LoginView.js',
    main: './src/MaingView.js'
  }
}
```

- 최초 진입점이 되는 대상 파일은 웹 애플리케이션의 전반적인 구조와 내용이 담겨있어야 함. 그래야 웹팩이 해당 파일을 토대로 애플리케이션의 모듈들의 연관관계에 대해 이해하고 분석하고 합치기 때문.
- 모듈간의 의존관계가 생기는 구조를 디펜던시 그래프라고 부름.

## Output

- 웹팩을 실행하여 빌드하고 난 후 결과물의 파일 경로를 의미함.
- filename은 웹팩으로 빌드한 파일의 이름.
- path는 해당 파일의 경로.
- path 속성에서 사용된 메소드는 인자로 받은 경로를 조합하여 유효한 파일 경로를 만드는 Node.jsAPI라고 함.

```jsx
// webpack.config.js
var path = require('path');

module.exports = {
  output: {
    filename: 'bundle.js',
    path: path.resolve(__dirname, './dist')
  }
}

/* Node.js API가 하는 역할은 아래 코드와 동일함. */
output: './dist/bundle.js'
```

## Loader

- 웹팩이 애플리케이션을 해석할 때 자바스크립트 파일이 아닌 HTML, CSS, Images, font 등을 변환할 수 있게 도와주는 속성임.
- 웹팩은 모든 파일을 모듈로 취급하여 관리하는데 사실상 자바스크립트 파일만 알고 있어 로더를 이용해 다른 파일들을 웹팩이 이해하게끔 변경해줘야 함.
- 로더로 설정을 지정해주지 않으면 웹팩이 해당 파일을 읽을 수 없어 에러가 발생함.

### 사용되는 로더 종류

- CSS Loader
- Babel Loader
- Sass Loader
- File Loader
- Vue Loader
- TS Loader
- rules라는 객체로 속성을 지정하며, test => 로더를 적용할 파일 유형 (일반적으로 정규 표현식) use => 해당 파일에 적용한 로더의 이름

```jsx
// webpack.config.js

module.exports = {
  module: {
    rules: [
      { test: /\\.css$/, use: 'css-loader' },
      { test: /\\.ts$/, use: 'ts-loader' },
      // ...
     ]
  }
}
```

## Plugin

- 웹팩의 기본적인 동작에 추가적인 기능을 제공하는 속성임.
- 로더는 파일을 해석하고 변환하는 과정에 관여하며, 플러그인은 해당 결과물의 **형태를 바꾸는 역할**을 함.

```jsx
// webpack.config.js
var webpack = require('webpack');
var HtmlWebpackPlugin = require('html-webpack-plugin');

module.exports = {
  plugins: [
    new HtmlWebpackPlugin(),
    new webpack.ProgressPlugin()
  ]
}
```

- HtmlWebpackPlugin: 웹팩으로 빌드한 결과물로 HTML 파일을 생성해주는 플러그인.
- ProgressPlugin: 웹팩의 빌드 진행율을 표시해주는 플러그인.

------

## 참고 자료

- https://velog.io/@gusdh2/Webpack이란-왜-필요할까요#webpack의-핵심-요소