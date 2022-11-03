# 20221103 TIL

# Vue CLI

> Vue CLI Quick Start

- 설치

```bash
$ npm install -g @vue/cli
```

- 프로젝트 생성

  - vscode terminal 내에서

  ```bash
  $ vue create vue-cli
  ```

- vue 버전 선택

- 프로젝트 생성 성공

- 출력된 명령어

  - 프로젝트 디렉토리로 이동

  ```bash
  $ cd vue-cli
  ```

  - 프로젝트 실행

  ```bash
  $ npm run serve
  ```

## Vue CLI 프로젝트 구조

> node_modules

- node.js 환경의 여러 의존성 모듈

> node_modules - Babel

- 자바스크립트의 ES6+ 코드를 구버전으로 번역/변환 해주는 도구

> node_modules - Webpack

- 모듈간의 의존성 문제를 해결하기 위한 도구
- 프로젝트에 필요한 모든 모듈을 매핑하고 내부적으로 종속성 그래프를 빌드함

> Module

- 개발하는 애플리케이션의 크기가 커지고 복잡해지면 파일 하나에 모든 기능을 담기가 어려워짐
- 따라서 파일을 여러개로 분리하여 관리 -> 분리된 파일이 각각 모듈
- 모듈은 대개 기능 단위로 분리, 클래스 하나 혹은 특정한 목적을 가진 복수의 함수로 구성된 라이브러리 하나로 구서
- 여러 모듈 시스템

  - ESM(ECMA Script Module), AMD, CommonJS, UMD

> Module 의존성 문제

- 모듈의 수가 많아지고 라이브러리, 모듈 간의 의존성(연결성)이 깊어지면서 특정한 곳에서 발생한 문제가 어떤 모듈 간의 문제인지 파악하기 어려움

  - Webpack은 이 모듈 간의 의존성 문제를 해결하기 위해 등장

> Bundler

- 모듈 의존성 문제를 해결해주는 작업이 Bundling
- 이러한 일을 해주는 도구가 Bundler, Webpack은 다양한 Bundler 중 하나

> package.json

- 프로젝트의 종속성 목록과 지원되는 브라우저에 대한 구성 옵션 포함

> package-lock.json

- node_modules에 설치되는 모듈과 관련된 모든 의존성을 설정 및 관리
- 협업 및 배포 환경에서 정확히 동일한 종속성을 설치하도록 보장하는 표현
- 사용 할 패키지의 버전을 고정
- 개발 과정 간의 의존성 패키지 충돌 방지

> public/index.html

- Vue 앱의 뼈대가 되는 html 파일
- Vue 앱과 연결될 요소가 있음

> src/

- src/assets

  - 정적 파일 저장하는 디렉토리

- src/components

  - 하위 컴포넌트들이 위치

- src/App.vue

  - 최상위 컴포넌트
  - public/index.html과 연결됨

- src/main.js

  - webpack이 빌드를 시작할 때 가장 먼저 불러오는 entry point
  - public/index.html과 src/App.vue를 연결시키는 작업이 이루어지는 곳
  - Vue 전역에서 활동할 모듈을 등록할 수 있는 파일

# SFC

## Component

> Component

- UI를 독립적이고 재사용 가능한 조각들로 나눈 것

  - 기능별로 분화한 코드 조각

- CS에서는 다시 사용할 수 있는 범용성을 위해 개발된 소프트웨어 구성 요소를 의미
- 하나의 app을 구성할 때 중첩된 컴포넌트들의 tree로 구성하는 것이 보편적

  - Vue에서는 src/App.vue를 root node로 하는 tree의 구조를 가짐

- 컴포넌트는 유지보수를 쉽게, 재사용성의 측면에서도 강력한 기능 제공

> Component based architecture 특징

- 관리 용이

  - 유지보수 비용 감소

- 재사용성
- 확장 가능
- 캡슐화
- 독립적

# SFC

