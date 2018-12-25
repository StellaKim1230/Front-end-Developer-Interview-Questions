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
  // 생성된 객체를 이용하여 프로토타입 객체의 멤버를 수정하면 프로토타입 객체에 있는 멤버를 수정하는 것이 아니라 자신의 객체에 멤버를 추가하는 것이다. joon 객체를 사용하여 getType()을 호출하면 프로토타입 객체의 getType()을 호출한 것이 아니다. joon 객체에 추가된 getType()을 호출한 것이다. 즉, 사용된 객체의 원형인 프로토타입 객체의 멤버를 수정할 경우는 멤버 추가와 같이 함수의 prototype 속성을 이용하여 수정한다.

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
  결론 : 프로토타입 객체는 정의된 함수의 새로운 객체가 생성되기 위한 원형이 되는 객체입니다. 같은 원형으로 생성된 객체가 공통으로 참조하는 공간이다. 프로토타입 객체의 멤버를 추가, 수정, 삭제는 함수의 prototype 속성을 통해 접근해야 한다.

  프로토타입이란? : JavaScript 에서는 기본 데이터 타입을 제외한 모든 것이 객체다. 객체가 만들어지기 위해서는 자신을 만드는데 사용된 원형의 프로토타입 객체를 이용하여 객체를 만든다. 이때 만들어진 객체 안에 __proto__ 속성이 자신을 만들어낸 원형을 의미하는 프로토타입 객체를 참조하는 숨겨진 링크가 있다. 이 숨겨진 링크를 프로토타입이라고 정의한다.
  ```
* Explain how prototypal inheritance works (Explain Prototype Chain 같이 설명)
  ```
  function Person1() {}
  Person1.prototype.getName = function() { return 'kim' }
  const f1 = new Person1()
  fi.getName()  // kim

  class Human extends Person1{}
  Human.prototype.getType = function() { return 'human' } // Human의 prototype속성을 통해 getType이라는 함수를 만들었다. Human을 원형으로 생성된 객체들이 getType을 참조 할 수 있다.

  const h1 = new Human
  h1.getName() // kim
  // kim이 출력되는 이유 : h1은 Human의 객체이고, h1를 만들게 해 준 원형 객체의 프로토타입을 참조한다. Human의 getName()이 없으면, 상속받은 Person 프로토타입 객체에서 getName을 찾는다. (이때 kim이 출력)
  만약 Person 프로토타입 객체에도 없다면 Person 이 상속받고 있는 Object 객체의 프로토타입에서 찾는데 여기서도 없으면 undefined를 출력한다. (prototype chain)
  h1.getType() // human
  // Human 프로토타입 객체에 getType함수를 생성했기 때문에 Person까지 찾지 않고 Human에서 찾은 human을 리턴시킨다.

  const h2 = new Human
  h2.getName = function() { return 'han' }
  h2.getName() // han : 바로 위에서 h2객체 자신에 getName 함수를 만들었다. getName을 찾았고, 바로 han으로 리턴됨.
  h1.getName() // kim
  h2.getType() // human

  ---> 함수를 정의하면 constructor, __proto__를 갖는 프로토타입 객체가 생성되고, 이 함수의 새로운 객체를 만들면 그 새로운 객체는 __proto__라는 속성을 갖는다. 이 새로운 객체의 __proto__ 는 새로운 객체를 만들게 해 준 원형의 프로토타입 객체를 참조한다. ( prototype chain 이 이 때문에 일어날 수 있다. )
  // 
  ```
* What do you think of AMD vs CommonJS?
* Explain why the following doesn't work as an IIFE(즉시실행함수표현 : Immediately Invoked Function Expression): `function foo(){ }();`.
  * What needs to be changed to properly make it an IIFE?
* What's the difference between a variable that is: `null`, `undefined` or undeclared?
  * How would you go about checking for any of these states?
* What is a closure, and how/why would you use one?
* Can you describe the main difference between a `forEach` loop and a `.map()` loop and why you would pick one versus the other?
* What's a typical use case for anonymous functions?
* How do you organize your code? (module pattern, classical inheritance?)
* What's the difference between host objects and native objects?
* Difference between: `function Person(){}`, `var person = Person()`, and `var person = new Person()`?
* What's the difference between `.call` and `.apply`?
* Explain `Function.prototype.bind`.
* What's the difference between feature detection, feature inference, and using the UA string?
* Explain Ajax in as much detail as possible.
* What are the advantages and disadvantages of using Ajax?
* Explain how JSONP works (and how it's not really Ajax).
* Have you ever used JavaScript templating?
  * If so, what libraries have you used?
* Explain "hoisting".
* Describe event bubbling.
* Describe event capturing.
* What's the difference between an "attribute" and a "property"?
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
* Explain the differences on the usage of `foo` between `function foo() {}` and `var foo = function() {}`
* What are the differences between variables created using `let`, `var` or `const`?
* What are the differences between ES6 class and ES5 function constructors?
* Can you offer a use case for the new arrow `=>` function syntax? How does this new syntax differ from other functions?
* What advantage is there for using the arrow syntax for a method in a constructor?
* What is the definition of a higher-order function?
* Can you give an example for destructuring an object or an array?
* ES6 Template Literals offer a lot of flexibility in generating strings, can you give an example?
* Can you give an example of a curry function and why this syntax offers an advantage?
* What are the benefits of using `spread syntax` and how is it different from `rest syntax`?
* How can you share code between files?
* Why you might want to create static class members?
