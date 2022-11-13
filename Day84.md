# 20221113 TIL

# Front-end Development란?

- Web App(SPA)을 만들 때 사용하는 도구

  - SPA - Single Page Application

> Web App이란?

- 웹 브라우저에서 실행되는 어플리케이션 소프트웨어
- 디바이스에 설치된 App처럼 보이는 것
- 웹 페이지가 디바이스에 맞는 적절한 UX/UI로 표현되는 형태

> SPA(Single Page Application)

- 서버에서 최초 1장의 HTML만 전달받아 모든 요청에 대응하는 방식

  - CSR(Client Side Rendering) 방식으로 요청을 처리

> SSR(Server Side Rendering) 이란?

- 기존의 요청 방식은 SSR
- Server가 사용자의 요청에 적합한 HTML을 렌더링하여 제공하는 방식
- 전달받은 새 문서를 보여주기 위해 브라우저는 새로고침을 진행

> CSR(Client Side Rendering)

- 최초 한 장의 HTML을 받아오는 것은 동일

  - 단 server로부터 최초로 받아오는 문서는 빈 html
  - 각 요청에 대한 대응을 JS를 사용하여 필요한 부분만 렌더링

  1. 필요한 페이지를 서버의 AJAX로 요청
  2. 서버는 데이터를 JSON 방식으로 전달
  3. JSON 데이터를 JS로 처리, DOM 트리에 반영(렌더링)

> 왜 CSR 방식을 사용할까?

1. 모든 HTML 페이지를 서버로부터 받아서 표시하지 않아도 됨

   - 트래픽 감소 > 응답 속도 빨라짐

2. 필요한 부분만 고쳐 나가므로 각 요청이 끊임없이 진행

   - 요청이 자연스럽게 된다 = UX 향상

3. BE와 FE의 작업 영역을 명확히 분리할 수 있음

   - 협업이 용이해짐

> CSR은 만능일까?

- 첫 구동 시 필요한 데이터가 많으면 최초 작동 시작까지 오랜 시간 소요
- 검색 엔진 최적화가 어려움

# Vue

> MVVM Pattern

- Model : 실제 데이터 == JSON
- View : 눈에 보이는 부분 == DOM
- View Model(Vue)

  - View를 위한 Model
  - View와 연결되어 Action을 주고 받음
  - Model이 변경되면 View Model도 변경되고 바인딩된 View도 변경됨
  - View에서 사용자가 데이터를 변경하면 View Model의 데이터가 변경되고 바인딩된 다른 View도 변경됨

> 정리

- MVC 패턴에서 Controller 를 제외하고 View Model을 넣은 패턴
- 독립성 증가, 적은 의존성
- View에서 데이터를 변경하면 View Model의 데이터가 변경되고, 연관된 다른 View도 함께 변경된다

# Directives

> Directives 기본 구성

- v-접두사가 있는 특수 속성에는 값을 할당할 수 있음

  - 값에는 JS 표현식을 작성할 수 있음

- directive의 역할은 표현식의 값이 변경될 때 반응적으로 DOM에 적용하는 것

> v-text

- 가장 기본적인 바인딩 방법
- {{}} 와 거의 비슷

> v-html

- RAW HTML 을 표현할 수 있는 방법
- 단, 사용자가 입력하거나 제공하는 컨텐츠에는 사용 금지

> v-show

- 표현식에 작성된 값에 따라 element를 보여줄 것인지 결정

  - boolean 값이 변경될 때 마다 반응

- 대상 element의 display 속성을 기본 속성과 none으로 toggle
- 요소 자체는 항상 DOM에 렌더링

- 화면에서만 사라졌을 뿐, DOM에 존재

> v-if

- v-show와 사용 방법은 동일
- isActive의 값이 변경될 때 반응
- 단 값이 false인 경우 DOM에서 사라짐

> v-show vs v-if

- v-show

  - 표현식 결과 관계 없이 렌더링 > 초기 렌더링 비용은 v-if보다 높음
  - 렌더링 후 toggle 비용은 적음

