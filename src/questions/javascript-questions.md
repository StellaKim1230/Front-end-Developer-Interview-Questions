---
title: JavaScript Questions
layout: layouts/page.njk
permalink: /questions/javascript-questions/index.html
---

* event bubbling
  - 특정 요소에서 이벤트가 발생했을 때 해당 이벤트가 상위 요소들로 전달되어 가는 특성
* event capturing
  - 이벤트 버블링과 반대 방향으로 이벤트가 전달되어 가는 방식
* event stopPropagation
  - 이벤트가 전파 되는것을 막는다. 예를들어, 이벤트 버블링의 경우 클릭한 요소의 이벤트만 발생시키고 상위 요소로 이벤트를 전달하는 것을 막는다.
* Explain event delegation
  - 하위 요소에 각각 이벤트를 붙이지 않고 상위 요소에서 하위 요소의 이벤트를 제어하는 방식
* Explain how `this` works in JavaScript
  - this는 함수가 호출되는 방식에 따라 달라진다.
  - 함수를 호출할 때 new 키워드를 사용하는 함수 내부에 있는 this는 완전히 새로운 객체이다.
  - apply, call, bind가 함수의 호출 / 작성에 사용되는 경우 함수 내의 this는 인수로 전달된 객체다.
  - obj.method()와 같이 함수를 메서드로 호출하는 경우 this는 함수가 프로퍼티인 객체이다.
  - 함수가 자유함수로 호출되는 경우 즉 위의 조건 없이 호추되는 경우 this는 전역 객체이다. 브라우저에서는 window 객체이다. 엄격모드('use strict') 일 경우 this는 전역 객체 대신 undefined 입니다.
  - 함수가 화살표 함수인 경우 모든 규칙을 무시하고 생성된 시점에서 주변 스코프의 this 값을 받는다.
