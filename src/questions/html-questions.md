---
title: HTML Questions
layout: layouts/page.njk
permalink: /questions/html-questions/index.html
---

* What does a `doctype` do?
  - (Document Type) 문서 형식은 HTML 버전과 종류를 명시함으로써, 브라우저가 문서를 해석하고 출력하는데 직접적인 영향을 준다.
* How do you serve a page with content in multiple languages? (여러 언어로 되어 있는 콘텐츠의 페이지를 어떻게 제공하나요?)
  - HTTP를 서버에 요청하면 대개 요청하는 사용자 에이전트가 `Accept-Language` 헤더와 같은 언어 기본 설정에 대한 정보를 보낸다. 그런 다음 서버는 이 정보를 사용하여 해당 언어가 사용 가능한 경우 해당 언어로 된 문서 버전을 반환 할 수 있다. 반환된 HTML 문서는 `<html lang="en">...</html>` 같이 `<html>` 태그에 `lang` 속성을 선언해야 한다.
* What kind of things must you be wary of when design or developing for multilingual sites?(다국어 사이트를 디자인하거나 개발할 때 주의해야 할 사항은 무엇인가?)
  - HTML에서 `lang` 속성을 사용한다.
  - 사용자를 모국어로 안내한다.
  - 일부 언어는 다른 언어로 작성될 때 길어질 수도 있어서 디자인을 꺨 수 있는 디자인은 안 하는것이 좋다.
  - 날짜 및 통화 서식 : 나라마다 다른 방식으로 제시된다.
  - 번역된 문자열은 연결하지 않는다. `"오늘의 날짜는 " + date + "입니다" ` 단어의 순서가 다른 언어로 인해 꺠지게 된다.
  - 언어를 읽는 방향 주의
* What are `data-` attributes good for?
  - 요즘엔 권장하지 않는다. 이유는 사용자가 브라우저의 검사 요소를 사용하여 데이터 속성을 쉽게 수정 가능하다.
* Consider HTML5 as an open web platform. What are the building blocks of HTML5?
  - 콘텐츠를 보다 더 정확하게 설명 가능하다.
  - 새롭고 혁신적인 방법으로 서버와 통신 가능하다 ( 웹소켄 ??)
  - storage(오프라인 저장소) - 웹 페이지가 데이터를 클라이언트 측에 로컬로 저장하여 오프라인에서보다 효율적으로 작동하도록 하용한다.
  - 멀티미디어 : 개방형 웹에서 비디오와 오디오 분야에서 최고급으로 만듬
  - 성능 및 통합 - 속도 최적화 및 컴퓨터 하드웨어 개선으로 더 나은 사용 제공
  - 장치 접근
  - 더 정교한 스타일링
* Describe the difference between a `cookie`, `sessionStorage` and `localStorage`.
  - 세 가지 기술은 모두 클라이언트 측에서 중요한 값을 저장한다. 모두 문자열로 저장 하지만 저장하는 용량이 다르다.
  - cookie 는 4kb, 나머지는 5MB
  - cookie 는 모든 HTTP 요청과 함께 서버로 보내지만 localStorage, sessionStorage는 안보낸다.
  - 만료는 쿠키는 수동으로 설정하고, localStorage는 영구적, sessiongStorage는 탭을 닫을때 만료된다.
* Describe the difference between `<script>`, `<script async>` and `<script defer>`.
  - html에서 script태그를 만나면 script를 실행하고, script src는 해당 파일을 로드 한 후 스크립트 실행하거나, 해당 url에 있는 스크립트를 로드해서 실행한다.
  - 기본적으로 웹 브라우저가 외부 자바스크립트를 불러오는 일반 script 태그를 만나게 되면, 우선 해당 스크립트를 내려받아 실행하는데, 실행할 때 까지 웹 문서의 HTML 코드 파싱 작업을 잠시 뒤로 미룬다.
  - async 혹은 defer 된 스크립트 문서는 parsing 작업의 중단 없이 동시에 내려받게 되는데, 둘의 차이를 결정짓는 중요한 것은 바로 스크립트 실행되는 시점이 다르다.
  - async는 스크립트를 내려받는 즉시 바로 실행되는데 반해 defer는 문서의 parsing 작업이 끝난 후에 실행된다.
  - script가 문서를 직접 만지고 조작하거나 서로 간 로딩 순서가 중요할떄는 defer 속성을 쓰고, 그렇지 않다면 async 속성을 써서 웹페이지 로딩 속도를 줄인다.
* Why is it generally a good idea to position CSS `<link>`s between `<head></head>` and JS `<script>`s just before `</body>`? Do you know any exceptions?
  - body 태그 안에 script를 넣는 이유는 script태그는 다운로드되고 실행되는 동안 html 파싱을 차단합니다. 스크립트를 맨 아래에서 다운로드하면 html을 먼저 파싱하여 사용자에게 표시할 수 있다.
* What is progressive rendering?
  - 콘텐츠를 가능한 한 빨리 표시하고, 웹 페이지의 성능을 향상시키는 데 사용되는 기술이다.
  - 이 기술에는 페이지 로드시 모든 이미지를 로드하는 대신 브라우저 뷰포트에 들어올때 뷰의 픽셀을 계산하여 일부 자바스크립트가 계산된 픽셀만큼 이미지를 로드하는 방식이 있고, 서드파티가 HTML에 로드되는 경우 메인 컨텐트를 로드 시킨 후 서드파티를 로드시킨다. 예를 들어 사이드바와 메인화면이 있으면 사이드바 보다는 메인 화면을 먼저 로드시키는 방법으로 고려해야 한다.
  - 이러한 기술은 사용자에게 빠른 웹환경을 제공하기 위해 고안된 기술이다.
* Why you would use a `srcset` attribute in an image tag? Explain the process the browser uses when evaluating the content of this attribute.
  - 기기의 디스플레이 너비에 따라 다른 이미지를 사용자에게 제공하려는 경우 `srcset` 속성을 사용한다.
  - srcset을 사용하는 이유는, 레티나 디스플레이를 통해 장치에 고품질 이미지를 제공하여 사용자 경험을 향상시키고, 저해상도 이미지를 저사양 기기에 제공하여 성능을 높이고 데이터 낭비를 줄일수 있습니다.  
* Have you used different HTML templating languages before? (다른 HTML 템플릿 언어를 사용해본 적이 있습니까?)
