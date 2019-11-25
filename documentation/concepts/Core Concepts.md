Concepts  ( https://webpack.js.org/concepts/ )
---------



<a name="4949">

# Core Concepts

</a>


Webpack 4.0


<div>웹팩 : Webpack 은 공식 사이트 이미지에서 소개하듯이 웹페이지를 동작시키기 위한 서로 연관 관계가 있는 웹 자원(웹앱 애플리케이션의 구성파일)들인 js, css, img, webfont, etc.. 와 같은 구성파일들의 관계들을 Webpack 에서 인식하여 번들링하게 되면 최종적으로 기존의 원본 파일들을 압축, 축소하여 최적화된 스택틱 자원(파일)으로 변환해주는 작업(웹페이지 성능 최적화)을 하게 되는데 이러한 작업을 번들링이라고 하고 webpack은 모듈 번들러이다.</div>

<div>모듈 번들러 : 모듈 번들러란 웹 애플리케이션을 구성하는 웹 자원(HTML, CSS, Javscript, Images 등)을 모두 각각의 모듈로 보고 이 자원들의 의존성 관계들을 묶고 조합하여 병합된 하나의 결과물(스택틱한 자원으로 변환)을 자동으로 만들어 주는 도구를 의미합니다.</div>



##### Concepts

</a>

<a name="4949"></a>
*   <a name="4949"></a>

    <div><a name="4949">웹팩의 핵심은 Modern Javascript Application을 위한 정적 모듈 번들러다. 웹팩이 application을 처리할때, 프로젝트가 필요로 하는 모든 모듈을 매핑하고 하나 이상의 bundles를 생성하는</a> [dependency graph](https://webpack.js.org/concepts/dependency-graph/)를 내부적으로 구축한다.</div>

*   <div>4.0.0 버전부터 웹팩은 configuration file을 필요로 하지 않지만 더 나은 요구를 충족하기 위해서는 config설정이 필요하다.</div>

<div>To get started you only need to understand its Core Concepts: </div>

[sublink]

*   <div>Entry</div>

*   <div>Output</div>

*   <div>Loaders</div>

*   <div>Plugins</div>

*   <div>Mode</div>

*   <div>Browser Compatibility</div>

<div>module bundlers에 대한 숨겨진 아이디어와 어떻게 동작하는 지에 대하여 이해하고자 하면 다음 리소스를 참고.</div>

*   <div>Manually Bundling an Application</div>

*   <div>Live Coding a Simple Module Bundler</div>

*   <div>Detailed Explanation of a Simple Module Bundler</div>

</div>

</div>