* Explan prototype [참고링크](http://www.nextree.co.kr/p7323/)
  - javascript는 클래스라는 개념이 없다. 기존의 객체를 복사하여 새로운 객체를 생성하는 프로토타입 기반의 언어다. 프로로타입의 단어 뜻은 원형이라는 뜻이며, 프로토타입 기반 언어는 객체 원형인 프로토타입을 이용하여 새로운 객체를 만들어 냅니다. 이렇게 생성된 객체 역시 또 다른 객체의 원형이 될 수 있다.
* 함수와 객체의 내부 구조 (Person 이라는 함수가 있다고 가정)
  function Person() {}
  - Person 함수를 정의하면 함수 멤버로 prototype 속성 있다. Person 함수가 메모리에 쌓인다. (prototype 속성은 Person 프로토타입 객체를 참조한다.)
  - Person 함수를 정의하는 즉시 다른 메모리에 생성된 Person의 프로토타입 객체가 만들어진다. (프로토타입 객체 멤버인 constructor 속성은 Person 함수를 참조한다.)
  - Person 함수의 prototype 속성이 참조하는 프로토타입 객체는 new라는 연산자와 Person 함수를 통해 생성된 모든 객체의 원형이 되는 객체이다. 즉, 생성된 모든 객체가 참조한다.
  - javascript 에서는 기본 데이터 타입인 boolean, number, string, null, undefined 빼고는 모두 객체이다. 사용자가 정의한 함수도 객체이고 new라는 연산자를 통해 생성된 것도 객체이다.
  - 객체 안에는 __proto__ 라는 속성이 있는데 이 속성은 객체가 만들어지기 위해 사용된 원형의 프로토타입 객체를 참조한다.
  - new로 만들어진 객체는 prototype 속성은 없고, __proto__ 속성은 있다.
  ```
  function Person() {}
  var joon = new Person()  // joon.__proto__ 는 Person 프로토타입 객체를 참조한다.
  var jisoo = new Person() // jisoo.__proto__ 는 Person 프로토타입 객체를 참조한다.

  Person.prototype.getType = function() {
    return '사람' // 프로토타입 객체에 멤버를 추가, 수정, 삭제를 할 때는 함수 안의 prototype 속성을 사용해야 한다.
    // 프로토타입 멤버를 읽을 때는 함수안의 prototype속성 또는 객체 이름으로 접근한다.
  }
  console.log(joon.getType()) // 사람
  console.log(jisoo.getType()) // 사람
  ```
  ```
  joon.getType = function() {
    return '인간';
  }
  // 생성된 객체를 이용하여 프로토타입 객체의 멤버를 수정하면 프로토타입 객체에 있는 멤버를 수정하는 것이 아니라 자신의 객체에 멤버를 추가하는 것이다.
  joon 객체를 사용하여 getType()을 호출하면 프로토타입 객체의 getType()을 호출한 것이 아니다.
  joon 객체에 추가된 getType()을 호출한 것이다.
  즉, 사용된 객체의 원형인 프로토타입 객체의 멤버를 수정할 경우는 멤버 추가와 같이 함수의 prototype 속성을 이용하여 수정한다.

  console.log(joon.getType()) // 인간
  console.log(jisoo.getType()) // 사람

  jisoo.age = 25
  console.log(joon.age) // undefined
  console.log(jisoo.age) // 25

  Perton.prototype.getType = function() {
    return '인간';
  }
  console.log(jisoo.getType()) // 인간
  ```
  ```
  결론 : 프로토타입 객체는 정의된 함수의 새로운 객체가 생성되기 위한 원형이 되는 객체입니다.
  같은 원형으로 생성된 객체가 공통으로 참조하는 공간이다.
  프로토타입 객체의 멤버를 추가, 수정, 삭제는 함수의 prototype 속성을 통해 접근해야 한다.

  프로토타입이란? : JavaScript 에서는 기본 데이터 타입을 제외한 모든 것이 객체다.
  객체가 만들어지기 위해서는 자신을 만드는데 사용된 원형의 프로토타입 객체를 이용하여 객체를 만든다.
  이때 만들어진 객체 안에 __proto__ 속성이 자신을 만들어낸 원형을 의미하는 프로토타입 객체를 참조하는 숨겨진 링크가 있다.
  이 숨겨진 링크를 프로토타입이라고 정의한다.
  ```
* Explain how prototypal inheritance works (Explain Prototype Chain 같이 설명)
  ```
  function Person1() {}
  Person1.prototype.getName = function() { return 'kim' }
  const f1 = new Person1()
  fi.getName()  // kim

  class Human extends Person1{}
  Human.prototype.getType = function() { return 'human' } // Human의 prototype속성을 통해 getType이라는 함수를 만들었다.
  Human을 원형으로 생성된 객체들이 getType을 참조 할 수 있다.

  const h1 = new Human
  h1.getName() // kim
  // kim이 출력되는 이유 : h1은 Human의 객체이고, h1를 만들게 해 준 원형 객체의 프로토타입을 참조한다.
  Human의 getName()이 없으면, 상속받은 Person 프로토타입 객체에서 getName을 찾는다.(이때 kim이 출력)
  만약 Person 프로토타입 객체에도 없다면 Person 이 상속받고 있는 Object 객체의 프로토타입에서 찾는데 여기서도 없으면 undefined를 출력한다. (prototype chain)
  h1.getType() // human
  // Human 프로토타입 객체에 getType함수를 생성했기 때문에 Person까지 찾지 않고 Human에서 찾은 human을 리턴시킨다.

  const h2 = new Human
  h2.getName = function() { return 'han' }
  h2.getName() // han : 바로 위에서 h2객체 자신에 getName 함수를 만들었다. getName을 찾았고, 바로 han으로 리턴됨.
  h1.getName() // kim
  h2.getType() // human

  ---> 함수를 정의하면 constructor, __proto__를 갖는 프로토타입 객체가 생성되고, 이 함수의 새로운 객체를 만들면 그 새로운 객체는 __proto__라는 속성을 갖는다.
  이 새로운 객체의 __proto__ 는 새로운 객체를 만들게 해 준 원형의 프로토타입 객체를 참조한다.
  ( prototype chain 이 이 때문에 일어날 수 있다. )
  // 
  ```
* What do you think of AMD vs CommonJS?
  - 
* Explain why the following doesn't work as an IIFE(즉시실행함수표현 : Immediately Invoked Function Expression): `function foo(){ }();`.
  - function foo(){} 여기는 함수 선언이고 ()는 함수를 호출하려고 시도했지만 이름이 지정되지 않았기 때문에 `Uncaught SyntacError : Unexpected token)` 에러를 던집니다.
  - JavaScript 파서는 `function foo() {}와 () `로 읽는다.
  * What needs to be changed to properly make it an IIFE?
    - `f(function foo(){})()` or `(function foo(){}())` 입니다.
* What's the difference between a variable that is: `null`, `undefined` or undeclared?
  - `undeclared` : 선언되지 않은 변수는 변수에 값을 할당하기 전에 (var, let, const)를 사용하여 생성되지 않은 변수에 값을 할당할 때 생성된다. `use strict` 하면 ReferenceError 발생시킴
  - `undefined` : 변수는 선언되었지만 값이 할당되지 않은 변수, 자료형이 결정되지 않은 변수
  - `null` : 변수를 선언하고 null이라는 빈 값을 할당한 경우, 자료형은 객체인데 비어있는 변수
  - undefined == null --> true // == 비교연산자는 자료형이 다르면 자동 형변환으로 자료형을 강제로 맞춰서 비교하는 비교연산자이다. undefined와 null(object) 는 자료형이 다르니 자바스크립트 엔진이 알아서 통일해서 둘다 값이 없으니까 true를 반환한다. 이 경우 ===연산자(자료형까지 비교)를 사용해야 한다.
  * How would you go about checking for any of these states?
* What is a closure, and how/why would you use one?
  - 클로저는 외부함수의 변수와 매개변수에 접근 할 수 있는 내부함수를 말한다. 클로저는 함수와 그 함수가 선언된 렉시컬 환경의 조합이다. "렉시컬"은 렉시컬 범위 지정이 변수가 사용 가능한 위치를 결정하기 위해 소스 코드 내에서 변수가 선언된 위치를 사용한다는 사실을 나타낸다. 핵심 : 클로저는 외부 함수가 반환된 후에도 외부 함수의 변수 범위 체인에 접근 할 수 있는 내부함수이다.
  - 데이터를 private하게 사용하기 위해
* Can you describe the main difference between a `forEach` loop and a `.map()` loop and why you would pick one versus the other?
  - forEach : 배열의 요소를 반복한다, 각 요소에 대한 콜백을 실행한다, 값을 반환하지 않는다.
  - map : 배열의 요소를 반복한다, 각 요소에서 함수를 호출하여 결과로 새로운 배열을 작성하여 각 요소를 새 요소에 매핑한다.
  - 주된 차이점은 .map()이 새로운 배열을 반환한다는 것이다. 결과가 필요하지만 원본 배열을 변경하고 싶지 않으면 .map()이 확실한 선택이다. 단순히 배열을 반복할 필요가 있다면 forEach가 좋은 선택이다.
* What's a typical use case for anonymous functions?
  - IIFE로 사용되어 지역 범위 내에서 일부 코드를 캡슐화하므로 선언된 변수가 전역 범위로 노출되지 않는다.
  - 한번 사용되며 다른 곳에서는 사용할 필요가 없는 콜백으로 사용된다.
* How do you organize your code? (module pattern, classical inheritance?)
  (코드를 어떻게 구성합니까? 모듈 패턴? 코전적인 상속?)
* What's the difference between host objects and native objects?
  (호스트 객체와 내장 객체의 차이점은 무엇입니까?)
  - 내장 객체는 JavaScript 언어의 일부인 객체이다. (예 : String, Math, Object, FUnction 등)
  - 호스트 객체는 window, XMLHTTPRequest 등과 같이 런타임 환경(브라우저 또는 노드)에 의해 제공된다.
* Difference between: `function Person(){}`, `var person = Person()`, and `var person = new Person()`?
  - JavaScript의 생성자에 대해 묻는 질문이다.
  ```
  function Person(name) { // 함수 선언일 뿐이다.
    this.name = name
  }

  // 생성자가 아니며 Person을 함수로 호출한다.
  // 일반적으로 생성자는 아무것도 반환하지 않으므로 일반 함수처럼 생성자를 호출하면 undefined가 반환되고 지정된 변수에 할당된다.
  var person = Person('John')
  console.log(person) // undefined
  console.log(person.name) // Uncaught TypeError : 정의되지 않은 'name' 프로퍼티를 읽을 수 없다.

  // Person.prototype을 상속받은 new 연산자를 사용해서 Person 객체의 인스턴스를 생성한다.
  var person = new Person('John')
  console.log(person) // Person { name: "John" }
  console.log(person.name) // "john"
  ```
* What's the difference between `.call` and `.apply` and `.bind`?
[예제](http://www.kimsatgod.com/call-apply-bind-%EC%B0%A8%EC%9D%B4/)
  - 셋 다 Context를 조정하기 위한 함수이다.
  - 함수 안에서 this를 사용할 때 대체 this가 어디냐를 조정하는 것인데, 기본적으로 브라우저에서 this는 window 객체를 가리킨다.
  - 객체의 메서드는 해당 객체를 가리키게 된다. 하지만 객체의 메서드만 따로 변수로 참조하는 경우엔 이 Context가 window로 되어 버린다. 따라서 Context를 조정해야 하 일이 생긴다.
  ```
  // this부분에 객체를 넣어주면 그걸 가리키게된다. 특이사항은 일일이 콤마로 구분해서 넣어줘야 함
  func.call(this, arg1, arg2, ...argN);

  // call()과 기능은 같지만 파라미터를 배열로 넘겨준다는 특징이 있다.
  func.apply(this, arguments)
  ```
  - call(), apply() vs bind()
  - call(), apply()는 함수가 실행이 되고 bind()는 아니다. bind()는 새로운 함수 인스턴스를 생성된다, 즉 바로 호출하지 않고 context가 조정된 함수를 반환한다는 의미.

  ```
  // 새로운 함수 인스턴스를 생성한다는 말을 생각해보면
  function func() {
    console.log('this.name: ', this.name)
  }
  var a = { name: 'a' }
  var b = { name : 'b' }
  var c = { name: 'c' }

  var bind_a = func.bind(a);
  var bind_b = func.bind(b);
  var bind_c = func.bind(c);

  bind_a()
  bind_b()
  bind_c()

  // 출력 결과
  // this.name : a
  // this.name : b
  // this.name : c
  ```
  - 결론
    * 셋 다 컨텍스트를 조정한다.
    * call(), apply()는 바로 호출하고, bind()는 바로 호출하지 않는다.
    * call()은 파라미터를 콤마로 구분해서 일일이 넘겨준다.
    * apply()는 파라미터를 배열로 넘긴다.

* Explain `Function.prototype.bind`.
  - 다른 함수로 전달하고자 하는 클래스의 메소드에서 this의 값을 바인딩 할 때 가장 유용하다.
  - bind() 메소드는 호출될 때 this 키워드가 제공된 값으로 설정되고 새로운 함수가 호출될 때 주어진 인자 앞에 주어진 시퀀스가 새로운 함수를 생성한다.
* What's the difference between feature detection, feature inference, and using the UA string?
  - Feature Detection은 브라우저가 특정 코드 블록을 지원하는지에 따라 다른 코드를 실행하도록 하여, 일부 브라우젖에서 항상 오류가 발생하도록 한다.
  - Feature Inference 는 Feature Detection고 마찬가지로 기능을 확인하지만 다른 함수도 존재한다고 가정하고 사용한다.
* Explain Ajax in as much detail as possible.
  - Asynchronous Javascript And Xml(비동기 자바스크립트와 xml)의 약자입니다. JavaScript를 사용한 비동기 통신, 클라이언트와 서버간에 XML 데이터를 주고 받는 기술이라고 할 수 있다.
  - 비동기 방식이란 웹페이지를 리로드하지 않고 데이터를 불러오는 방식입니다. 장점은 페이지 리로드의 경우 전체 리소스를 닫시 불러와야 하는데 (이미지, 자바스크립트, 기타 코드 등) 모두 재요청할 경우 불필요한 리소스 낭비가 발생하게 되지만 비동기식 방식을 이용할 경우 필요한 부분만 불러와 사용할 수 있으므로 장점이 있다.
* What are the advantages and disadvantages of using Ajax?
  - 장점
    * 웹페이지의 속도향상
    * 서버의 처리가 완료 될때까지 기다리지 않고 처리 가능하다.
    * 서버에서 Data만 전송 하면 되므로 전체적인 코딩의 양이 줄어든다.
    * 기존 웹에서는 불가능했던 다양한 UI를 가능하게 해준다.
  - 단점
    * 히스토리 관리가 안된다.
    * 연속적으로 데이터를 요청하면 서버 부하가 증가할 수 있다.
    * XMLHttpRequest를 통해 통신을 하는 경우 사용자에게 아무런 진행 정보가 주어지지 않는다. 그래서 아직 요청이 완료되지 않았는데 사용자가 페이지를 떠나거나 오작동할 우려가 발생하게 된다.
* Explain how JSONP works (and how it's not really Ajax).
  - JSON with Padding은 현재 페이지에서 cross-oprigin 도메인으로의 Ajax 요청이 허용되지 않기 때문에 웹브라우저에서 cross-domain정책을 우회하는데 사용되는 방법이다.
* Have you ever used JavaScript templating?
  * If so, what libraries have you used?
  - Lodash를 사용해봤습니다.
* Explain "hoisting". (hoist : 끌어올린다.)
  - 호이스팅은 코드에서 변수 선언의 동작을 설명하는데 사용된다. `var` 키워드로 선언 혹은 초기화된 변수는 현재 스코프의 최상위까지 `호이스팅` 됩니다. 그러나 선언문만 호이스팅 되며 할당은 그대로다. 아래 예제.
  ```
  // var 선언이 호이스팅된다.
  console.log(foo) // undefined
  var foo = 1
  console.log(foo) // 1

  // let/const 선언은 호이스팅이 안된다.
  console.log(bar) // ReferenceError : bar는 정의되지 않았습니다.
  let bar = 2
  console.log(bar) // 2
  ```
  - 함수 선언은 바디를 호이스팅되는 반면 변수 선언 형태로 작성된 함수 표현식은 변수 선언만 호이스팅 된다.
  ```
  // 함수 선언
  console.log(foo) // [Function: foo]
  foo() // 'FOOOOOO'
  function foo() {
    console.log('FOOOO)
  }
  console.log(foo) // [Function: foo]

  // 함수 표현
  console.log(bar) //undefined
  bar() // Uncaught TypeError : bar는 함수가 아니다.
  var bar = function() {
    console.log('BARRRR')
  }
  console.log(bar) // [Function: bar]
  ```
* Describe event bubbling.
  - DOM 요소에서 이벤트가 트리거되면 리스너가 연결되어 있는 경우 이벤트 처리를 시도한 다음 해당 이벤트가 부모에게 버블링되고 같은 이벤트가 발생한다. 이 버블링은 요소의 조상 `document` 까지 계속적으로 발생시킵니다.
* Describe event capturing.
  - event bubbling과 반대. 하위로 이벤트 전파
* What's the difference between an "attribute" and a "property"?
  - `attribute`는 HTML마크업에 정의되지만 `property`는 DOM에 정의된다.
  `<input type="text" value="Hello">`
  ```
  const input = document.querySelector('input')
  console.log(input.getAttribute('value)) //Hello
  console.log(input.value) // Hello

  // 텍스트 필드에 'World"를 추가하면 아래와 같다.
  console.log(input.getAttribute('value')) // Hello
  console.log(input.value) // Hello World
  ```
* Why is extending built-in JavaScript objects not a good idea?
* Difference between window load event and document DOMContentLoaded event?
* What is the difference between `==` and `===`?
* Explain the same-origin policy with regards to JavaScript.
* Make this work:
```javascript
duplicate([1,2,3,4,5]); // [1,2,3,4,5,1,2,3,4,5]
```
* Why is it called a Ternary operator, what does the word "Ternary" indicate?
* What is `"use strict";`? what are the advantages and disadvantages to using it?
* Create a for loop that iterates up to `100` while outputting **"fizz"** at multiples of `3`, **"buzz"** at multiples of `5` and **"fizzbuzz"** at multiples of `3` and `5`
* Why is it, in general, a good idea to leave the global scope of a website as-is and never touch it?
* Why would you use something like the `load` event? Does this event have disadvantages? Do you know any alternatives, and why would you use those?
* Explain what a single page app is and how to make one SEO-friendly.
* What is the extent of your experience with Promises and/or their polyfills?
* What are the pros and cons of using Promises instead of callbacks?
* What are some of the advantages/disadvantages of writing JavaScript code in a language that compiles to JavaScript?
* What tools and techniques do you use debugging JavaScript code?
* What language constructions do you use for iterating over object properties and array items?
* Explain the difference between mutable and immutable objects.
  * What is an example of an immutable object in JavaScript?
  * What are the pros and cons of immutability?
  * How can you achieve immutability in your own code?
* Explain the difference between synchronous and asynchronous functions.
* What is event loop?
  * What is the difference between call stack and task queue?
  - 이벤트 루프는 콜 스택을 모니터하고 태스크 큐에서 수행할 작업이 있는지 확인하는 단일 스레드 루프다.
    콜 스택이 비어 있고 태스크 큐에 콜백 함수가 있는 경우, 함수는 큐에서 제외되고 실행될 콜 스택으로 푸시된다.
* Explain the differences on the usage of `foo` between `function foo() {}` and `var foo = function() {}`
* What are the differences between variables created using `let`, `var` or `const`?
* What are the differences between ES6 class and ES5 function constructors?
* Can you offer a use case for the new arrow `=>` function syntax? How does this new syntax differ from other functions?
[예제](https://hanjungv.github.io/2018-02-03-1_JS_arrow_function/)
* What advantage is there for using the arrow syntax for a method in a constructor?
* What is the definition of a higher-order function?
* Can you give an example for destructuring an object or an array?
* ES6 Template Literals offer a lot of flexibility in generating strings, can you give an example?
* Can you give an example of a curry function and why this syntax offers an advantage?
* What are the benefits of using `spread syntax` and how is it different from `rest syntax`?
* How can you share code between files?
* Why you might want to create static class members?
