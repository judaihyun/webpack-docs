

# Loaders

Loader는 `import`하거나 `load`한 소스 코드에 적용되는 프론트 엔드 전처리 변환를 제공하는  도구입니다.  Loader는 TypeScript와 같은 다른 언어나 data URL로 표현되는 인라인 이미지들을 변환시켜줍니다. 또한 `import`를 통하여 CSS 파일도 포함시켜 줄 수 있습니다.

## Example

For example, you can use loaders to tell webpack to load a CSS file or to convert TypeScript to JavaScript. To do this, you would start by installing the loaders you need:

Loader를 사용하여 웹팩에게 CSS파일을 불러오거나 TypeScript를 JavsScript로 변환시켜 줄 수 있습니다. 
Loader의 설치는 다음과 같습니다.
```
npm install --save-dev css-loader ts-loader  
( css, typescript 로더 )
```

웹팩에게 [`css-loader`](https://webpack.js.org/loaders/css-loader)와  [`ts-loader`](https://github.com/TypeStrong/ts-loader)를 이용하여 모든 `.css`, `.ts`파일을 변환하라고 설정할 수 있습니다.

**webpack.config.js**

```
module.exports = {
  module: {
    rules: [
      { test: /\.css$/, use: 'css-loader' },
      { test: /\.ts$/, use: 'ts-loader' }
    ]
  }
};
```

## Using Loaders

로더를 사용하는 방법에는 세가지가 존재합니다.

-   [Configuration](https://webpack.js.org/concepts/loaders/#configuration)  (권장):  **webpack.config.js** 파일에 대한 설정.

-   [Inline](https://webpack.js.org/concepts/loaders/#inline): 각 소스코드에  `import`  문을 통한 방법.

-   [CLI](https://webpack.js.org/concepts/loaders/#cli): 스크립트 명령어를 통한 방법.

### Configuration 방식

아래의 [`module.rules`](https://webpack.js.org/configuration/module/#modulerules) 에서 웹팩 설정에서 여러개의 Loader를 지정할 수 있습니다.  이 설정을 통하여 웹팩에 어떠한 모듈이 적용되어 있고 사용되는지 한눈에 파악할 수 있습니다.

Loader는 오른쪽에서 왼쪽(또는 아래에서 위로)으로 평가/실행됩니다. 아래 설정의 경우 sass-loader, css-loader, style-loader의 순서로 실행됩니다.

["Loader Features"](https://webpack.js.org/concepts/loaders/#loader-features)에서 더 자세한 로더의 특징을 살펴볼 수 있습니다.

```javascript
module.exports = {
  module: {
    rules: [
      {
        test: /\.css$/,
        use: [
          // style-loader
          { loader: 'style-loader' },
          // css-loader
          {
            loader: 'css-loader',
            options: {
              modules: true
            }
          },
          // sass-loader
          { loader: 'sass-loader' }
        ]
      }
    ]
  }
};
```

### Inline 방식

`import`구문을 이용하거나 [equivalent "importing" method](https://webpack.js.org/api/module-methods)를 통하여 Loader를 지정할 수 있고 `!`문자로 로더를 분리할 수 있습니다. (각 Loader 부분은 현재 디렉토리를 기준으로 상대 경로입니다.)

```javascript
import Styles from 'style-loader!css-loader?modules!./styles.css';
```

또한 모든 preLoader, postLoader등을 `!`을 이용하여 재정의 할 수 있습니다.

- `!` 를 이용하면 모든 일반 Loader가 제외됩니다.
```javascript
import Styles from '!style-loader!css-loader?modules!./styles.css';
```

- `!!`를 이용하면 모든 Loader가 제외됩니다.(preLoaders, loaders, postLoaders)
```javascript
import Styles from '!!style-loader!css-loader?modules!./styles.css';
```

- `-!`를 이용하면 postLoader를 제외한 로더들이 제외됩니다.

```javascript
import Styles from '-!style-loader!css-loader?modules!./styles.css';
```

이곳에 `?key=value&foo=bar` 와 같은 쿼리 파라미터, `?{"key":"value","foo":"bar"}` JSON object도 넘겨줄 수 있습니다.

앞서 밝혔듯이 `module.rules`(Configuration)을 이용하는 것이 보일러 플레이트 감소, 더 빠른 로딩, 편하게 디버깅 할 수 있습니다.

### CLI

아래와 같이 CLI을 통하여 Loader를 사용할 수 있습니다.
```javascript
webpack --module-bind jade-loader --module-bind 'css=style-loader!css-loader'
```


## Loader Features

- Loader는 체인으로 묶이며, 이 체인은 역순으로 실행됩니다. 첫 번째 로더에 의한 변환된 자원은 그 다음 로더에 전달되는 식입니다. 그리고 마지막 로더에 의하여 JavaScript로 리턴됩니다.

- Loader는 동기/비동기식으로 실행됩니다.

- Loader는 Node.js에서 동작하며 Node.js에서 가능한 모든 것을 할 수 있습니다.

- Loader는 `options`으로 설정할 수도 있습니다.(deprecated 됐지만 아직 지원하는 `query`파라미터도 사용가능)

- Normal module은 `package.json`을 통해 일반 `main`외에 `loader`필드로 loader를 내보낼 수 있습니다.

- 플러그인은 Loader에게 기능을 추가합니다.

-  Loader는 추가 임의 파일을 내보낼 수 있습니다. can emit additional arbitrary files.

Loader는 전처리 기능을 통하여 output을 사용자 지정하는 방법을 제공합니다. 이로써 사용자는 압축, 패키징, 언어 변환, 잘 다듬어진 로직들을 include하는데 더 유연해집니다. 


## Resolving Loaders

Loader는 표준 [module resolution](https://webpack.js.org/concepts/module-resolution/)를 따르고 대부분의 케이스에서는 [module path](https://webpack.js.org/concepts/module-resolution/#module-paths) 에서 로드됩니다.

로더 모듈은 Node.js와 호환되는 JavaScript로 작성된 function을 내보내어져야 합니다. 주로 npm을 통하여 관리하지만 사용자 정의 loader를 통하여도 이를 설정할 수 있습니다.  