- v-if

  - 표현식 결과가 false 인 경우 렌더링 되지 않으므로 초기 렌더링 비용은 v-show보다 낮을 수 있음
  - 단, 표현식 값이 자주 변경되는 경우 잦은 재 렌더링으로 비용이 증가할 수 있음

> v-for

- for ... in ... 형식으로 작성
- 반복한 데이터 타입에 모두 사용 가능
- index를 함께 출력하고자 한다면 (char, index) 형태로 사용 가능
- 각 요소가 객체라면 dot notation으로 접근 가능

> key

- v-for 사용 시 반드시 key 속성을 각 요소에 작성
- 주로 v-for directive 작성 시 사용
- key가 중복되어서는 안됨
- 각 요소가 고유한 값을 가지고 있다면 생략 가능

> v-on

- :을 통해 전달받은 인자를 확인
- 대기하고 있던 이벤트가 발생하면 할당된 표현식 실행
- method를 통한 data 조작도 가능
- @ shortcut

> v-bind

- class의 경우 다양한 형태로 연결 가능

  - 조건부 바인딩
  - 다중 바인딩

- vue data의 변화에 반응하여 DOM 에 반응
- : shortcut 제공

> v-model

- Vue instance와 DOM의 양방향 바인딩

# Vue advanced

> computed

- computed 객체에 정의한 함수를 페이지가 최초로 렌더링 될 때 호출하여 계산

  - 계산 결과가 변하기 전까지 함수를 재호출 하는 것이 아닌 계산된 값을 반환


> methods vs computed

- methods

  - 호출될 때마다 함수를 실행
  - 같은 결과여도 매번 새롭게 계산

- computed

  - 함수의 종속 대상의 변화에 따라 계산 여부가 결정됨
  - 종속 대상이 변하지 않으면 항상 저장(캐싱)된 값 반환

> watch

- 특정 데이터의 변화를 감지하는 기능

  1. watch 객체 정의
  2. 감시할 대상 data 지정
  3. data가 변할 시 실행 할 함수를 정의

- 첫 번째 인자는 변동 후 
- 두 번째 인자는 변동 전

- 실행 함수를 vue method로 대체 가능

  1. 감시 대상 data 의 이름으로 객체 생성
  2. 실행하고자 하는 method를 handler에 문자열 형태로 할당

- 내부 요소 변경 변화 감지를 위해서는 deep 속성 추가 필요

> filters

- 텍스트 형식화를 적용할 수 있는 필터
- |가 함께 추가되어야 함

# Vue Style Guide

> 1. v-for는 항상 key와 함께 사용하기

- 내부 컴포넌트 상태의 일관성 유지
- 데이터의 예측 가능한 행동 유지(객체 불변성)

> 2. v-for에 v-if 절대 사용하지 말기

- v-if 가 먼저 계산되고, 해당 처리 시점에 반복 면수인 user가 존재하지 않기 때문에 에러
- v-if 가 v-for보다 높은 우선순위

- 해결방법

  - computed속성 사용
  - v-for가 있는 template 태그로 li 감싸기

---

# Vue CLI

> NPM(Node Package Manage)

- 자바스크립트 패키지 관리자

  - python에 pip가 있다면 Node.js에는 npm

> Vue CLI

- 설치 

npm install -g @vue/cli

# Vue CLI 프로젝트 구조

> node_modules

- node.js 의 여러 의존성 모듈

> node_modules - babel

- 자바스크립트의 ES6+ 코드를 구버전으로 번역 / 변환해주는 도구

> node_modules - webpack

- 모듈 간의 의존성 문제 해결을 위한 도구

> Module

- 파일 하나에 모든 기능을 담기 어려워짐
- 파일을 여러 개로 분리하여 관리 > js 파일 하나가 하나의 모듈
- 기능 단위 분리

> Module 의존성 문제

- 모듈 수가 많아지고 모듈 간의 의존성이 깊어지면서 문제 파악 어려움

  - webpack은 모듈간의 의존성 문제 해결을 위해 등장

> Bundler

- 모듈 의존성 문제를 해결해주는 작업이 Bundling
- 모듈을 하나로 묶어주고 묶인 파일은 하나 또는 여러개로 만들어짐
- 자동으로 설정

> package.json

