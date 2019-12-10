---
title: Output
sort: 3
contributors:
  - JdevH
---

`output`옵션을 설정하면 컴파일된 파일(`bundles`)을 디스크에 쓰는 방법을 웹팩에게 알려주는 것입니다. `entry point`는 여러 곳일 수 있지만 `output`은 하나만 지정된 다는 것을 유의해주세요.


## Usage

웹팩 config에서 `output`프로퍼티에 대한 최소 요구 조건은 다음과 같이 [`output.filename`](https://webpack.js.org/configuration/output/#outputfilename) 설정 값을 Object로써 설정하는 것입니다.


__webpack.config.js__

```javascript
module.exports = {
  output: {
    filename: 'bundle.js',
  }
};
```

위 설정은 `dist`디렉토리에 단일 `bundle.js`파일로 출력하게 됩니다.



## Multiple Entry Points

만약 설정이 싱글 chunk(mutiple entry point 또는 CommonChunkPlugins) 이상일 때 각 파일이 고유한 이름을 갖도록 설정해야 합니다.

```javascript
module.exports = {
  entry: {
    app: './src/app.js',
    search: './src/search.js'
  },
  output: {
    filename: '[name].js',
    path: __dirname + '/dist'
  }
};

// writes to disk: ./dist/app.js, ./dist/search.js
```


## Advanced

아래는 assets에 대한 CDN을 이용하는 방법입니다.

__config.js__

```javascript
module.exports = {
  //...
  output: {
    path: '/home/proj/cdn/assets/[hash]',
    publicPath: 'http://cdn.example.com/assets/[hash]/'
  }
};
```

컴파일 시간에 출력 파일의 `publicPath`를 알 수 없는 경우, `__webpack_public_path__`변수를 통하여 런타임에 동적으로 설정하게 할 수도 있습니다.

```javascript
__webpack_public_path__ = myRuntimePublicPath;

// rest of your application entry
```
