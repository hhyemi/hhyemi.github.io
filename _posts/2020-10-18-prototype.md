---
title: JavaScript - Prototype(프로토타입)
tags: javaScript
key: page-202010181853
summary : js prototype을 알아보자
---

## Prototype(프로토타입)이란
자바스크립트는 프로토타입 기반의 언어이다.<br/>
자바스크립트는 객체 원형인 프로토타입을 이용하여 새로운 객체를 생성한다. (Java에서의 class와 동일한 의미이다.) <br/>
어떠한 객체가 생성될 때 사용한 <b>객체의 원형을 프로토타입</b>이라고 한다. 이렇게 생성된 객체는 다른 객체의 원형이 될 수 있다. <br/>

```javascript
function Person(name,age){
    this.name = name;
    this.age = age;
    this.hello = function(){
      console.log('hello',this.name);
    }
}

const a = new Person('a',26);
const b = new Person('b',27);

a.hello(); // hello a
b.hello(); // hello b
```
Person이라는 객체의 원형을 사용하여 새로운 a,b 객체를 생성하였다. <br/>
객체의 원형에 있는 `hello();`를 a,b 둘 다 사용이 가능하다.


이번엔 Person의 원형이 되는 prototype Object에 직접 접근해보자.
```javascript
function Person(name,age){
    this.name = name;
    this.age = age;
}

Person.prototype.hello = function(){
    console.log('hello',this.name);
}
const a = new Person('a',26);

a.hello(); // hello a
```
Person 함수에 hello를 선언하지 않았지만 `a.hello();`사용이 가능한 이유는
Person의 원형이 되는 prototype Object에 직접 접근하였기 때문이다.
자바스크립트의 모든 객체는 Object 객체의 프로토타입을 기반으로 확장되어 있어 연결의 끝은 Object이다. <br/>
<br/>
## Prototype Object
함수를 정의하면 함수와 함께 생성되는 객체이다.
### 속성
- <b>`Object.prototype.constructor`</b> : 객체의 프로토타입을 생성하는 함수를 지정한다.
- <b>`Object.prototype.__proto__`</b> : 객체를 만들어낼 때 프로토타입으로 사용된 객체를 가리킨다.

<br/>

## Prototype chain
특정 객체의 속성이나 메소드에 접근할 때 해당 속성이나 메소드가 없는 경우
Prototype으로 이동하여 객체 내 속성과 메소드를 찾는다. (prototype 상속)
이러한 객체들의 연쇄를 <b>프로토타입 체인(prototype chain)</b>이라고 한다.

```javascript
function Person(){}

Person.prototype.hello = function(){
    console.log('hello');
}

function Job(name){
    this.name = name;
    this.where = function(){
        console.log('where',this.name);
    };
}

Job.prototype = Person.prototype; // Job의 prototype을 Person의 prototype으로 바꿈

const k = new Job('SeongNam');

k.hello();
k.where();

console.log( k instanceof Person); // true
console.log( k instanceof Job); // true
console.log( k instanceof Object); // true
```
`k.hello();` 와 `k.where();`가 둘 다 되는 것을 볼 수 있다. <br/>
가장 가까운 것은 Job이고 여기에 prototype을 가지고 있는 체인을 Person이 가지고 있다. <br/>
또 Object가 주는 예를 들면 toString() 등 prototype으로 가지고 있는 것이다.

<br/>

참고자료 : [http://insanehong.kr/post/javascript-prototype/](http://insanehong.kr/post/javascript-prototype/)

<br/><br/><br/><br/>
