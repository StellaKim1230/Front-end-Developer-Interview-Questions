---
title: Ui Questions (React.js, Vue.js, Angular)
layout: layouts/page.njk
permalink: /questions/ui-library-questions/index.html
---
* MVC, MVVP, flux 패턴이란
* redux에서 action 이란
  - 어떤 변화가 일어나야 할 지 나타낸다.
* redux에서 reducer 이란
  - action 객체를 받았을 때, 데이터를 어떻게 바꿀지 처리할지 정의한다.
  - 스토어 안에 위치하며, 변화에 관련된 작업을 하는 함수이다. 스토어의 상태와 액션 객체를 인자로 받아 변화를 일으키며, 함수의 리턴값은 새로운 상태이다.
  - reducer 함수는 다음의 3가지를 만족하는 순수함수여야 한다.
  - reducer 함수 내에서 비동기 작업을 수행하면 안된다.
  - reducer 함수로 들어온 인수를 변경해서는 안된다.
  - reducer 함수로 들어온 인수가 같다면 결과는 항상 동일해야 한다.
* reducer을 이용한 상태관리 프로젝트 순서
  - 액션 타입 생성 (action은 객체이며, type 속성을 반드시 가지고 있어야 한다.)
  - 액션 생성 함수 정의 (액션 생성 함수를 통하여 action 객체를 빠르게 만들 수 있도록 도와준다.)
  - 실질적으로 변화를 일으키는 함수인 리듀서 정의 (인자로는 prevState와 action이 들어오고, 들어오는 action객체의 타입에 따라 어떤 변화를 일이클지 정의한다.)
  - 스토어 생성(위에서 만든 리듀서를 포함하여 createStore을 통해 생성한다)
  - 스토어의 변화가 생길때 실행될 리스너 함수 정의
  - 클릭 등 이벤트에 dispatch를 통해 액션 전달
* redux 사용하는 이유
* 꼭 redux가 필요한가? 전역변수에 데이터 관리하고 window 객체에서 global 하게 관리하면 안되는가?
* Fragment란
  - 별도의 노드를 추가하지 않고 여러 자식을 그룹화 할 수 있다.
  - dom 구조는 항상 트리 구조를 가져야 한다.
* map 에서 key의 역할이란
  - React가 어떤 아이템이 바뀌었는지, 혹은 추가되었는지, 삭제되었는지를 인식하는데 도움을 준다.
* ref 란
  - React 에서 DOM에 직접적인 접근을 해야할 때 사용한다.
  - input/textarea 등에 포커스 해야 할 때, 특정 DOM의 크기를 가져와야 할 때, 특정 DOM에서 스크롤 위치를 가져오거나 설정을 해야할 때, 외부 라이브러리를 사용할 때 등
* DOM Selector VS React Ref
  - ref 는 구성 요소에 이미 DOM 노드에 대한 참조가 있으므로 참조가 약간 더 빠르다. document.querySelector을 사용하면 브라우저가 노드를 찾기 위해 트리 구문 분석을 하고 찾으니 react ref 보다 느려질 수 있다.
* one way binding vs two way binding
* react life cycle
  - 컴포넌트 생성 (constructor -> componentWillMount -> render -> componentDidMount)
  - prop 변화 (componentWillReceiveProps -> shouldComponentUpdate -> componentWillUpdate -> render -> componentDidUpdate)
* presentation component
  - 데이터를 어떻게 보여지는지와 관련있고, css 작업을 presentation component 에서 한다.
* container component
  - 데이터 로직 처리를 담당한다. 어떻게 동작하는지와 관련이 있고, 리덕사 액션을 호출한다. presentation component에 콜백함수로써 제공하고, 데이터 소스 역할을 하기 때문에 상태가 자주 변경된다.
* react hooks (useEffect, useState)
  - useEffect: 리액트에게 컴포넌트가 렌더링 이후에 어떤 일을 수행해야 하는지 말한다.
  - useState: 상태 유지 값과 그 값을 갱신하는 함수를 반환한다.
* class component vs functional component
  - class component는 life cycle이 있고, functional component는 life cycle이 없다.