- 프로젝트의 종속성 목록과 지원되는 브라우저에 대한 구성 옵션을 포함

> package-lock.json

- node_modules에 설치되는 모듈과 관련된 모든 의존성을 설정 및 관리
- 협업 및 배포 환경에서 정확히 동일한 종속성을 설치하도록 보장하는 표현
- 사용 할 패키지의 버전 고정

> public/index.html

- Vue 앱의 뼈대가 되는 html 파일
- Vue 앱과 연결될 요소가 있음

> src/

- assets

  - 정적 파일을 저장하는 디렉토리

- components

  - 하위 컴포넌트 들이 위치

- App.vue

  - 최상위 컴포넌트
  - public/index.html과 연결됨

- main.js

  - webpack이 빌드를 시작할 때 가장 먼저 불러오는 entry point
  - public/index.html과 src/App.vue를 연결시키는 작업이 이루어지는 곳

# Component

> component

- UI를 독립적이고 재사용 가능한 조각들로 나눈 것

  - 기능별로 분화

> Component based architecture 특징

- 관리 용이

  - 유지 보수 비용 감소

- 재사용성
- 확장 가능
- 캡슐화
- 독립적

# SFC

> Component in Vue

- Vue에서 말하는 component란?

  - 이름이 있는 재사용 가능한 Vue instance

- Vue instance란?

  - new Vue()로 만든 인스턴스

> SFC(Single File Component)

- 하나의 .vue파일이 하나의 Vue instance 이고 하나의 컴포넌트.

> 정리

- .vue라는 확장자에서 HTML, CSS, JS 관리
- 이 파일을 vue instance, vue component라고 함
- Vue CLI 가 component based하게 사용하도록 도와줌

# Vue component

> Vue component 구조

- 컴포넌트들이 tree 구조를 이루어 하나의 페이지를 만듦
- root 에 해당하는 최상단의 component가 App.vue
- App.vue를 index.html과 연결
- 결국 index.html 파일 하나만을 rendering

  - 이게 SPA

# Data in components

- 컴포넌트는 부모-자식 관계를 가지고 있으므로 부모 자식 관계만 데이터를 주고받게 하자
- 데이터의 흐름 파악 용이
- 유지보수 쉬워짐

- 부모 > 자식 : pass props
- 자식 > 부모 : emit event

# Pass Props

> Pass Props

- 요소의 속성을 사용하여 데이터 전달
- 부모 컴포넌트의 정볼르 전달하기 위한 사용자 지정 특성
- props를 명시적으로 선언
- 정적인 데이터를 전달하는 경우 static props라고 명시하기도 함
- prop-data-name="value"

  - 속성의 키 값은 kebab-case

- 받는 쪽에서 데이터를 명시적으로 작성
- type 과 함께 명시

> Pass Props convention

- 부모에서 넘겨주는 props

  - kebab-case

- 자식에서 받는 props

  - camelCase

> Dynamic props

- 변수를 동적으로 바인딩

> 컴포넌트의 data 함수

- 각 vue 인스턴스는 같은 data 객체를 공유하므로 새로운 data 객체를 반환하여 사용해야 함

> Pass Props

- 앞의 키 값(dynamic-props)란 이름으로 뒤의 ""안에 오는 데이터(dynamicProps)를 전달하겠다는 뜻

> 단방향 데이터 흐름

- 하위 컴포넌트에서 prop을 변경하려고 하면 안됨

# Emit Event

- 이벤트 발생

1. 데이터를 이벤트 리스너의 콜백함수의 인자로 전달
2. 상위 컴포넌트는 해당 이벤트를 통해 데이터 받음

> $emit

- $emit 메서드를 통해 부모 컴포넌트에 이벤트 발생

  - $emit("event-name")

- $

  - js는 변수에 _, $ 두 개의 특수문자 사용 가능
  - 기존 변수 메서드들과 겹치지 않게 하기 위해

> Emit Event

1. 자식 컴포넌트에 버튼을 만들고 클릭 이벤트 추가
2. $emit 을 통해 부모 컴포넌트에게 이벤트 트리거

- emit 된 이벤트를 상위 컴포넌트에서 청취 후 핸들러 함수 실행