> component in Vue

- Vue 에서 말하는 component란?

  - 이름이 있는 재사용 가능한 Vue instance

- 그렇다면 Vue instance란?

  - 앞서 수업에서 사용한 new Vue()로 만든 인스턴스

> SFC(Single File Component)

- 하나의 .vue 파일이 하나의 Vue instance이고, 하나의 컴포넌트

  - 즉, Single File Component

- Vue instance에서는 HTML, CSS, JavaScript 코드를 한번에 관리

  - 이 Vue instance를 기능 단위로 작성하는 것이 핵심!

- 컴포넌트 기반 개발의 핵심 기능

> 정리

- HTML, CSS, JavaScript를 .vue라는 확장자를 가진 파일 안에서 관리하며 개발
- 이 파일을 Vue instance, 또는 Vue component라고 하며, 기능 단위로 작성
- Vue CLI가 Vue를 Component based하게 사용하도록 도와줌

# Vue component

- 템플릿(HTML)

  - HTML의 body 부분
  - 눈으로 보여지는 부분
  - 다른 컴포넌트를 HTML 요소처럼 추가 가능

- 스크립트(JavaScript)

  - JavaScript 코드가 작성되는 곳
  - 컴포넌트 정보, 데이터, 메서드 등 vue 인스턴스를 구성하는 대부분이 작성됨

- 스타일(CSS)

  - CSS가 작성되며 컴포넌트의 스타일을 담당

> Vue component 구조 정리

- 컴포넌트들이 tree 구조를 이루어 하나의 페이지를 만듦
- root에 해당하는 최상단의 component가 App.vue
- 이 App.vue를 index.html과 연결
- 결국 index.html 파일 하나만들 rendering

  - 이게 SPA

## Vue component 실습

> MyComponent.vue

1. src/components/ 안에 생성
2. script에 이름 등록
3. template에 요소 추가

   - 비어있으면 안됨
   - 해당 요소 안에 추가 요소를 작성해야 한다.

> component 등록 3단계

1. 불러오기
2. 등록하기
3. 보여주기

> component 등록 - 불러오기

- import {instance name} from {위치}
- instance name은 instance 생성 시 작성한 name
- @는 src의 shortcut
- .vue 생략 가능

> component 등록 - 등록하기

- App.vue에 components에 등록하기

> component 등록 - 보여주기

- 닫는 태그만 있는 요소처럼 사용

> 자식 컴포넌트 작성

- MyComponent의 자식 컴포넌트를 만들어보자
- 자식 관계를 표현하기 위해 기존 MyComponent에 간단한 border 추가
- src/components/ 안에 MyChild.vue 생성
- MyComponent에 MyChild 등록

# Data in components

> Data in components

- 한 페이지 내에서 같은 데이터를 공유해야 함

  - 하지만 페이지들은 component로 구분이 되어있음

- MyComponent에 정의된 data를 MyChild에서 사용하려면?

- 컴포넌트는 부모-자식 관게를 가지고 있으므로, 부모-자식 관계만 데이터를 주고 받게 하자

- 데이터의 흐름을 파악하기 용이
- 유지보수 쉬워짐

> pass props and emit event

- 부모 > 자식으로의 데이터 흐름

  - pass props의 방식

- 자식 > 부모로의 데이터 흐름

  - emit event 방식

# Pass Props

> Pass Props

- 요소의 속성(property)을 사용하여 데이터 전달
- props는 부모(상위) 컴포넌트의 정보를 전달하기 위한 사용자 지정 특성
- 자식(하위) 컴포넌트는 props 옵션을 사용하여 수신하는 props를 명시적으로 선언해야 함

> props in HelloWorld

- Vue CLI를 설치할 때 만들어 주었던 App.vue의 HelloWorld 컴포넌트를 살펴보면 msg라는 property가 작성되어 있음

- HelloWorld.vue에서 msg를 사용한 것을 확인

