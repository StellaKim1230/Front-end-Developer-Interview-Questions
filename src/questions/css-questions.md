---
title: CSS Questions
layout: layouts/page.njk
permalink: /questions/css-questions/index.html
---

* What is CSS selector specificity and how does it work? (css 선택자 명시도는 무엇이며 어떻게 작동 되는가?)
  - specificity는 브라우저가 어떤 css 속성값이 요소와 가장 관련이 있고 따라서 적용되는 지를 결정한다.
  - type 선택자(ex: h1) 및 가상 요소(ex: :before) > class 선택자 > id 선택자
  - 요소에 추가된 인라인 스타일 ( style = "font-weight:bold")은 항상 외부 스타일시트의 모든 스타일을 덮어쓰고, 따라서 가장 높은 명시도를 갖는 것으로 생각 할 수 있다.
* What's the difference between "resetting" and "normalizing" CSS? Which would you choose, and why?
  - reset CSS : 설정돼 있는 모든 속성을 초기화 시키는 목적으로 사용된다.
  - normalize CSS : 무작정 초기화 시키는것이 아닌, 브라우저의 기본 스타일을 통일시켜주는 방법
  - 작업에 리소스가 더 많이 들어가는것은 reset 이지만, 섬세하게 하나하나 핸들링하기엔 더 좋다. reset과 normalize를 비교해보고 현재 프로젝트에 맞는 방법을 택할것이다.
* Describe Floats and how they work.
  - float는 css 위치 지정 속성입니다. 원래 웹 페이지에서 이미지를 띄워서 텍스트와 함께 배치할 것인가에 대한 속성이다.
  - 부모요소가 자식요소를 더 이상 감싸지 않고 높이 값을 파악하지 못하게 되는 버그 발생한다. 부모 요소의 높이 값이 0px로 출력되고, 전체적인 HTML 요소들이 뒤엉켜버리는 경우가 많다.
  - 부모 요소가 다시 자식 요소를 감쌀 수 있게 float를 초기화(clear) 하여 버그를 고쳐주는(fix) 코드를 clearfix라고 한다.
* Describe z-index and how stacking context is formed.
  - z-index 속성은 요소의 겹치는 순서를 제어한다. static이 아닌 position 값을 갖는 요소에만 영향을 준다.
  - z-index 값이 없으면 dom에 나타나는 순서대로 요소가 쌓이게 된다. 
  - stacking context는 레이어 집합을 포함하는 요소이다. stacking context 내에서 자신의 z-index 값은 문서루트가 아닌 해당 요소를 기준으로 설정된다.
* Describe BFC (Block Formatting Context) and how it works.
  - 블록 서식 문맥은 웹 페이지의 블록 레벨 요소를 렌더링하는데 사용되는 css의 비주얼 서식 모델중 하나다.
  - BFC 는 다음 중 하나에 의해 생성된다.
    - 루트 또는 이를 포함하는 요소
    - float
    - 절대위치로 지정된 요소 (position이 absolute 또는 fixed인 요소)
    - 인라인블록 (display : inline-block인 요소 )
    - 테이블 셀 (display: table-cell인 요소, HTML table cell의 기본값)
    - 테이블 캡션 ( display: table-caption 인 요소, HTML table caption의 기본값)
    - overflow가 visible이 아닌 요소
    - flex box(display: flex or inline-flex) 인 요소
* What are the various clearing techniques and which is appropriate for what context?
  - 예로 float 속성을 통해 태그를 부유시킨 이후 문서의 흐름을 제거하기 위해 사용한다.
  - left: 좌측 부유 제거
  - right: 우측 부유 제거
  - both: 양측 모두 제거
  - clear 해주기 위해서는 float된 요소 다음에 clear하는 태그를 따로 삽입해야 하는 불편함이 있어 부유를 제거하고싶은 div 태그에 다음을 적용하면 된다.
  - ` .class선택자:after { content: ""; display: block; clear: both; }`
* css 스프라이트는 무엇입니까?
  - 여러 이미지를 하나의 큰 이미지로 결합합니다. 스프라이트 생성기를 사용하여 여러 이미지를 하나로 묶어 적절한 css를 생성합니다.
  - 각 이미지는 background-image, background-position, bacground-size 속성이 정의 된 해당 css클래스를 갖는다.
  - 장점 : 여러 이미지에 대한 HTTP 요청 수 줄이기
* How would you approach fixing browser-specific styling issues?
  - 문제를 일으키는 브라우저를 식별한 후에 해당 브라우저가 사용중 일 때만 로드되는 별도의 스타일 시트를 이용(서버 측 렌더링 필요)
  - 프리픽스 추가
  - Reset CSS pr Normalize.css 사용한다.
* How do you serve your pages for feature-constrained browsers?
  * What techniques/processes do you use?
  - caniuse를 사용하여 기능 지원을 확인한다.
* What are the different ways to visually hide content (and make it available only for screen readers)?
  - `visibility: hidden` : 그러나 요소는 아직 페이지의 흐름에 여전히 공간을 차지하고 있다.
  - `width: 0, height: 0` : 요소가 화면의 어떤 공간도 차지 안한다.