> emit with data

- 이벤트를 발생시킬 때 인자로 데이터 전달 가능
- 부모 컴포넌트 핸들러 함수의 인자로 사용 가능

> 흐름 정리

1. 자식 컴포넌트에 있는 버튼 클릭 이벤트로 핸들러 함수 호출
2. 호출된 함수에서 $emit을 통해 부모 컴포넌트에 이벤트 발생

   - 데이터 함께 전달

3. 이벤트를 청취하여 연결된 핸들러 함수 호출, 인자로 전달된 데이터 포함
4. 호출된 함수에서 실행

> 정리

- 자식 컴포넌트에서 부모 컴포넌트로 이벤트 발생

  - 이벤트에 데이터를 담아 전달 가능

- 부모 컴포넌트에서는 자식 컴포넌트의 이벤트 청취

  - 전달받은 데이터는 이벤트 핸들러 함수의 인자로

> pass props / emit event 컨벤션

- props 

  - 상위 > 하위 흐름에서 html 요소로 : kebab-case
  - 하위에서 받을 때 javascript에서 : camelCase

- emit

  - emit 이벤트를 발생시키면 html 요소가 이벤트 청취 : kebab-case
  - 메서드, 변수명 등은 javascript에서 : camelCase

---

# Vuex

# State Management

> 상태 관리

- app이 가지고 있는 data
- 여러 개의 component를 조합해서 하나의 App을 만들고 있음
- 각 component는 독립적이기 때문에 각각의 상태(data)를 가짐
- 여러 개의 component가 같은 상태를 유지할 필요가 있음

> Pass Props & Emit Event

- 같은 데이터를 공유하고 있음
- 그러나 component의 중첩이 깊어지면 데이터 전달이 쉽지 않음

> Centralized Store

- 중앙 저장소(store)에 데이터를 모아서 상태 관리
- 중앙에서 데이터를 얻고 변경
- component들은 데이터의 변화에 반응하여 새로 변경된 데이터 반영

> Vuex

- 데이터가 예측 가능한 방식으로만 변경될 수 있도록 하는 규칙 설정, Vue의 반응성을 효율적으로 사용하는 상태 관리 기능 제공

# Vuex 시작

> 프로젝트 with vuex

- vue create vuex-app
- vue add vuex

> 1. State

- vue 인스턴스의 data
- 중앙에서 관리하는 모든 상태 정보
- $store.state로 state 데이터에 접근

> 2. Mutations

- 실제로 state 를 변경하는 유일한 방법
- Mutations에서 호출되는 handler는 동기적이어야 함

  - 비동기 로직으로 mutations를 사용해서 state를 변경하는 경우 state의 변화의 시기를 특정할 수 없기 때문

- 첫 번째 인자로 state, commit()메서드로 호출됨

> 3. Actions

- mutations와 비슷하지만 비동기 작업을 포함할 수 있다는 차이
- commit()메서드로 mutations를 호출하여 state 변경
- context 객체를 인자로 받음. 이 객체를 통해 store.js의 모든 요소와 메서드에 접근할 수 있음
- component 에서 dispatch() 메서드에 의해 호출됨

> Mutations and Actions

- mutations

  - state를 변경

- actions

  - 나머지

4. Getters

- vue 인스턴스의 computed
- state를 활용하여 계산된 값을 얻고자 할때 사용. 원본 데이터는 건들지 않고
- computed와 마찬가지로 getters의 결과는 캐시되며, 종속값이 변경된 경우에만 재계산
- 첫 번째 인자로 state, 두 번째 인자로 getter

> 정리

- state

  - 중앙에서 관리하는 모든 상태 정보

- mutations

  - state 를 변경하기 위한 methods

- actions

  - 비동기 작업이 포함될 수 있는 methods
  - state 를 변경하는 것 외의 모든 로직 진행

- getters

  - state 를 활용해 계산한 새로운 변수 값

- component에서 데이터를 조작하기 위한 데이터의 흐름

  - component > actions > mutations > state

- component에서 데이터를 사용하기 위한 데이터의 흐름

  - state > getters > component

# Lifecycle Hooks

> Lifecycle Hooks

