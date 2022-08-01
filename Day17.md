# 20220801 TIL

## Web

### HTML & CSS

> 웹 사이트의 구성 요소

- 웹 사이트란 웹 페이지(문서)들의 모음
- 여러 가지 정보를 담고 있으며, 클릭하면 다른 웹페이지로 이동하는 링크들이 있음. 링크를 통해 여러 웹 페이지를 연결한 것을 웹 사이트라고 함.
- HTML >> 구조 ex. 건물
- CSS >> 표현 ex. 인테리어
- Javascript >> 동작(처리, 계산) ex.엘베, IOThome

> 웹 사이트와 브라우저

- 웹 사이트는 브라우저를 통해 동작함
- 브라우저마다 동작이 약간씩 달라서 문제가 생기는 경우가 많음(파편화)
- 해결책으로 웹 표준 등장
- 크롬, 웨일, 엣지, 파이어폭스 등
- Internet Explorer >> deprecated(사용하지 않음)
- 결론 : msword, 한컴문서 등이 있어야 .hwp, .doc를 실행한다. 따라서 HTML 문서를 실행하기 위해서 브라우저가 필요하다.

> 웹 표준

- 웹에서 표준적으로 사용되는 기술이나 규칙
- 어떤 브라우저든 웹 페이지가 동일하게 보이도록 함(크로스 브라우징)
- 실행기도 표준(기계), 문서도 표준(선, 폰트 등)이 있다.

### HTML

> HTML

- Hyper Text Markup Language

> Hyper Text란?

- 참조(하이퍼링크)를 통해 사용자가 한 문서에서 다른 문서로 즉시 접근할 수 있는 텍스트

> Markup Language

- 태그 등을 이용하여 문서나 데이터의 구조를 명시하는 언어
  - 예 - HTML, Markdown

> HTML 이란?

- 웹 페이지를 작성(구조화)하기 위한 언어

> HTML 스타일 가이드

- 마크업 스타일 가이드(2 space)

### HTML 기본 구조

> HTML 기본 구조

- html : 문서의 최상위 요소
- head : 문서 메타데이터 요소 (실제 사이트에 관련된 내용)
  - 문서제목, 인코딩, 스타일, 외부파일 로딩 등
  - 일반적으로 브라우저에 나타나지 않음
- body : 문서 본문 요소
  - 실제 화면 구성

> head 예시

- title : 상단 타이틀
- meta : 문서 레벨 메타데이터 요소
- link : 외부 리소스 연결
- script : 스크립트 요소
- style : css 직접 작성

> head 예시 : Open Graph Protocol

- 메타 데이터를 표현하는 새로운 규약
  - HTML 문서의 메타 데이터를 통해 문서의 정보 전달
  - 메타정보에 해당하는 제목, 설명 등을 쓸 수 있도록 정의

> 요소

- HTML 요소는 시작 태그와 종료 태그, 태그사이에 위치로 구성
  - 요소는 태그로 컨텐츠(내용)을 감싸는 것으로 그 정보의 성격과 의미 정의
  - 내용이 없는 태그도 존재(닫는태그 X)
    - br, hr, img, input, link, meta
- 요소는 중첩될 수 있음
  - 요소의 중첩을 통해 하나의 문서를 구조화
  - 여는 태그와 닫는 태그의 쌍을 잘 확인
    - 오류를 반환하는 것이 아닌 레이아웃이 깨진 상태로 출력 << 디버깅이 힘들어짐.

> 속성(attribute)

- 태그별로 사용할 수 있는 속성은 다르다.
- 속성을 통해 태그의 부가적인 정보 설정 가능
- 요소는 속성을 가질 수 있으며, 경로나 크기와 같은 추가적인 정보 제공
- 보통 이름과 값이 하나의 쌍으로 존재
- 태그와 상관없이 사용 가능한 속성 있음

> HTML Global Attribute

- 모든 HTML 요소가 사용가능한 대표적인 속성

> 시맨틱 태그

- HTML 태그가 특정 목적, 역할 및 의미적 가치를 가지는 것
  - h1 태그는 최상위 제목
- Non semantic 요소로는 div, span 등

> 시맨틱 태그를 사용해야 하는 이유

