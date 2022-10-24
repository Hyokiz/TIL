# 20221024 TIL

# DOM

> 개요

- 브라우저에서의 JavaScript

  - 웹 페이지에서 복잡한 기능을 구현하는 스크립트 언어
  - 가만히 정적인 정보만 보여주는 것이 아닌 주기적으로 갱신되거나, 사용자와 상호 작용이 가능하거나, 애니메이션이 적용된 그래픽 등에 관여

  - 스크립트 언어(Script Language)

    - 응용 소프트웨어를 제어하는 컴퓨터 프로그래밍 언어

> Browser APIs

- 웹 브라우저에 내장된 API. 현재 컴퓨터 환경에 관한 데이터 제공이나 여러가지 유용하고 복잡한 일 수행

- 종류

  - DOM
  - Geolocation API(지리 정보)
  - WebGL(그래픽) 등

> DOM

- 문서 객체 모델(Document Object Model)
- 문서의 구조화된 표현 제공, 프로그래밍 언어가 DOM 구조에 접근할 수 있는 방법 제공

  - 문서 구조, 스타일, 내용 등을 변경할 수 있게 도움
  - HTML 콘텐츠를 추가, 제거, 변경하고 동적으로 페이지에 스타일을 추가하는 등 HTML/CSS를 조작할 수 있음

- HTML문서를 구조화하여 각 요소를 객체(object)로 취급
- 단순한 속성 접근, 메서드 활용 뿐만 아니라 프로그램이 언어적 특성을 활용한 조작 가능

> DOM

- DOM은 문서를 논리 트리로 표현
- DOM메서드를 사용하면 프로그래밍적 트리에 접근할 수 있고 이를 통해 문서의 구조, 스타일, 컨텐츠를 변경할 수 있음

> DOM

- 웹 페이지는 일종의 문서(document)
- 이 문서는 웹 브라우저를 통해 그 내용이 해석되어 웹 브라우저 화면에 나타나거나 HTML 코드 자체로 나타나기도 함
- DOM은 동일한 문서를 표현하고, 저장하고, 조작하는 방법을 제공
- DOM은 웹 페이지의 객체 지향 표현이며, JavaScript와 같은 스크립트 언어를 이용해 DOM 을 수정할 수 있음

> DOM에 접근하기

- DOM을 사용하기 위해 특별히 해야할 일은 없다.
- 모든 웹 브라우저는 스크립트 언어가 접근할 수 있는 웹페이지를 만들기 우해 DOM을 항상 사용함
- "DOM의 주요 객체"들을 활용하여 문서를 조작하거나 특정 요소들을 얻을 수 있음

> DOM의 주요 객체

- window
- document
- navigator, location, history, screen 등

> window object

- DOM을 표현하는 창
- 가장 최상위 객체(작성 시 생략 가능)
- 탭 기능이 있는 브라우저에서는 각각의 탭을 각각의 window 객체로 나타냄
- 창 전체를 의미

> window의 메서드 예시

- 새 탭 열기

```js
window.open()

Window {window: Window, self: Window, document: document, name: '', locatio: Location, ...}
```

- 경고 대화 상자 표시

```js
window.alert()

undefined
```

- 인쇄 대화 상자 표시

```js
window.print()

undefined
```