- 각 Vue 인스턴스는 생성과 소멸의 과정 중 단계별 초기화 과정을 거침
- 각 단계가 트리거가 되어 특정 로직 실행 가능
- 이를 Lifecycle Hooks라고 함

> created

- Vue instance가 생성된 후
- data, computed 등 설정 완료된 상태
- mount 되지 않아 요소에 접근 불가

> mounted

- Vue instance 요소가 mount 된 후 호출됨
- mount 된 요소를 조작할 수 있음
- created의 경우, mount 되기 전이기 때문에 DOM에 접근할 수 없으므로 동작하지 않음

> updated

- 데이터가 변경되어 DOM에 변화를 줄때 호출

> Lifecycle Hooks 특징

- instance마다 가지고 있음
- 부모 컴포넌트의 mounted hook이 실행 되었다고 해서 자식이 mount 된 것이 아니고 부모 컴포넌트가 updated hook이 실행 되었다고 해서 자식이 updated 된 것이 아님

  - 부착 여부가 부모-자식 관계에 따라 순서를 가지고 있지 않은 것

---

# UX, UI

> UX

- 유저와 가장 가까이에 있는 분야, 데이털르 기반으로 유저를 조사하고 분석해서 개발자, 디자이너가 이해할 수 있게 소통
- 유저가 느끼는 느낌, 태도, 행동을 디자인

> 좋은 UX를 설계하기 위해서는

- 사람들의 마음과 생각을 이해, 정리

> UI(User Interface)

- 유저에게 보여지는 화면을 디자인
- UX를 고려한 디자인을 반영

> Interface

- 서로 다른 두 개의 시스템, 장치 사이에서 정보나 신호를 주고받는 경우의 접점

  - 사용자가 기기를 쉽게 동작시키는데 도움을 주는 시스템

> 좋은 UI를 설계하기 위해서는

- 사용자가 보다 쉽고 편리하게 사용할 수 있도록 하는 부분까지 고려되어야 함
- 통일된 디자인을 위한 디자인 시스템, 소통을 위한 중간 산출물, 프로토타입 등 필요
- 협업이 중요

# Prototyping

> Software prototyping

- 애플리케이션의 프로토타입을 만드는 것
- 개발중인 소프트웨어 프로그램의 완성되기 전 버전을 만드는 것
- 중간마다 현재 상태를 체크하는 과정

> Prototyping Tool 

- Figma 가 많이 사용되는 중

> Figma

- 협업에 중점

> Why Figma?

- 웹 기반

  - 매우 가벼운 환경, 모든 작업 내역이 웹에 저장

- 실시간으로 협업
- 직관적이고 다양한 툴
- 다양한 플러그인
- 대부분 무료

> 프로젝트 시작 전

- 개발부터 시작하지 말고 충분한 기획
- 완성하고자 하는 대략적인 모습 그리기(프로토타입)
- 이러한 과정을 통해서 빠진 화면이나 API 등 확인

# Vue Router

# Routing

> Routing

- 네트워크에서 경로를 선택하는 프로세스
- 웹 서비스에서 라우팅

  - 유저가 방문한 URL에 대해 적절한 결과를 응답하는 것

> Routing in SSR

- Server가 모든 라우팅을 통제
- URL로 요청이 들어오면 응답으로 완성된 HTML 제공
- 결론적으로, Routing(URL)에 대한 결정권을 서버가 가짐

> Routing in SPA / CSR

- 서버는 하나의 HTML만 제공
- 이후 모든 동작은 하나의 HTML 문서 위에서 JavaScript 코드 활용

  - DOM을 그리는데 추가적인 데이터가 있다면 axios 와 같은 AJAX 요청을 보낼 수 있는 도구를 사용하여 데이터를 가져오고 처리

- 즉 하나의 URL

> Why routing?

- Routing이 없다면

  - 유저가 URL을 통한 페이지 변화 감지 X
  - 페이지가 무엇을 렌더링 중인지에 대한 상태를 알 수 없음

    - 새로 고침 시 처음 페이지로
    - 링크 공유할 시 처음 페이지만 공유 가능

  - 뒤로가기 기능 사용 불가

