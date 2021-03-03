---
title: JavaScript - 모듈 번들러와 트랜스파일러
tags: JavaScript TIL
key: page-202103012053
summary : 모듈 번들러(Module bundler) , 트랜스파일러(Transpiler)
---
모듈이랑 모듈시스템의 정의는 [모듈시스템](https://dlgpal95.github.io/2021/02/26/module.html)을 참고하자

<br/>

## 모듈 번들러(Module bundler)란?
**여러 개로 나뉘어져 있는 JS파일을 하나의 "Javascript Bundle"파일로 만들어준다.** (의존성 처리) <br/>
모듈 번들러가 없으면 수동으로 파일을 결합하거나 수많은 ```<script>```태그를 사용하여 자바 스크립트를 HTML로 로드해야 한다.

**:heavy_check_mark: 번들러 없을때 단점**
- 필요한 코드와 적절한 로드 순서를 추적해야한다.
- ```<script>```태그가 여러 개인 경우 서버 호출이 많아져 성능이 저하된다.
- 수많은 수작업이 필요하다.

<br/>
번들러를 이용하여 결합, 축소 (코드를 더 작고 효율적으로), 코드 분할 (초기 로드시간을 축소) 및 Javascript를 로드하는 프로세스를 자동화한다. 번들러로는 ```Webpack, Parcel, Rollup``` 등이 있다.

<br/>

## 트랜스파일러(Transpiler)란?
**트랜스파일링(Transpiling)이란 어떤 특정 언어로 작성된 소스 코드를 다른 언어의 소스 코드로 변환하는 것**을 말한다. <br/>
이를 해주는 것이 트랜스파일러(Transpiler)이다. 트랜스파일러가 필요한 이유는 지원하지 않는 언어를 지원하는 다른 언어로 변환하기 위해서 이다.
<br/>

**:heavy_check_mark: 트랜스파일러의 기능**
- ES6+의 기능을 ES5 코드로 변환
- 리액트의 JSX를 자바스크립트 코드로 변환
- 타입스크립트를 자바스크립트로 변환
- sass를 CSS로 변환
등등..

<br/>
ES6+나 JSX를 변환시키는 트랜스파일러로는 ```바벨(Babel)```이 있으며 타입스크립트를 변환시키는 도구로는 타입스크립트 트랜스파일러가 있다.
보통 모듈 번들러에 트랜스파일러를 추가해서 사용하는 방식을 사용한다.
<br/><br/><br/><br/>
참고자료 : [https://ichi.pro/ko/modyul-beon-deulleo-sogae-278442518586853](https://ichi.pro/ko/modyul-beon-deulleo-sogae-278442518586853) <br/>
참고자료 : [https://ooz.co.kr/416](https://ooz.co.kr/416)

<br/>
<br/>
