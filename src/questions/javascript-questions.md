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
  - 내장 JavaScript 객체를 확장한다는 것은 prototype에 속성/함수를 추가한다는 것을 의미합니다. 이것은 처음에는 좋은 생각처럼 보일 수 있지만 실제로는 위험하다. 여러분의 코드가 동일한 contains 메소드를 추가함으로써 Array.prototype 을 확장하는 여러가지 라이브러리를 사용한다고 상상해본다. 이러한 구현은 메소드를 서로 덮어쓰게 되며 이 두 메소드의 동작이 동일하지 않으면 코드가 망가질 것이다. 네이티브 객체를 확장할 수 있는 유일한 경우는 폴리필을 만들려고 할 떄이다. JavaSCript 사양의 일부이지만 오래된 브라우저이기 때문에 사용자 브라우저에 없을 수도 있는 메서드에 대한 고유한 구현을 제공해야 할 경우이다.
* Difference between window load event and document DOMContentLoaded event?
  - DOMContentLoaded 이벤트는 스타일시트, 이미지, 서브프레임이 로딩을 기다리지 않고 초기 HTML 문서가 완전히 로드되고 파싱될 때 발생한다.
  - window의 load 이벤트는 DOM과 모든 종속 리소스와 에셋들이 로드된 후에만 발생한다.
* What is the difference between `==` and `===`?
  - == 는 추상 동등 연산자이고 === 는 완전 동등 연산자이다. == 연산자는 타입 변환이 필요한 경우 타입 변환을 한 후에 동등한지 비교할 것이다. === 연산자는 타입 변환을 하지 않으므로 두 값이 같은 타입이 아닌 경우 ===는 단순히 false를 반환한다 (=== 는 타입 체크까지 해준다)
* Explain the same-origin policy with regards to JavaScript.
  - JavaScript 가 도메인 경계를 넘어서 요청하는 것을 방지한다. origin은 URI 체계, 호스트 이름 및 포트 번호의 조합으로 정의된다. 이 정책은 한 페이지의 악의적인 스크립트가 해당 페이지의 문서 객체 모델을 통해 다른 웹 페이지의 중요한 데이터에 접근하는 것을 방지한다.
* Make this work:
```javascript
duplicate([1,2,3,4,5]); // [1,2,3,4,5,1,2,3,4,5]
```
```
  function duplicate(arr) {
    return arr.concat(arr)
  }
  duplicate([1, 2, 3, 4, 5])
```
* Why is it called a Ternary operator, what does the word "Ternary" indicate?
  - 삼항을 나타내고 삼항 표현식은 세각지 피연산자, 테스트 조건문, "then" 표현석, "else" 표현식을 받는다.
* What is `"use strict";`? what are the advantages and disadvantages to using it?
  - 전체 스크립트나 개별 함수에 엄격 모드를 사용하는데 사용되는 명령문이다. Strict 모드는 JavaScript 제한된 번형에서 선택하는 방법이다.
  - 장점
    * 실수로 전역변수를 만드는 것이 불가능하다.
    * 암묵적으로 실패한 예외를 throw 하지 못하는 할당을 만든다.
    * 삭제할 수 없는 속성을 삭제하려고 시도한다
    * 함수의 매개변수 이름은 고유해야 한다
    * this는 전역 컨텍스트에서 undefined이다.
    * 예외를 발생시키는 몇 가지 일반적인 코딩을 잡아낸다
    * 헷갈리거나 잘 모르는 기능을 사용할 수 없게 한다.
  - 단점
    * 일부 개발자는 익숙하지 않은 기능이 많다
    * `functon.caller`와 `function.arguments` 에 더 이상 접근 할 수 없다
    * 서로 다른 엄격한 모드로 작성된 스크립트를 병합하면 문제가 발생할 수 있다.
