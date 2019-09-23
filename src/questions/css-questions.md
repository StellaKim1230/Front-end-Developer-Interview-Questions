---
title: CSS Questions
layout: layouts/page.njk
permalink: /questions/css-questions/index.html
---

* What is CSS selector specificity and how does it work? (css 선택자 명시도는 무엇이며 어떻게 작동 되는가?)
[반드시 기억해야하는 선택자 30개](https://code.tutsplus.com/ko/tutorials/the-30-css-selectors-you-must-memorize--net-16048)
  - 선택자란 말 그대로 선택을 해주는 요소입니다. 이를 통해 특정 요소들을 선택하여 스타일을 적용할 수 있게 됩니다.
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
  - 요소를 어떻게 보여줄지를 결정한다.
* What's the difference between inline and inline-block?
  - none : 보이지 않음
  - block
    - `<div>`, `<p>` 태그 등이 이에 해당된다
    - 가로 길이가 기본적으로 100%이며, block인 태그를 이어서 사용하면 줄바꿈 되어 보인다.
    - width, height 속성을 지정 할 수 있으며, 레이아웃 배치시 주로 사용한다.
  - inline-block
    - block과 inline 의 중간 형태라고 볼 수 있다. 줄 바꿈이 되지는 않지만 크기를 지정할 수 있다.
  - inline
    - `<span>`, `<b>`, `<i>` 태그 등이 해당된다.
    - block과 달리 줄 바꿈이 되지 않고, width와 height 지정 할 수 없다.
* What's the difference between the "nth-of-type()" and "nth-child()" selectors?
  - 둘 다 순서와 연관된 css의 선택자이다.
  - nth-child : 부모 엘리먼트의 모든 자식 엘리먼트중 n 번째
  - nth-of-type : 부모 엘리먼트의 특정 자식 엘리먼트중 n 번째
  ```
  <div class="box">
    <p>1. p태그 1</p>
    <span>2. span태그 2</span>
    <p>3. p태그 3</p>
    <span>4. span태그 4</span>
    <p>5. p태그 5</p>
  </div>
  ```
  ```
  <style>
   .box > p:nth-child(5) {
     color: red;  // 5 번
   }

   .box > p:nth-of-type(3) {
     color: red; // 5 번
   }
  </style>
  ```
* What's the difference between a relative, fixed, absolute and statically positioned element?
  - static : 기본 위치. `static`엘리먼트는 위치가 지정된 것이 아니라고 표현하며, `static`이 아닌 다른 값으로 지정된 엘리먼트에 대해 위치가 지저오댔다고 표한한다.
  - relative : 별도의 프로퍼티를 지정하지 않는 이상 static과 동일하게 동작한다. 상대 위치가 지정된 엘리먼트에 top, right, bottom, left를 지정하면 기본 위치와 다르게 위치가 조정된다. 다른 콘텐츠는 해당 엘리먼트에서 남긴 공백에 맞춰 들어가게끔 조정되지 않는다.
  - fixed : 뷰포트에 상대적으로 위치가 지정되는데, 페이지가 스크롤되더라도 늘 같은곳에 위치한다는 뜻이다.
  - absolute : 뷰포트에 상대적으로 위치가 지정되는게 아니라 가장 가까운 곳에 위치한 부모 요소에 상대적으로 위차가 지정된다는 점을 제외하면 fixed와 비슷하게 동작한다.
  [참고자료](https://ko.learnlayout.com/position.html)
* What existing CSS frameworks have you used locally, or in production? How would you change/improve them?
  - 
* Have you played around with the new CSS Flexbox or Grid specs?
  - flex-grow 를 사용해보았지만, 브라우저에서 비호환성 문제가 있었다.
* Can you explain the difference between coding a web site to be responsive versus using a mobile-first strategy?
  - 반응형 웹사이트를 만드는 것은 일부 요소가 미디어 쿼리를 통해 장치의 화면 크기(일반적으로 뷰포트 너비)에 따라 크기나 기타 기능을 조정하도록 반응함을 의미한다.
  - 모바일 우선 전략 또한 반응형이지만, 모바일 장치에 대한 모든 스타일을 정의해야하며 나중에 다른 장치에 대한 특정 규칙을 추가해야 한다.
  - 모바일 우선 전략의 장점은 모바일 장치에서 적용되는 모든 규칙이 미디어 쿼리에 대해 유효성 검사를 받을 필요가 없어서 뛰어난 성능을 발휘한다.
  - 모바일 우선 전략의 장점2 반응형 CSS 규칙과 관련하여 보다 명확한 코드 작성
* Have you ever worked with retina graphics? If so, when and what techniques did you use?
  - 아니요
* 반응형 디자인은 적응형 디자인과 어떻게 다른가?
  - 반응형 웹은 하나의 템플릿을 사용해 모든 기기에 대응하는데 반해, 적응형 웹은 선별된 기기 유형에 독립적인 템플릿이 요구된다. 즉, 별도 페이지 제작이 필요하다
  - 적응형 웹이 반영된 예로 네이버, 다음 같은 포털 사이트를 들 수 있는데 기존부터 서비스 되고 있는 사이트 변경 없이, 모바일 환경에 대응하기 위해 별도의 url을 통해 서비스 합니다. 모바일 환경에서 기존 사이트 주소로 접속할 경우, 이를 감지하여 모바일 전용 페이지로 리다이렉션 합니다.
* Is there any reason you'd want to use `translate()` instead of *absolute positioning*, or vice-versa? And why?
(절대 위치 지정 대신 translate()를 사용하거나 그 반대의 이유가 있씁니까? 왜?)
  - 브라우저의 성능 문제로 볼 수 있다. `transform` 이나`opacity`를 변경하면 브라우저의 리플로우나 리페인트가 트리거되지 않고 컴포지션만 실행되는 반면, 절대 위치 값을 변겨하면 '리플로우'가 발생한다. `transform`을 사용하면 브라우저에서 이 요소에 위한 GPU레이어를 생성하지만 포지션 위치 속성 변경은 CPU를 사용한다. 그러므로 `translate()`가 더 효율적이며 매끄러운 애니메이션을 위한 페인트 시간이 짧아진다.
* 블럭 내 자식 요소를 중앙 정렬하는 방법은?
```
div {
  display: block;
  margin: 0 auto;
}
```
