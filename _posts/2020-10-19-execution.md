---
title: JavaScript - Execution Context(실행 컨텍스트)
tags: JavaScript TIL
key: page-202010191128
summary : 자바스크립트의 핵심원리인 실행컨텍스트에 대해 알아보자
---

## 실행 컨텍스트란?
실행 가능한 코드를 형상화하고 구분하는 추상적 개념이다.<br/>
즉, <b>실행 가능한 코드가 실행되기 위해 필요한 환경</b>이다.<br/>
<br/>
실행 가능한 코드는 3가지가 있다. 일반적으로 실행 가능한 코드는 전역코드, 함수코드이다. <br/>
- 전역코드 : 전역 영역에 존재하는 코드 <br/>
- Eval 코드 : eval함수로 실행되는 코드 <br/>
- 함수 코드 : 함수 내에 존재하는 코드 <br/>

<br/>
코드를 실행하기 위하여 필요한 여러가지 정보가 있다.<br/>

- 변수 : 전역변수, 지역변수, 매개변수, 객체의 프로퍼티<br/>
- 함수 선언<br/>
- 변수의 유효범위(Scope)<br/>
- this<br/>

## 논리적 스택 구조를 가지는 실행 컨텍스트 스택

자바스크립트 엔진은 실행 컨텍스트를 물리적 객체의 형태로 관리한다.

```javascript
var x = 'xxx';

function foo () {
  var y = 'yyy';

  function bar () {
    var z = 'zzz';
    console.log(x + y + z);
  }
  bar();
}
foo();
```

<img src="/assets/images/execution.png" width="700" height="200"/>


1.&ensp;실행 가능한 코드로 이동하면 논리적 스택 구조를 가지는 <b>실행 컨텍스트 스택이 생성</b>된다. <br/>
2.&ensp;전역코드로 진입하면 <b>전역 실행 컨텍스트가 생성</b>되고 실행 컨텍스트 스택에 쌓인다. <br/>
3.&ensp;전역코드에서 함수 호출 시 <b>함수 실행 컨텍스트가 생성</b>되고 전역 컨텍스트 위에 쌓인다. <br/>
4.&ensp;함수가 종료되면 <b>함수 실행 컨텍스트를 삭제</b>되며 직전에 실행 컨텍스트로 제어권이 넘어간다.<br/>
5.&ensp;전역코드가 끝나면 <b>전역 컨텍스트가 스택에서 삭제</b>되고(클로저제외), 애플리케이션이 종료된다. <br/>

## 실행 컨텍스트의 3가지 객체

실행컨텍스트는 생성 시 물리적으로 객체의 형태를 가지며 3가지 프로퍼티를 소유한다.

<img src="/assets/images/excute_structure.png" width="300" height="200"/>

### 1. Variable Object (VO / 변수객체)

실행 컨텍스트가 실행되면 자바스크립트 엔진은 실행에 필요한 여러 정보들을 담은 객체를 생성한다. <br/>
이 정보들을 담은 객체를  Variable Object라고 한다. <br/>

 Variable Object는 3가지의 정보를 담는다. <br/>
- 변수<br/>
- 매개변수(parameter)와 인수 정보(arguments)<br/>
- 함수 선언(함수 표현식은 제외)<br/>

Variable Object는 실행 컨텍스트의 프로퍼티이기 때문에 값을 갖는데 이 값은 다른 객체를 가리킨다. <br/>

#### 1.1 전역 컨텍스트 경우
최상위에 위치하고 모든 전역 변수, 전역 함수 등을 포함하는 유일한 <b>전역 객체(Global Object / GO)</b>를 가리킨다. <br/>
전역 객체는 전역에 선언된 전역 변수와 전역 함수를 프로퍼티로 소유한다.<br/>

<img src="/assets/images/ec-vo-global.png" width="400" height="200"/>

#### 1.2 함수 컨텍스트 경우
<b>Activation Object(AO / 활성 객체)</b>를 가리킨다.<br/>
매개변수와 인수들의 정보를 배열의 형태로 담고 있는 객체인 arguments object가 추가된다.<br/>

<img src="/assets/images/ec-vo-foo.png" width="500" height="200"/>


### 2. Scope Chain (SC)
해당 전역 또는 함수가 참조할 수 있는 변수, 함수 선언 등의 정보를 담고 있는 전역 객체(GO) 또는 활성 객체(AO)의 리스트를 가리킨다. <br/>
<img src="/assets/images/ec-sc.png" width="400" height="300"/>

현재 실행 컨텍스트의 활성 객체(AO)를 선두로 하여 순차적으로 상위 컨텍스트의 활성 객체(AO)를 가리키며 마지막 리스트는 전역 객체(GO)를 가리킨다.<br/>
스코프 체인은 <b>식별자 중에서 객체(전역 객체 제외)의 프로퍼티가 아닌 식별자, 즉 변수를 검색하는 메커니즘</b>이다. <br/>
식별자 중에서 변수가 아닌 객체의 프로퍼티(물론 메소드도 포함된다)를 검색하는 메커니즘은 프로토타입 체인(Prototype Chain)이다. <br/>

### 3. this value
this 프로퍼티에는 this 값이 할당된다.<br/>
함수 호출 패턴에 의해 결정되며, 아무런 값도 지정되어 있지 않으면 window를 값으로 가진다.
<br/><br/><br/>

참고자료 : [https://poiemaweb.com/js-execution-context#2-%EC%8B%A4%ED%96%89-%EC%BB%A8%ED%85%8D%EC%8A%A4%ED%8A%B8%EC%9D%98-3%EA%B0%80%EC%A7%80-%EA%B0%9D%EC%B2%B4](https://poiemaweb.com/js-execution-context#2-%EC%8B%A4%ED%96%89-%EC%BB%A8%ED%85%8D%EC%8A%A4%ED%8A%B8%EC%9D%98-3%EA%B0%80%EC%A7%80-%EA%B0%9D%EC%B2%B4)

<br/><br/><br/>