* Create a for loop that iterates up to `100` while outputting **"fizz"** at multiples of `3`, **"buzz"** at multiples of `5` and **"fizzbuzz"** at multiples of `3` and `5`
* Why is it, in general, a good idea to leave the global scope of a website as-is and never touch it?
  ```
  for (let i = 1; i<=30; i++) {
    var f = i % 3 == 0, b = i % 5 == 0
    console.log( f ? b? 'FIZZBUZZ' :  'Fizz' : b ? 'Buzz' : i)
  }
  ```
  - 모든 스크립트는 전역 스코프에 접근할 수 있으며 모든 사람이 전역 네임스페이스를 사용하여 변수를 정의하면 충돌이 발생할 수 있다. 모듈 패턴(IIFEs)을 사용하여 변수를 로컬 네임페이스 내에 캡슐화해야한다.
* Why would you use something like the `load` event? Does this event have disadvantages? Do you know any alternatives, and why would you use those?
  - load 이벤트는 문서로딩 프로세스가 끝날 때 발생된다. 이 시점에서 문서의 모든 객체가 DOM에 있고, 모든 이미지, 스크립트, 링크 및 하위 프레임로딩이 완료된다. DOM 이벤트 DomContentLoaded는 페이지의 DOM이 생성된 후에 발생하지만 다른 리소스가 로딩되기를 기다리지 않습니다. 이것은 초기화되기 전까지 전체 페이지가 로드될 필요가 없는 경우에 선호된다.
* Explain what a single page app is and how to make one SEO-friendly.
  - SPA 장점
    * 전체 페이지 새로고침으로 인해 페이지 탐색 사이에 하얀 화면이 보이지 않아 앱이 더 반응적으로 느껴진다.
    * 동일한 애셋을 페이지 로드마다 다시 다운로드 할 필요가 없어서 서버에 대한 HTTP 요청이 줄어든다.
    * 클라이언트와 서버 사이의 고려해야 할 부분을 명확하게 구분한다.
  - SPA 단점
    * 여러 페이지에 필요한 프레임워크, 앱 코드, 애셋로드로 인해 초기 페이지로드가 무거워진다.
    * 모든 요청을 단일 진입점으로 라우트하고 클라이언트 측 라우팅이 한 곳에 인계받을 수 있도록 서버를 구성하는 추가 단계가 수행되어진다.
    * SPA는 콘텐츠를 렌더링하기 위해 JavaSCript에 의존하지만 모든 검색 엔진이 크롤링 중에 JavaScript를 실행하지는 않으며 페이지에 빈 콘텐츠가 표시될 수 있다. 
* What is the extent of your experience with Promises and/or their polyfills?(Promise, Polyfill 에 대한 당신의 경험도는 어느 정도 인가?)
  - Promise는 어느 시점에 resolve된 값 또는 resolve 되지 않은 이유 중 하나의 값을 생성할 수 있는 객체이다. promise는 fulfilled, rejected, pending 3가지 상태 중 하나일수 있다. promise 사용자는 콜백을 붙여서 fulfill된 값이나 reject된 이유를 처리할 수 있다.
  - ES6는 즉시 사용할 수 있는 Promise를 지원하며 일반적으로 요즘 polyfill은 필요 없다.
* What are the pros and cons of using Promises instead of callbacks?(Callback 대신에 Promise를 사용할 때의 장점과 단점은 무엇입니까?)
  - 장점
    * 이해하기 어려운 콜백 지옥을 피할 수 있다.
    * 읽기 쉬운 .then()을 이용하여 연속적인 비동기 코드를 쉽게 작성할 수 있다.
    * Promise.all()을 사용하여 병렬 비동기 코드를 쉽게 작성 할 수 있다.
  - 단점
    * 약간 더 복잡한 소스코드
    * ES6을 지원하지 않는 이전 브라우저에서 이를 사용하기 위해서는 polyfill을 로드해야 한다.(폴리필은 개발자가 특정 기능이 지원되지 않는 브라우저를 위해 사용할수 있는 플러그인)
* async/await가 promise를 사라지게 만들수 있는 이유
  - 간결함과 깔끔함
  - 에러 핸들링 (try/catch)
  - 분기
  - 중간값
  - 디버깅이 쉬워진다.