- 의미론적 마크업
  - 개발자, 사용자 뿐만 아니라 검색엔진 등에 의미있는 정보의 그룹을 태그로 표현
  - 구역 나누는 것 뿐만 아니라 의미를 가지는 태그들을 활용하기 위한 노력
  - 코드의 가독성 높이고 유지보수 쉽게함
  - 검색 엔진 최적화를 위해서 메타태그, 시멘틱 태그 등

> 텍스트 > 웹 사이트가 되는 과정

- 렌더링은 웹사이트 코드를 사용자가 보게 되는 웹 사이트로 바꾸는 과정

> DOM(Document Object Model) 트리

- 텍스트 파일인 HTML 문서를 브라우저에서 렌더링 하기 위한 구조
  - HTML 문서에 대한 모델을 구성
  - HTML 문서 내 각 요소에 접근 / 수정에 필요한 프로퍼티, 메서드 제공

### HTML 문서 구조화

> 인라인 / 블록 요소

- HTML 요소는 크게 인라인 / 블록 요소
- 인라인 요소는 글자처럼 취급
- 블록 요소는 한 줄 모두 사용

> form

- form 은 정보(데이터)를 서버에 제출하기 위해 사용하는 태그
- ex. 아이디, 비밀번호 사용자에게 입력받는 데이터
- form 기본 속성
  - action : form을 처리할 서버의 URL(데이터를 보낼 곳)
  - method : form을 제출할 때 사용할 HTTP 메서드(GET 혹은 POST)
  - enctype : method가 post인 경우 데이터의 유형
    - 파일 전송 시 사용

> input

- 다양한 타입을 가지는 입력 데이터 유형과 위젯이 제공됨
- input의 대표적인 속성
  - name : form control에 적용되는 이름
  - value : form control에 적요되는 값
  - required, readonly, autofocus 등등

> input label

- label을 클릭하여 input 자체의 초점을 맞추거나 활성화
- input 에 id 속성을, label에는 for 속성을 활용하여 상호 연관을 시킴
  - id : 태그 스페셜별명

> input 유형 - 일반

- 일반적으로 입력을 받기 위하여 제공되며 타입별로 HTML 기본 검증 혹은 추가 속성을 활용할 수 있음
  - text : 일반 텍스트
  - password : 입력시 값 보이지 않고 문자를 특수기호(\*)로 표현
  - email : 이메일 형식이 아닌 경우 form 제출 불가
  - number : min, max, step 속성을 활용하여 숫자 범위 설정 가능
  - file : accept 속성을 활용하여 파일 타입 지정 가능

> 정리

- 기본적 원리 태그 + 속성

### CSS

> CSS

- Cascading Style Sheets
- 스타일을 지정하기 위한 언어

> CSS 구문

```html
h1 { color: blue; font-size: 15px; }
```

- h1 : 선택자
- 스타일 변경

> CSS 정의 방법

- 인라인(inline)
- 내부 참조(embedding) - style
- 외부 참조(link file) - 분리된 CSS 파일

1. 인라인(inline)

   - 인라인을 쓰게 되면 실수가 잦아짐.(중복도 있고 찾기가 어려움)

2. 내부 참조(embedding) - style

   - 내부 참조를 쓰게 되면 코드가 너무 길어짐

3. 외부 참조(link file) - 분리된 CSS파일

   - 가장 많이 쓰는 방식

> CSS 시작하기전에

- 30~40개만 외우자

> CSS with 개발자 도구

### CSS Selectors

> 선택자(selectors) 유형

- 기본 선택자
  - 전체 선택자, 요소 선택자
  - 클래스 선택자, 아이디 선택자, 속성 선택자
- 결합자(Combinators)
  - 자손 결합자, 자식 결합자
  - 일반 형제 결합자, 인접 형제 결합자
- 의사 클래스/요소(Pseudo Class)

> CSS 선택자 정리

- 요소 선택자
  - HTML 태그를 직접 선택
- 클래스 선택자
  - 마침표(.)문자로 시작하며, 해당 클래스가 적용된 항목을 선택
- 아이디(id) 선택자
  - '#'문자로 시작하며, 해당 아이디가 적용된 항목을 선택
  - 일반적으로 하나의ㅏ 문서에 1번만 사용
  - 여러 번 사용해도 동작하지만, 단일 id를 사용하는 것을 권장

> CSS 적용 우선순위(cascading order)

