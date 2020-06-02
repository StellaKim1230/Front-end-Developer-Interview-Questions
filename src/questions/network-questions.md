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