> props in HelloWorld 정리

- App.vue의 HelloWorld요소에 msg="~"라는 property를 설정하였고, 하위 컴포넌트인 HelloWorld는 자신에게 부여된 msg property를 template에서 {{ msg }}의 형태로 사용한 것

> Pass Props

- 부모 -> 자식으로의 데이터 전달 방식을 pass props라고 한다.
- 정적인 데이터를 전달하는 경우 static props라고 명시하기도 함
- 요소에 속성을 작성하듯이 사용 가능하며, prop-data-name="value"의 형태로 데이터를 전달

  - 이때 속성의 키 값은 kebab-case 사용

```js
// HelloWorld.vue

<script>
export default {
  name: 'HelloWorld',
  props: {
    msg: String
  }
}
</script>
```

- Prop 명시
- 데이터를 받는 쪽, 즉 하위 컴포넌트에서도 props에 대해 명시적으로 작성 해주어야 함
- 전달받은 props를 type과 함께 명시
- 컴포넌트를 문서화할 뿐만 아니라, 잘못된 타입이 전달하는 경우 브라우저의 자바스크립트 콘솔에서 사용자에게 경고

> MyComponent to MyChild

```html
// MyComponent.vue

<template>
  <div class='border'>
    <h1>This is my component</h1>
    <MyChild static-props="component에서 child로"/>
  </div>
</template>
```

```html
// MyChild.vue

<template>
  <div>
    <h3>This is child component</h3>
    <p>{{ staticProps }}></p>
  </div>
</template>

<script>
export default {
  name: 'MyChild',
  props: {
    staticProps: String,
  }
}
</script>
```

## Pass Props convention

- 부모에서 넘겨주는 props

  - kebab-case(HTML속성명은 대소문자를 구분하지 않기 때문)

- 자식에서 받는 props

  - camelCase

- 부모 템플릿(html)에서 kebab-case로 넘긴 변수를 자식의 스크립트(vue)에서 자동으로 camelCase로 변환하여 인식함

> Dynamic props

- 변수를 props로 전달할 수 있음
- v-bind directive 를 사용해 데이터를 동적으로 바인딩
- 부모 컴포넌트의 데이터가 업데이트 되면 자식 컴포넌트로 전달되는 데이터 또한 업데이트 됨

> Dynamic props 실습

```html
// MyComponent.vue

<template>
  <div class='border'>
    <h1>This is my component</h1>
    <MyChild
      static-props="component에서 child로"
      :dynamic-props="dynamicProps"
    />
  </div>
</template>

<script>
export default {
  ...
  data: function() {
    return {
      dynamicProps: "It's in data"
    }
  }
}
</script>
```

```html
// MyChild.vue

<template>
  <div>
    <h3>This is child component</h3>
    <p>{{ staticProps }}</p>
    <p>{{ dynamicProps }}</p>
  </div>
</template>

<script>
export default {
  name: 'MyChild',
  props: {
    staticProps: String,
    dynamicProps: String,
  }
}
</script>
```

> 컴포넌트의 data 함수

- 각 vue 인스턴스는 같은 data 객체를 공유하므로 새로운 data 객체를 반환(return)하여 사용해야 함

> Pass Props

- :dynamic-props="dynamicProps"는 앞의 key값(dynamic-props)이란 이름으로 뒤의 " " 안에 오는 데이터(dynamicProps)를 전달하겠다는 뜻
- 즉 :my-props="dynamicProps"로 데이터를 넘긴다면 자식 컴포넌트에서 myProps로 데이터를 받아야 함

- v-bind로 묶여 있는 " "안의 구문은 javascript의 구문으로 볼 수 있음

  - 따라서 dynamicProps라고 하는 변수에 대한 data를 전달할 수 있는 것

- 그렇다면, 숫자를 props로 전달하기 위해서 다음 두 방법 중 어떤 게 맞을까?