[예제](https://medium.com/@constell99/%EC%9E%90%EB%B0%94%EC%8A%A4%ED%81%AC%EB%A6%BD%ED%8A%B8%EC%9D%98-async-await-%EA%B0%80-promises%EB%A5%BC-%EC%82%AC%EB%9D%BC%EC%A7%80%EA%B2%8C-%EB%A7%8C%EB%93%A4-%EC%88%98-%EC%9E%88%EB%8A%94-6%EA%B0%80%EC%A7%80-%EC%9D%B4%EC%9C%A0-c5fe0add656c)
* What are some of the advantages/disadvantages of writing JavaScript code in a language that compiles to JavaScript?
* What tools and techniques do you use debugging JavaScript code?(JavaScript 코드를 디버깅 하기 위해 어떤 도구와 기술을 사용합니까?)
  - Vue ( vuex DevTools)
  - JavaScript : Chrome Devtools, debugger statement, console.log
* What language constructions do you use for iterating over object properties and array items?(오브젝트 속성 및 배열 항목을 반복할 때 사용하는 언어 구조는 무엇입니까?)
  - 오브젝트 경우
    * for  반복문 : 사용하기 전에 hasOwnProperty(property) 체크 추가
    * Object.keys() : 전달하는 객체의 열거 가능한 모든 속성을 나열하는 메소드
    * Object.getOwnPropertyNames() : 전달하는 객체의 열거 가능한 속성과 열거되지 않는 모든 속성을 나열하는 메소드
  - 배열 경우
    * for 반복문 :
    * forEach : 필요한 모든 것이 배열 요소라면 index를 사용할 필요가 없기 때문에 이 구조가 더 필요할 수 있다. 
  - 대부분의 경우 .forEach메서드를 선호하지만 무엇을 하느냐에 따라서 각 상황에 맞게 사용하는 것이 좋다. for 루프는 break를 사용하여 루프를 조기에 종료하거ㅏㄴ 루프 당 두 번 이상 반복자를 증가시키는 것과 같이 더 많은 유연성을 허용한다.
* Explain the difference between mutable and immutable objects.
  * What is an example of an immutable object in JavaScript?
  * What are the pros and cons of immutability?
    - 장점 : 변경점 찾기 및 디버깅이 쉬움
    - 단점 : mutable한 코드보다 훨씬 느림
  * How can you achieve immutability in your own code?
  - Immutability는 객체가 생성된 이후 그 상태를 변경할 수 없는 디자인 패턴을 말한다.
  - 객체는 참조 형태로 전달하고 전달 받는다. 객체가 참조를 통해 공유되어 있다면 그 상태가 언제든지 변경될 수 있기 때문에 문제가 될 가능성도 커지게 된다. 이는 객체의 참조를 가지고 있는 어떤 장소에서 객체를 변경하면 참조를 공유하는 모든 장소에서 그 영향을 받기 때문인데 이것이 의도한 동작이 아니라면 참조를 가지고 있는 다른 장소에 변경 사실을 통지하고 대처해야 한다.
  - 의도하지 않은 객체의 변경이 발생하는 원인의 대다수는 "레퍼런스를 참조한 다른 객체에서 객체를 변경"하기 때문이다. 이 문제의 해결 방법은 객체를 불변객체로 만들어 프로퍼티의 변경을 방지하며 객체의 변경이 필요한 경우에는 참조가 아닌 객체의 방어적 복사를 통해 새로운 객체를 생성한 후 변경한다. 
* Explain the difference between synchronous and asynchronous functions.
  (동기 및 비동기 함수의 차이점을 설명하십시오)
  - 동기 함수에서는 다음 명령문이 실행되기 전에 명령문이 완료됩니다. 이 경우 프로그램은 명령문의 순서대로 정확하게 평가되고 명령문 중 하나가 매우 오랜 시간이 걸리면 프로그램 실행이 일시중지됩니다.
  - 비동기 함수는 일반적으로 파라미터를 통해서 콜백을 받아들이고, 비동기 기능은 일반적으로 매개변수로 콜백을 허용하며 비동기 기능이 호출된 후 즉시 다음 줄에서 실행이 계속 된다. 
* What is event loop?
  * What is the difference between call stack and task queue?
  - 이벤트 루프는 콜 스택을 모니터하고 태스크 큐에서 수행할 작업이 있는지 확인하는 단일 스레드 루프다.
    콜 스택이 비어 있고 태스크 큐에 콜백 함수가 있는 경우, 함수는 큐에서 제외되고 실행될 콜 스택으로 푸시된다.
* Explain the differences on the usage of `foo` between `function foo() {}` and `var foo = function() {}`
  - 전자는 함수 선언, 후자는 함수 표현. 주요한 차이점은 함수 선언은 몸체가 호이스트 되지만 함수 표현의 몸체는 호이스트가 되지 않는다.(변수와 동일한 호이스팅 동작을 가짐) , 함수 표현식을 정의하기 전에 호출하려고 하면 `Uncaught TypeError : XXX is not function` 오류 발생한다.
  - 함수 선언
  ```
  foo()
  function foo() {
    console.log('FPPPP')
  }
  ```
  - 함수 표현
  ```
  foo() // Uncaught TypeError: foo는 함수가 아니다.
  var foo = function() {
    console.log('FOPP')
  }
  ```
* What are the differences between variables created using `let`, `var` or `const`?
  - var 키워드를 사용하여 선언된 변수는 함수가 생성된 함수나 함수 밖에서 생성된 함수에 전역 오브젝트로 적용된다. let과 const는 블록 범위이다. 즉 가장 가까운 중괄호 내에서만 접근 가능하다.
  - var 은 변수 호이스팅이 가능하다. 즉, 변수가 선언되기 전에 코드에서 참조될 수 있습니다. let 과 const는 변수 호이스팅이 안되고 에러를 던진다.
  - var을 사용하여 변수를 다시 선언해도 오류는 발생하지 않지만 let과 const는 오류를 발생한다.
  - let은 변수의 값을 재할당 할 수 있지만, const는 재할당 할 수 없다
* What are the differences between ES6 class and ES5 function constructors?
  ```
  // ES5 함수 생성자
  function Person(name) {
    this.name = name
  }

  // ES6 클래스
  class Person {
    constructor(name) {
      this.name = name
    }
  }
  ```
  생성자의 주요 차이점은 상속을 할 때 발생한다.
  ```
  // ES5 함수 생성자
  function Student(name, studentId) {
    // 수퍼 클래스의 생성자를 호출하여 수퍼 클래스에 상속된 멤버를 초기화한다.
    Person.call(this, name)

    // 서브 클래스의 멤버를 초기화한다
    this.studentId = studentId
  }

  Student.prototype = Object.create(Person.prototype)
  Student.prototype.contstructor = Student

  // ES6 클래스
  Class Student extends Person {
    constructor(name, studentId) {
      super(name)
      this.studentId = studentId
    }
  }
  ```
* Can you offer a use case for the new arrow `=>` function syntax? How does this new syntax differ from other functions?
  - arrow function의 장점
    * 짧은 함수를 작성할 수 있게 된다.
    * 기존 자바스크립트에서 this는 dynamic scoping이 되었는데 이 경우 lexical scoping을 사용하게 된다. 고로 따로 binding을 사용하지 않아도 된다. 정리하면 `자신만의 this를 생성하지 않고 자신을 포함하고 있는 context의 this를 이어 받는다.`
  - lexical scope란?
    * 렉시컬 스코프란 `소스코드가 작성된 그 문맥`에 결정된다고 합니다.
[예제](https://hanjungv.github.io/2018-02-03-1_JS_arrow_function/)
* What advantage is there for using the arrow syntax for a method in a constructor?
* What is the definition of a higher-order function?(고차함수의 정의는 무엇인가?)
  - 고차 함수는 다른 함수를 매개 변수로 사용하여 일부 데이터에서 작동하거나 결과로 함수를 반환하는 함수이다.
  - 전형적인 예로는 배열과 함수를 인수로 취하는 map이다. map 은 고차 함수를 사용하여 배열의 각 항목을 변환하고 변환 된 데이터를 새로운 배열로 반환한다.
* Can you give an example for destructuring an object or an array?
  - 디스트럭쳐링은 ES6에서 사용할 수 있는 표현식으로 객체 또는 배열의 값을 추출하여 다른 변수에 배치하는 간결하고 편리한 방법을 제공한다.
  배열 디스트럭쳐링
  ```
  // 변수 할당
  const foo = ['one', 'two', 'three']
  const [one, two, three] = foo;

  console.log(one) // "one"
  console.log(two) // "two"
  console.log(three) // "three"

  // 변수 교환
  let a = 1
  let b = 3

  [a, b] = [b, a]
  console.log(a) // 3
  console.log(b) // 1
  ```
  객체 디스트럭쳐링
  ```
  const o = { p: 42, q: true }
  const { p, q } = o;

  console.log(p) // 42
  console.log(q) // true
  ```
* ES6 Template Literals offer a lot of flexibility in generating strings, can you give an example?
  - 백틱 사용(`)
  - 백틱을 사용하고 그 안에 변수들은 ${}로 감싸주면 자바스크립트 엔진이 알아서 합쳐준다.
* Can you give an example of a curry function and why this syntax offers an advantage?
  - curry : 함수와 인자를 다루는 기법이다.
  - 커링은 함수 하나가 n개의 인자를 받는 과정을 n개의 함수로 각각의 인자를 받도록 하는 것이다. 
  - 부분적으로 적용된 함수를 체인으로 계속 생성해 결과적으로 값을 처리한다. 
  - 필요한 인자를 모두 채울때까지 인자를 적용해 나가다가 모든 인자의 개수가 채워지면 함수의 본체를 실행하는 기법이다.
  ```
  function _curry(fn) {
    return function(a, b) {
      return arguments.length === 2 ? fn(a, b) : function(b) { return fn(a, b);};
    }
  }

  var add = _curry(function(a, b) {
    return a + b;
  });

  var add10 = add(10);
  console.log( add10(5) );
  console.log( add(5)(3) );
  console.log( add(10, 2) );
  ```
  - 결국은 본체 함수인 _curry 안의 인자인 함수를 값으로 들고 있다가 원하는 시점까지 미뤄뒀다가 최종적으로 평가하는 기법이다. 함수가 함수를 대신 실행하거나 함수가 함수를 리턴하는 방식이 함수형 프로그래밍이다.
* What are the benefits of using `spread syntax` and how is it different from `rest syntax`?
  - spread syntax
    * 확산 문법이란 es6에서 추가된 문법으로 ...를 사용해서 배열의 나머지 값들을 받아오거나 편하게 화장시킬 수도 있다.
    ```
    function spreadArray(arr) {
      return [...arr, 'dookie']
    }
    var result = spreadArray(['I', 'really'])  // ['I', 'really', 'dookie']

    var person = {
      name: 'Todd',
      age: 29
    }

    var copyOfTodd = {...person}
    ```
  - rest syntax
    * 나머지 구문은 2개 이상의 요소를 하나의 요소로 모읍니다.
* How can you share code between files? (파일간에 코드를 공유하려면 어떻게 해야 하는가?)
  - JavaScript 환경에 따라 다르다.
  - 클라이언트(브라우저 환경)에서는 변수/함수가 전역범위(`window`)에 선언되어있는 한 모든 스크립트가 이를 참조할 수 있습니다. 서버(Node.js)에서 일반적인 방법은 CommonJS를 사용하는 것입니다. 각 파일은 모듈로 취급되며 변수와 함수를 `module.exports` 객체에 첨부하여 내보낼 수 있다.
* Why you might want to create static class members?
  - 정적 클래스 멤버는 클래스의 특정 인스턴스에 연결되지 않으며 어떤 인스턴스가 이를 참조하는지에 관계없이 동일한 값을 가진다. 정적 속성은 일반적으로 구성 변수이며 정적 메서드는 일반적으로 인스턴스의 상태에 의존하지 않는 순수 유틸리티 함수이다.