- 범위가 좁을 수록 강하다.
- CSS 우선순위를 아래와 같이 그룹을 지어볼 수 있다.
  - (1) 중요도(Importance) - 사용시 주의
    - !important
  - (2) 우선 순위(Specificity)
    - 인라인 > id > class, 속성, pseudo-class > 요소, pseudo-element
  - (3) CSS 파일 로딩 순서

### CSS 기본 스타일

> 크기 단위

- px(픽셀)

  - 모니터 해상도의 한 화소인 '픽셀' 기준
  - 픽셀의 크기는 변하지 않기 때문에 고정적인 단위

- %

  - 백분율 단위
  - 가변적인 레이아웃에서 자주 사용

- em

  - (바로 위, 부모 요소에 대한) 상속의 영향 받음
  - 배수 단위, 요소에 지정된 사이즈에 상대적인 사이즈를 가짐

- rem
  - (바로 위, 부모 요소에 대한) 상속의 영향을 받지 않음
  - 최상위 요소(html)의 사이즈를 기준으로 배수 단위를 가짐

> 크기 단위(viewport)

- 웹 페이지를 방문한 유저에게 바로 보이게 되는 웹 컨텐츠의 영역
  - px는 브라우저의 크기를 변경해도 그대로
  - vw는 브라우저의 크기에 따라 크기가 변함

> 색상 단위

- 색상 키워드(background-color: red;)
  - 대소문자 구분 X
  - red, blue 와 같은 특정 색을 직접 글자로 나타냄
- RGB색상
  - 16진수 표기법 혹은 함수형 표기법으로 표현
- HSL색상
  - 색상, 채도, 명도를 통해 표현

> CSS 문서 표현

- 텍스트
  - 서체, 서체스타일
  - 자간, 단어간격, 행간 등
- 컬러, 배경
- 기타 HTML 태그별 스타일링

### CSS Selectors

> 결합자(Combinators)

- 자손결합자
  - selectorA 하위의 모든 selectorB요소
- 자식 결합자
  - selectorA 바로 아래의 selectorB요소
- 일반 형제 결합자
- 인접 형제 결합자

### Box model

> CSS 원칙 1

- 모든 요소는 네모(박스모델)이고, 위에서부터 아래로, 왼쪽에서 오른쪽으로 쌓인다.(좌상단에 배치)

> Box model

- 모든 HTML요소는 box 형태로 되어있음
- 하나의 박스는 네 부분(영역)으로 이루어짐
  - margin
  - border
  - padding
  - content

> Box model 구성(margin)

- 상하좌우

> Box model 구성(padding)

- 상하좌우

> Box model 구성(margin / padding)

- shorthand를 통해서 표현 가능하다.

> Box model 구성(border)

> box-sizing

- 기본적으로 모든 요소의 box-sizing은 content-box
  - padding을 제외한 순수 contents 영역만을 box로 지정
- 다만, 우리가 일반적으로 영역을 볼 때는 border까지의 너비를 100px 보는 것을 원함
  - 그 경우 box-sizing을 border-box로 설정

### CSS Display

> 대표적으로 활용되는 display

- display: block

  - 줄 바꿈이 일어나는 요소
  - 화면 크기 전체의 가로폭 차지
  - 블록 레벨 요소 안에 인라인 레벨 요소 들어갈 수 있음
  - 블록은 테트리스처럼 한줄 다 차지하면서 쌓인다.

- display: inline
  - 줄바꿈이 일어나지 않는 행의 일부 요소
  - content 너비만큼 가로폭 차지
  - width, height, margin-top, margin-bottom을 지정할 수 없다.
  - 상하 여백은 line-height로 지정한다.
  - 인라인은 글자다.

> 속성에 따른 수평 정렬

- margin-right: auto; : 오른쪽 여백
- margin-left: auto; : 왼쪽 여백
- margin-right: auto; margin-left: auto; : 양쪽여백

> display

- none : 보이지도 않고, 자리도 차지하지 않음
- hidden : 보이진 않지만 자리는 차지하고 있음

### CSS Position

> CSS position

- 문서 상에서 요소의 위치를 지정

1. relative: 상대위치
2. absolute: 절대위치
3. fixed: 고정위치
4. sticky: 스크롤에 따라 static >> fixed로 변경
5. static: 기본

> absolute

- relative가 없으면 browser기준으로 움직인다.

> absolute vs relative

- absolute는 위치차지 X, relative는 위치차지 O

> position sticky

- 기본적으로 static이나 스크롤 이동에 따라 fixed로 변경