* Have you ever used a grid system, and if so, what do you prefer?
  - 사용 안합니다.
* Have you used or implemented media queries or mobile specific layouts/CSS?
  - 네
* Are you familiar with styling SVG?
  - 아니요, 색상과 크기 정도만 수정 가능합니다.
* Can you give an example of an `@media` property other than `screen`?
  - all : 모든 미디어 기기 장치
  - print: 프린터
  - speech : 화면을 크게 읽는 스크린리더
  - screen : 컴퓨터 스크린, 태블릿, 스마트폰 등
  ```
  @media print {
    body {
      color: black;
    }
  }
  ```
* What are some of the "gotchas" for writing efficient CSS?(효율적인 css를 작성하는데 있어 어려움은 무엇입니까?)
  - 
* What are the advantages/disadvantages of using CSS preprocessors?
  * Describe what you like and dislike about the CSS preprocessors you have used.
  - 장점 : css의 유지보수성이 향상된다.
  - 중첩된 선택자를 작성하기 쉽다.
  - 일관된 스타일링 설정을 위한 변수 사용. 여러 프로젝트에 걸쳐 테마 파일을 공유할 수 있습니다.
  - 반복되는 css를 위한 mixins 생성
  - 코드를 여러 파일로 나눕니다. css파일도 나눌 수 있지만, 그렇게 하기 위해서는 각 css파일을 다운로드하기 위한 HTTP 요청이 필요합니다.
  - 단점 : 전처리기를 위한 도구가 필요합니다. 다시 컴파일 하는 시간이 느릴 수 있습니다.
* How would you implement a web design comp that uses non-standard fonts?
  - 위에 다 좋은 장점이 있지만 Less는 자바스크립트로 작성되었으며 node와 잘 작동한다.
* 비표준 글꼴을 사용하는 웹 디자인을 구현하는 방법은 무엇입니까?
  - `font-face`를 사용하고  `font-weight`가 다른 경우 `font-family`를 정의한다.
* Explain how a browser determines what elements match a CSS selector. (css 셀렉터에 일치하는 요소가 어떤 것인지 브라우저가 어떻게 결정되는지를 설명하시오)
  - 브라우저는 셀렉터를 오른쪽(선택자)에서ㅓ 왼쪽으로 일치시킵니다. 브라우저는 선택자에 따라 DOM의 요소를 필터링하고 부모 요소를 검사하여 일치를 판정합니다. 예를 들어 이 셀렉터 p span는 브라우저는 먼저 모든 <sapn> 요소를 찾아 그 부모의 루트까지 통과하며 <p> 요소를 찾습니다. 특정한 <span> 의경우 <p>를 찾는 즉시 <span>이 일치하는 것을 알고 있으며, 그에 따라 매칭 중지합니다.
* Describe pseudo-elements and discuss what they are used for.
  - 선택한 요소의 특정한 부분을 스타일링 할 수 있다. 마크업을 수정하지 않고 (:before, :after) 텍스트 데코레이션을 위해 사용하거나 (:first-line, :first-letter) 또는 마크 업에 요소를 추가할 수 있습니다.
  - :first-line과 :first-letter는 텍스트 데코레이션하는데 사용한다.
  - 툴팁의 삼각형 화살표는 :before와 :after을 사용합니다.
* Explain your understanding of the box model and how you would tell the browser in CSS to render your layout in different box models.
* What does ```* { box-sizing: border-box; }``` do? What are its advantages?
  - 기본적으로 요소들은 `box-sizing : content-box ` 가 적용되고, 내용의 크기만 고려됩니다.
  - `box-sizing: border-box` 는 요소의 `width`와 `height`가 어떻게 계산되는지를 변경하여 `border`과 `padding`도 계산에 포함된다.
* What is the CSS `display` property and can you give a few examples of its use?
* What's the difference between inline and inline-block?
* What's the difference between the "nth-of-type()" and "nth-child()" selectors?
* What's the difference between a relative, fixed, absolute and statically positioned element?
  - static : 기본 위치. 요소는 평소와 같이 페이지에 위치합니다.
  - relative : 별도의 프로퍼티를 지정하지 않는 이상 static과 동일하게 동작한다. 상대 위치가 지정된 엘리먼트에 top, right, bottom, left를 지정하면 기본 위치와 다르게 위치가 조정된다.
  - fixed : 뷰 포트에 상대적으로 위치가 지정되는데, 이는 페이지가 스크롤되더라도 늘 같은 곳에 위치한다.
  - absolute : 뷰포트에 상대적으로 위치가 지정되는게 아니라 가장 가까운 곳에 위치한 부모 요소에 상대적으로 위차가 지정된다는 점을 제외하면 fixed와 비슷하게 동작한다.
* What existing CSS frameworks have you used locally, or in production? How would you change/improve them?
* Have you played around with the new CSS Flexbox or Grid specs?
* Can you explain the difference between coding a web site to be responsive versus using a mobile-first strategy?
* Have you ever worked with retina graphics? If so, when and what techniques did you use?
* Is there any reason you'd want to use `translate()` instead of *absolute positioning*, or vice-versa? And why?