# Vue Router

> Vue Router

- 라우트(routes)에 컴포넌트를 매핑한 후 어떤 URL에서 렌더링 할 지 알려줌

  - SPA를 MPA처럼 URL을 이동하면서 사용 가능

- MPA

  - 여러 개의 페이지로 구성된 애플리케이션
  - SSR 방식

> History mode

- 브라우저의 History API를 활용한 방식

  - 새로고침 없이 URL 이동 기록을 남길 수 있음

> router-link

- a 태그와 비슷한 기능 > URL 이동

  - routes 에 등록된 컴포넌트와 매핑됨
  - 히스토리 모드에서 router-link는 클릭 이벤트를 차단하여 a태그와 달리 브라우저가 페이지를 다시 로드하지 않도록 함

- 목표 경로는 to 속성으로
- 기능에 맞게 HTML 에서 a 태그로 rendering 되지만, 필요에 따라 다른 태그로 바꿀 수 있음

> router-view

- 주어진 URL 에 대해 일치하는 컴포넌트를 렌더링 하는 컴포넌트
- 실제 component가 DOM에 부착되어 보이는 자리 의미
- block tag와 비슷

> src/Views

- router-view에 들어갈 component 작성
- 기능은 같음
- views

  - routes 에 매핑되는 컴포넌트
  - view로 끝나도록 만드는 것 권장

- components

  - routes에 매핑된 컴포넌트의 하위 컴포넌트를 모아두는 폴더

> 주소를 이동하는 2가지 방법

1. 선언적 방식 네비게이션

   - router-link의 to 속성으로 주소 전달

     - routes에 등록된 주소와 매핑된 컴포넌트로 이동
     - v-bind사용

2. 프로그래밍적 방식 네비게이션

   - 인스턴스 내부에서 $router로 접근할 수 있음
   - 다른 URL로 이동하려면 this.$router.push

> Dynamic Route Matching

- 동적 인자 전달

  - URL의 특정 값을 변수처럼 사용할 수 있음

- $route.params로 변수에 접근 가능

> lazy-loading

- 모든 파일을 한 번에 로드하려고 하면 모든 걸 다 읽는 시간이 매우 오래 걸림
- 미리 로드를 하지 않고 특정 라우트에 방문할 때 매핑된 컴포넌트의 코드를 로드하는 방식을 활용할 수 있음

  - 최초 로드 시간 빨라짐
  - 당장 사용하지 않을 컴포넌트는 먼저 로드하지 않음

# Navigation Guard

> 네비게이션 가드

- Vue router를 통해 특정 URL에 접근할 때 다른 url로 redirect 하거나 해당 URL로 접근을 막는 방법

> 네비게이션 가드 종류

- 전역 가드

  - 애플리케이션 전역에서 동작

- 라우터 가드

  - 특정 URL 에서만 동작

- 컴포넌트 가드

  - 라우터 컴포넌트 안에 정의

# 전역 가드

> Global Before Guard

- 다른 url 주소로 이동할 때 항상 실행
- router.beforeEach()
- 3개의 인자를 받음

  - to : 이동할 URL 정보가 담긴 Route 객체
  - from : 현재 URL
  - next : 지정한 URL로 이동하기 위해 호출하는 함수

    - 한 번만 호출되어야 함
    - 기본적으로 to 에 해당하는 URL로 이동

- next()가 호출되기 전까지 화면이 전환되지 않음

# 라우터 가드

> 라우터 가드

- 특정 route 에 대해서만 가드를 설정하고 싶을 때
- beforeEnter()

  - route에 진입했을 때 실행
  - 라우터를 등록한 위치에 추가

# 컴포넌트 가드

> 컴포넌트 가드

- 특정 컴포넌트 내에서 가드를 지정하고 싶을 때 사용
- beforeRouteUpdate()

  - 해당 컴포넌트를 렌더링하는 경로가 변경될 때 실행

# 404 Not Found

> 404 Not Found

- 요청한 리소스가 존재하지 않는 경우

  - 모든 경로에 대해서 404 page redirect
  - routes 최하단부에 작성

- 메세지를 바꿀 수도 있지만 404 페이지로 이동하도록