```html
// 1
<SomeComponent num-props="1"/>

// 2
<SomeComponent :num-props="1"/>
```

- 첫 번째 방식은 static props로 string으로써의 "1"을 전달
- 두 번째 방식은 dynamic props로 숫자로써의 1을 전달

> 단방향 데이터 흐름

- 모든 props는 부모에서 자식으로, 즉 아래로 단방향 바인딩을 형성
- 부모 속성이 업데이트 되면 자식으로 흐르지만 반대 방향은 아님

  - 부모 컴포넌트가 업데이트 될 때마다 자식 컴포넌트의 모든 prop들이 최신 값으로 새로고침 됨

- 목적

  - 하위 컴포넌트가 실수로 상위 컴포넌트 상태를 변경하여 앱의 데이터 흐름을 이해하기 힘들게 만드는 것을 방지

- 하위 컴포넌트에서 prop을 변경하려고 시도해서는 안되며 그렇게 하면 Vue는 콘솔에서 경고를 출력함

# Emit Event

> Emit Event

- 부모 컴포넌트에서 자식 컴포넌트로 데이터를 전달할 때는 이벤트를 발생 시킴
- 이벤트를 발생시키는 게 어떻게 데이터를 전달하는 것이냐?

  1. 데이터를 이벤트 리스너의 콜백 함수의 인자로 전달
  2. 상위 컴포넌트는 해당 이벤트를 통해 데이터를 받음

> $emit

- $emit 메서드를 통해 부모 컴포넌트에 이벤트를 발생

  - $emit('event-name') 형식으로 사용하며 부모 컴포넌트에 event-name이라는 이벤트가 발생했다는 것을 알림
  - 마치 사용자가 마우스 클릭을 하면 click 이벤트가 발생하는 것처럼 $emit('event-name')가 실행되면 event-name 이벤트가 발생하는 것

> Emit Event

1. 자식 컴포넌트에 버튼을 만들고 클릭 이벤트를 추가
2. $emit을 통해 부모 컴포넌트에게 child-to-parent 이벤트를 트리거

```html
// MyChild.vue

<template>
  <div>
    ...
    <button @click="ChildToParent">클릭!</button><br>
  </div>
</template>

<script>
export default {
  ...
  methods: {
    ChildToParent: function() {
      this.$emit('child-to-parent')
    }
  }
}
</script>
```

- emit 된 이벤트를 상위 컴포넌트에서 청취 후 핸들러 함수 실행

```html
// MyComponent.vue

<template>
  <div class='border'>
    <h1>This is my component</h1>
    <MyChild
      ...
      @child-to-parent="parentGetEvent"
      />
  </div>
</template>

<script>
export default {
  ...
  methods: {
    parentGetEvent: function() {
      console.log("자식 컴포넌트에서 발생한 이벤트!")
    }
  }
}
</script>
```

> Emit Event 흐름 정리

1. 자식 컴포넌트에 있는 버튼 클릭 이벤트를 청취하여 연결된 핸들러 함수(ChildToParent) 호출
2. 호출된 함수에서 $emit을 통해 상위 컴포넌트에 이벤트(child-to-parent) 발생
3. 상위 컴포넌트는 자식 컴포넌트가 발생시킨 이벤트(child-to-parent)를 청취하여 연결된 핸들러 함수(parentGetEvent) 호출

> emit with data

- 이벤트를 발생(emit) 시킬 때 인자로 데이터를 전달 가능

```html
// MyChild.vue

<template>
  <div>
    ...
    <button @click="ChildToParent">클릭!</button><br>
  </div>
</template>

<script>
export default {
  ...
  methods: {
    ChildToParent: function () {
      this.$emit('child-to-parent', 'child data')
    }
  }
}
</script>
```

- 이렇게 전달한 데이터는 이벤트와 연결된 부모 컴포넌트의 핸들러 함수의 인자로 사용 가능

