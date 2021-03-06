---
title: Web Fundamental Questions
layout: layouts/page.njk
permalink: /questions/web-fundamental-questions/index.html
---

- 브라우저 엔진이 하는 일
- 웹팩이란
  - 프로젝트의 구조를 분석하고 자바스크립트 모듈을 비롯한 모든 리소스들을 찾은 다음 브라우저에서 이용할 수 있는 번들로 묶고 패킹하는 모듈 번들러이다.
- typescript, typescript의 장점
  - 타입을 체크하는 javascript의 확장된 언어이다. typescript는 컴파일되는 시점에 타입을 체크하고, 컴파일 후에 javascript으로 변환한다.
  - 장점은 정적 타입을 지원하므로 컴파일 단계에서 오류를 발견할 수 있다. 명시적인 정적 타입 지정은 개발자의 의도를 명확하게 코드를 기술하며, 코드의 가독성을 높이고 예측할 수 있고 디버깅이 쉽다.
- 단위테스트는 왜 해야 하는가?
  - 단위테스트는 모듈이나 어플리케이션 안에 있는 개별적인 코드 단위가 예상대로 작동 하는지 확인하는 것이다.
  - 코드가 어떻게 작성하는지 생각하는데 도움을 준다.
  - 주된 효과로는 단위 테스트를 추가하는 것이 어플리케이션의 유닛(함수 외)를 더 작게 만든다.
  - 많은 일을 하는 테스팅 코드는 어렵다.
  - 함수를 단 한가지 만의 일을 하도록 작성해야 한다. 이렇게 하면 단위 테스트도 쉽게 테스트 할 수 있다.
  - 다른 장점은 문제를 빨리 해결하고 변화를 쉽게하며 통합을 간단하게 하고 설계를 개선할 수 있다.
- 컴포넌트란
  - (화면에서) 재사용한 기능과 마크업을 가지고 화면을 만들어내는 단위
- UX란
  - 사용자가 프로덕트나 서비스에 느끼는 감정이다 (경험)
- SPA란
  - 단일 페이지 어플리케이션은 브라우저에 로드되고 난 뒤에 페이지 전체를 서버에 요청하는것이 아니라 최초 한 번 페이지 전체를 로딩한 후 이후부턴 데이터만 변경해서 사용할 수 있는 웹 어플리케이션을 말한다.
- 화면 렌더링 동작 순서 (+FOUC)

  - www.naver.com 을 입력했을 때 화면이 켜지기까지

  1. Dns 캐시 조회
  2. /etc/hosts 조회
  3. Dns 서버 질의 -> 아이피 조회
  4. 아이피로 naver 서버로 리퀘스트
  5. index.html 로 리스펀스
  6. `<doctype , html, 등 하이퍼텍스트마크업언어`

  - Html, body, src, head 등 각각 토큰을 만들어서 토큰으로 Dom 트리를 만든다
  - Css 파일을 확인하고 돔 트리에 붙인다.
  - Javascript 실행
  - 렌더링트리구축
  - 레이아웃생성 ( 렌더 트리가 다 만들어지고 나면, 레이아웃 과정을 거친다. 각 노드들은 스크린의 좌표가 주어지고 정확히 어디에 나타나야 할 지 위치가 주어진다.)
  - 페인팅으로 화면에 그려진다. (그 다음 작업은 렌더링 된 요소들에 색을 입히는 과정인데, 트리의 각 노드들을 거쳐가면서 paint() 메소드를 호출한다. 그러고나면 스크린에 원하는 정보가 나타난다.)

- FOUC 를 막기 위해서 css가 먼저 선언 되어야 한다. (Flash Of Unstyled Content) : 외부의 css가 불러오기전에 잠시 스타일이 적용되지 않은 웹 페이지가 나타나는 현상이다.

- Js 는 바디 태그 밑에 있어야 하는 이유 : script 태그가 로드되고 실행될때 html 파싱을 멈추고 로드되고 실행된다. 사용자에게 불편한 경험을 제공할 수 있다. dom 이 다 파싱 된 후에 script가 로드되고 실행되어야 한다.
