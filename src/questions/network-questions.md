---
title: Network Questions
layout: layouts/page.njk
permalink: /questions/network-questions/index.html
---

* Traditionally, why has it been better to serve site assets from multiple domains?
* Do your best to describe the process from the time you type in a website's URL to it finishing loading on your screen.
* What are the differences between Long-Polling, Websockets and Server-Sent Events?
* Explain the following request and response headers:
  * Diff. between Expires, Date, Age and If-Modified-...
  * Do Not Track
  * Cache-Control
  * Transfer-Encoding
  * ETag
  * X-Frame-Options
* What are HTTP methods? List all HTTP methods that you know, and explain them.
* uri, url 차이
  - URI : Uniform Resource Identifier
  - URL : Uniform Resource Locator
  - URI는 네트워크 상에서 자원이 어디 있는지 알려주기 위한 규약, 자원을 식별할 수 있는 문자열 정도로 생각한다.
  - 예를 들어 `http://ko.wigipedia.org/`라는 주소는 요 주소라는 서버를 나타내기 때문에 URL 이면서 URI 이다.
  - 또 다른 예로 `https://www.google.co.kr/search?q=uri`같은 주소가 있다고 하자. search 까지가 URL 이고, 내가 원하는 정보를 얻기 위해서 q=uri 라는 식별자가 필요하므로 q=uri까지는 URI이지만 URL은 아니다.
* rest, rest api 란? ([https://gmlwjd9405.github.io/2018/09/21/rest-and-restful.html](https://gmlwjd9405.github.io/2018/09/21/rest-and-restful.html))
  - Rest란 웹에 존재하는 모든 자원(이미지, 동영상  DB자원)에 고유한 URI를 부여해 활용 하는 것으로 자원을 정의하고 자원에 대한 주소를 지정하는 방법론
  - Restful API는 REST 특징을 지키면서 API를 제공한다.
* rest api 장단점
  - 장점 : 쉬운 사용 ( rest api 메시지를 읽는것만으로도 메시지가 의도하는 바를 명확하게 파악할 수 있다.), 해당 uri와 원하는 메소드 자체만 독립적으로 이해하면 된다. 클라이언트와 서버의 역할이 명확하게 분리된다. 헤더 부분에 uri 처리 메소드를 명시함으로써, 필요한 실제 데이터를 페이로드에 표현할 수 있도록 구성할 수 있는 기능을 제공한다.
  - 장점2 : http 프로토콜의 인프라를 그대로 사용하기 때문에 rest api 사용을 위한 별도의 인프라를 구축할 필요가 없다.
  - 단점 : 메소드 형태가 제한적이다 (4가지). 표준이 존재하지 않는다. 관리의 어려움과 좋은 api 디자인 가이드가 존재하지 않고, 많은 사람들이 하나씩 쌓아 올리고 구성된다.
* HTTP method 란 클라이언트와 서버 사이에 이루어지는 요청과 응답 데이터를 전송하는 방식
* options는 웹서버가 지원되는 메소드의 종류만 확인할 경우 사용하는지? 또 다른 이유는?
* cors :
  - Cross Origin Resource Sharing의 약자로 도메인 또는 포트가 다른 서버의 자원을 요청하는 메커니즘을 말한다. 이때 요청을 할 때는 cross-origin HTTP에 의해 요청됩니다. 하지만 동일 출처 정책(same-origin-policy) 때문에 CORS 같은 상황이 발생하면 외부서버에 요청한 데이터를 브라우저에서 보안목적으로 차단한다.
  - 웹 브라우저에서 외부 도메인 서버와 통신하기 위한 방식을 표준화한 스펙이다. 서버와 클라이언트가 정해진 헤더를 통해 서로 요청이나 응답에 반응할지 결정하는 방식으로 교차 출처 자원 공유라는 이름으로 표준화가 되었다. 요청을 받은 웹서버가 허용 할 경우에는 다른 도메인의 웹페이지 스크립트에서도 자원을 주고 받을 수 있게 해준다.
* same-origin-policy
  - 이 정책에 의해서 자바스크립트(XMLHttpRequest)로 다른 웹페이지에 접근할떄는 같은 출처(same origin)의 페이지에만 접근이 가능하다. 같은 출처라는 것은 프로토콜, 호스트명, 포트가 같다는 것을 의미한다. 즉 쉽게 말하면 웹페이지의 스크립트는 그 페이지와 같은 서버에 있는 주소로만 ajax 요청을 할 수 있다는 것이다.  요즘은 REST API 등을 이용한 외부 호출이 많아지는 상황에서는 정책이 CORS 이다. 이 정책의 특징은 서버에서 외부 요청을 허용할 경우 ajax 요청이 가능해지는 방식이다.