```html
// MyComponent.vue

<template>
  <div class="border">
    <h1>This is my component</h1>
    <MyChild
      ...
      @child-to-parent="parentGetEvent"   
      />
  </div>
</template>

<script>
export default {
  ...
  methods: {
    parentGetEvent: function (inputData) {
      console.log("자식 컴포넌트에서 발생한 이벤트!")
      console.log(`child component로부터 ${inputData}를 받음!`)
    }
  }
}
</script>
```

> emit with data 흐름 정리

1. 자식 컴포넌트에 있는 버튼 클릭 이벤트를 청취하여 연결된 핸들러 함수(ChildToParent) 호출
2. 호출된 함수에서 $emit을 통해 부모 컴포넌트에 이벤트(child-to-parent)를 발생

   - 이벤트에 데이터(child data)를 함께 전달

3. 부모 컴포넌트는 자식 컴포넌트의 이벤트(child-to-parent)를 청취하여 연결된 핸들러 함수(parentGetEvent) 호출, 함수의 인자로 전달된 데이터(child data)가 포함되어 있음
4. 호출된 함수에서 console.log(~child data~) 실행

> emit with dynamic data

- pass props와 마찬가지로 동적인 데이터도 전달 가능
- 자식 컴포넌트에서 입력받은 데이터를 부모 컴포넌트에게 전달하여 출력해보자

```html
// MyChild.vue

<template>
  <div>
    ...
    <input
      type="text"
      v-mode="childInputData"
      @keyup.enter="childInput"
    >
  </div>
</template>

// MyChild.vue

<script>
export default {
  ...
  data: function() {
    return {
      childInputData: null,
    }
  },
  methods: {
    ...
    childInput: function () {
      this.$emit('child-input', this.childInputData)
      this.childInputData = ""
    }
  },
}
</script>
```

```html
// MyComponent.vue

<template>
  <div class='border'>
    <h1>This is my component</h1>
    <MyChild
      ...
      @child-input="getDynamicData"
    />
  </div>
</template>

// MyComponent.vue

<script>
import MyChild from '@/components/MyChild'

export default {
  ...
  methods: {
    ...
    getDynamicData: function (inputData) {
      console.log(`child component로부터 ${inputData}를 입력받음!`)
    }
  }
}
</script>
```

> emit with dynamic data 흐름 정리

1. 자식 컴포넌트에 있는 keyup.enter 이벤트를 청취하여 연결된 핸들러 함수(ChildInput) 호출
2. 호출된 함수에서 $emit을 통해 부모 컴포넌트에 이벤트(child-input)를 발생

   - 이벤트에 v-model로 바인딩 된 입력받은 데이터를 전달

3. 상위 컴포넌트는 자식 컴포넌트의 이벤트(child-input)를 청취하여 연결된 핸들러 함수(getDynamicData) 호출, 함수의 인자로 전달된 데이터가 포함되어 있음
4. 호출된 함수에서 console.log(~입력받은데이터~) 실행

## 정리

- 자식 컴포넌트에서 부모 컴포넌트로 이벤트를 발생시킴

  - 이벤트에 데이터를 담아 전달 가능

- 부모 컴포넌트에서는 자식 컴포넌트의 이벤트를 청취

  - 전달받은 데이터를 이벤트 핸들러 함수의 인자로 사용

> pass props / egmit event 컨벤션

- 아니 그래서 언제는 kebab-case고 언제는 camelCase야?

  - HTML 요소에서 사용할 때는 kebab-case
  - JavaScript 요소에서 사용할 때는 camelCase

- props

  - 상위 -> 하위 흐름에서 HTML 요소로 내려줌 : kebab-case
  - 하위에서 받을 때 JavaScript에서 받음 : camelCase

- emit

  - emit 이벤트를 발생시키면 HTML 요소가 이벤트를 청취함 : kebab-case
  - 메서드, 변수명 등은 JavaScript에서 사용함 : camelCase

