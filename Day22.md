# 20220807 TIL

## Web

> 웹 사이트의 구성 요소

- HTML : 구조
- CSS : 표현
- Javascript : 동작

> 웹 사이트와 브라우저

- 웹 사이트는 브라우저를 통해 동작
- 브라우저마다 동작이 다름
- 해결책으로 웹 표준 등장

> 웹 표준

- 웹에서 표준적으로 사용되는 기술이나 규칙
- 어떤 브라우저든 웹 페이지가 동일하게 보이도록 함.(크로스 브라우징)

## HTML

> Markup Language

- 태그 등을 이용하여 문서나 데이터의 구조를 명시하는 언어
  - HTML, Markdown 등

> HTML 스타일 가이드

- 마크업 스타일 가이드(2 space)

## HTML 기본 구조

> HTML 기본 구조

- html : 문서의 최상위 요소
- head : 문서 메타데이터 요소
  - 문서 제목, 인코딩, 스타일, 외부 파일 로딩 등
  - 일반적으로 브라우저에 나타나지 않는 내용
- body : 문서 본문 요소
  - 실제 화면 구성과 관련된 내용

> head 예시

- title : 브라우저 상단 타이틀
- meta : 문서 레벨 메타데이터 요소
- link : 외부 리소스 연결 요소 (CSS, favicon 등)
- script : 스크립트 요소(JavaScript 파일/코드)
- style : CSS 직접 작성

> 요소(element)

- HTML 요소는 시작 태그, 종료 태그, 그 사이에 위치한 내용으로 구성
  - 요소는 태그로 컨텐츠를 감싸는 것으로 그 정보의 성격과 의미를 정의
  - 내용이 없는 태그도 존재(닫는태그 X)
    - br, hr, img, imput, link, meta
- 요소는 중첩될 수 있음
  - 요소의 중첩을 통해 하나의 문서를 구조화
  - 여는 태그 닫는 태그 쌍 확인
    - 오류를 반환하는 것이 아니고 레이아웃이 깨진 상태로 출력되기 때문에, 디버깅이 힘들어질 수 있음

> 속성 작성 방식 통일하기

- 공백 없이, 쌍따옴표 사용하기

> 속성

- 속성을 통해 태그의 부가적인 정보 설정 가능
- 요소는 속성을 가질 수 있으며, 경로나 크기와 같은 추가적인 정보 제공
- 태그와 상관없이 사용 가능한 속성들도 있음.

> HTML Global Attribute

- 모든 HTML 요소가 공통으로 사용할 수 있는 대표적인 속성
  - id : 문서 전체에서 유일한 고유 식별자 지정
  - class : 공백으로 구분된 해당 요소의 클래스 목록(CSS, JS에서 요소를 선택하거나 접근)
  - data-\* : 페이지에 개인 사용자 정의 데이터를 저장하기 위해 사용
  - style : inline 스타일
  - title : 요소에 대한 추가 정보 지정
  - tabindex : 요소의 탭 순서

> 시맨틱 태그

- HTML 태그가 특정 목적, 역할 및 의미적 가치를 가지는 것
  - 예를 들어 h1 태그는 최상위 제목인 텍스트를 감싸는 역할
- Non semantic 요소로는 div, span 등이 있고 a, form, table 태그들도 시맨틱 태그로 볼 수 있음
- HTML5에서는 구획을 나타내기 위해 사용한 div태그의 대체로 여러 태그들 추가
- 대표적인 시맨틱 태그 목록
  - header : 머리말
  - nav : 내비게이션
  - aside : 사이드에 위치한 공간
  - section : 문서의 일반적인 부분, 컨텐츠의 그룹
  - article : 문서, 페이지, 사이트 안에서 독립적으로 구분되는 영역
  - footer : 문서 전체나 섹션의 푸터(마지막)

> 시맨틱 태그 사용 이유

- 의미론적 마크업
  - 개발자 및 사용자 뿐 아니라 검색엔진 등에 의미 있는 정보의 그룹을 태그로 표현
  - 의미를 가지는 태그들을 활용하기 위한 노력
  - 요소의 의미가 명확해지기 때문에 코드의 가독성을 높이고 유지보수 쉽게 함
  - 검색 엔진 최적화를 위해 마크업을 효과적으로 활용

> 텍스트로 작성된 코드가 어떻게 웹 사이트로?

- 렌더링
  - 웹 사이트 코드를 사용자가 보게 되는 웹 사이트로 바꾸는 과정

> DOM(Document Object Model) 트리

- 텍스트 파일인 HTML 문서를 브라우저에서 렌더링 하기 위한 구조
  - HTML 문서에 대한 모델 구성
  - HTML 문서 내 각 요소에 접근 / 수정에 피료한 프로퍼티, 메서드 제공

## HTML 문서 구조화

> 인라인 / 블록 요소

- HTML 요소는 크게 인라인 / 블록 요소로 나눔
- 인라인 요소는 글자처럼
- 블록 요소는 한 줄 모두

> 텍스트 요소

- a 태그 : href 속성을 활용하여 하이퍼링크 생성
- b 태그, strong 태그 : 굵은 글씨
- i 태그, em 태그 : 기울임 글씨
- br : 줄바꿈
- img : 이미지
- span : 의미 없는 인라인 컨테이너

> 그룹 컨텐츠

- p : 하나의 문단
- hr : 주제의 분리. 수평선
- ol / ul : 순서가 있는 / 없는 리스트
- pre : HTML에 작성한 내용 그대로 표현. 보통 고정폭 글꼴 사용, 공백 문자 유지
- blockquote : 텍스트가 긴 인용문. 주로 들여쓰기
- div : 의미 없는 블록 컨테이너

> form

- 정보를 서버에 제출하기 위해 사용
- form 기본 속성
  - action : form을 처리할 서버의 URL
  - method : form을 제출할 때 사용할 HTTP 메서드(GET or POST)
  - enctype : method가 post인 경우 데이터의 유형

> input

- 다양한 타입을 가지는 입력 데이터 유형과 위젯이 제공됨
- 대표적인 속성
  - name : form control에 적용되는 이름
  - value : form control에 적용되는 값

> input label

- label을 클릭하여 input 자체의 초점을 맞추거나 활성화 시킬 수 있음
  - 사용자는 선택할 수 있는 영역이 늘어나 웹 / 모바일 환경에서 편하게 사용가능
  - 화면리더기에서도 label을 읽어 쉽게 내용 확인 가능
- input에 id 속성을, label에는 for 속성 활용하여 상호 연관.

> input 유형 - 일반

- 일반적으로 입력을 받기 위해 제공
  - text : 일반 텍스트 입력
  - password : 입력 값이 보이지 않고 문자를 특수기호로 표현
  - email : 이메일 형식이 아닌 경우 form 제출 불가
  - number : min, max, step으로 범위 설정 가능
  - file : accept 속성 활용하여 파일 타입 지정 가능

> input 유형 - 항목 중 선택

- 동일 항목에 대하여는 name을 지정하고 선택된 항목에 대한 value를 지정해야 함
  - checkbox : 다중 선택
  - radio : 단일 선택

> input 유형 - 기타

- 다양한 종류의 input을 위한 picker를 제공

  - color : color picker
  - date : date picker

- hidden input을 활용하여 사용자 입력에 받지 않고 서버에 전송되어야 하는 값 설정
  - hidden : 사용자에겍 보이지 않는 input

> input 유형 - 종합

- input 요소의 동작은 type에 따라 달라지므로 각각의 내용 숙지

## CSS

> CSS

- cascading : 폭포같이 위에서 아래로

> CSS 구문 - 용어정리

- 선택자, 선언, 속성, 값

- 선택자를 통해 스타일을 지정할 HTML 요소 선택
- 중괄호 안에서 속성과 값, 하나의 쌍으로 이루어진 선언 진행
- 각 쌍은 선택한 요소의 속성, 속성에 부여할 값 의미
  - 속성 : 어떤 스타일 기능을 변경할지 결정
  - 값 : 어떤 스탕리 기능을 변경할지 결정

> CSS 정의 방법

1. 인라인(inline)
   - 실수가 잦아짐(중복도 있고 찾기 어려움)
2. 내부 참조(embedding) - style
   - 내부 참조를 쓰게 되면 코드가 너무 길어짐
3. 외부 참조(link file) - 분리된 CSS 파일
   - 가장 많이 사용

## CSS Selectors

> 선택자 유형

- 기본 선택자
  - 전체 선택자, 요소 선택자
  - 클래스 선택자, 아이디 선택자, 속성 선택자
- 결합자
  - 자손 결합자, 자식 결합자
  - 일반 형제 결합자, 인접 형제 결합자
- 의사 클래스/요소
  - 링크, 동적 의사 클래스
  - 구조적 의사 클래스, 기타 의사 클래스, 의사 엘리먼트, 속성 선택자

> CSS 선택자 정리

- 요소 선택자
  - HTML 태그 직접 선택
- 클래스 선택자
  - 마침표(.)문자로 시작하며, 해당 크래스가 적용된 항목을 선택
- 아이디 선택자
  - #문자로 시작, 해당 아이디가 적용된 항목을 선택
  - 일반적으로 하나의 문서에 1번만 사용
  - 여러 번 사용해도 동작하지만, 단일 id를 사용하는 것을 권장

> CSS 적용 우선 순위

- CSS 우선순위

1. 중요도(Importance) - 사용 시 주의
   - !important
2. 우선 순위
   - 인라인 > id > 클래스, 속성, pseudo-class > 요소, pseudo-element
3. CSS 파일 로딩 순서
   - 위에서 아래로

> CSS 상속

- CSS는 상속을 통해 부모 요소의 속성을 자식에게 상속.
  - 상속이 되는 것과 되지 않는 것들이 있다.
  - 상속 되는 것
    - text관련 요소(font, color, text-align), opacity, visiblity 등
  - 상속 되지 않는 것
    - box model 관련(width, height, margin, padding 등)
    - position 관련 요소(position top/right/bottom/left, z-index)등

## CSS 기본 스타일

> 크기 단위

- em

  - 상속의 영향을 받음
  - 배수 단위, 요소에 지정된 사이즈에 상대적인 사이즈를 가짐

- rem
  - 상속의 영향을 받지 않음
  - 최상위 요소의 사이즈를 기준으로 배수 단위를 가짐

> 크기 단위

- px는 브라우저의 크기를 변경해도 그대로
- vw는 브라우저의 크기에 따라 크기가 변함

> CSS 문서 표현

- 텍스트
  - 서체(font-family), 서체 스타일(font-style, font-weight)등
  - 자간(letter-spacing), 단어 간격(word-spacing), 행간(line-height)등
- 컬러(color), 배경(background-image, background-color)
- 기타 HTML 태그별 스타일링
  - 목록(li), 표(table)

## Selectors 심화

> 결합자

- 자손 결합자(공백)
  - selectorA 하위의 모든 selectorB 요소
- 자식 결합자(>)
  - selectorA 바로 아래의 selectorB 요소
- 일반 형제 결합자(~)
  - selectorA의 형제 요소 중 뒤에 위치하는 selectorB요소를 모두 선택
- 인접 형제 결합자(+)
  - selectorA의 형제 요소 중 바로 뒤에 위치하는 selectorB 요소를 선택

## CSS Box Model

> CSS 원칙

- 모든 요소는 박스모델, 위에서 아래로 왼쪽에서 오른쪽으로

> Box model

- 모든 HTML 요소는 Box로 되어 있다.
- 하나의 박스는 네 부분으로 이루어짐
  - margin : 테두리 바깥 외부 여백. 배경색 지정 X
  - border : 테두리 영역
  - padding : 태두리 안쪽의 내부 여백. 배경색, 이미지는 padding까지 적용
  - content : 글이나 이미지 등 요소의 실제 내용

> box-sizing

- 기본적으로 모든 요소의 box-sizing은 content-box
  - padding을 제외한 순수 contents 영역만을 box로 지정
- 다만 우리가 일반적으로 영역을 볼 때는 border까지의 너비를 100px 보는 것을 원함
  - 그 경우 box-sizing을 border-box로 설정

## CSS Display

> 대표적으로 활용되는 display

- display : block

  - 줄 바꿈이 일어나는 요소
  - 화면 크기 전체의 가로폭 차지
  - 블록 레벨 요소 안에 인라인 레벨 요소 들어갈 수 있다.

- display : inline

  - 줄 바꿈이 일어나지 않는 행의 일부 요소
  - content 너비만큼 가로 폭 차지
  - wid, height, margin-top, margin-bottom 지정 X
  - 상하 여백은 line-height로 지정

> 블록 레벨 요소와 인라인 레벨 요소

- 대표적인 블록 레벨 요소
  - div / ul, ol, li / p / hr / form 등
- 대표적인 인라인 레벨 요소
  - span / a / img / input, label / b, em, i, strong

> display

- display: inline-block

  - block과 inline 레벨 요소의 특징 모두 가짐
  - inline 처럼 한줄에 표시할 수 있고, block처럼 width, height, margin 속성 모두 지정 가능

- display: none
  - 해당 요소를 화면 표시 X, 공간 부여 X
  - 이와 비슷한 visibilty: hidden은 해당 요소가 공간은 차지하나 화면에 표시 X

## CSS Position

> CSS position

- 문서 상에서 요소의 위치 지정
- static : 모든 태그의 기본 값(기본 위치)
  - 일반적인 요소의 배치 순서 따름(좌상단)
  - 부모 요소 내에서 배치 시 부모 요소의 위치를 기준으로 배치
- 아래는 좌표 프로퍼티(top, bottom, left, right)를 사용하여 이동 가능
  1. relative
  2. absolute
  3. fixed
  4. sticky

> CSS position

1. relative : 상대 위치

   - 자기 자신의 static 위치를 기준으로 이동(normal flow 유지)
   - 레이아웃에서 요소가 차지하는 공간은 static일 때와 같음(normal position 대비 offset)

2. absolute : 절대 위치

   - 요소를 일반적인 문서 흐름에서 제거 후 레이아웃에 공간 차지 X(normal flow에서 벗어남)
   - static이 아닌 가장 가까이 있는 부모/조상 요소를 기준으로 이동

3. fixed : 고정 위치

   - 요소를 일반적인 문서 흐름에서 제거 후 레이아웃에 공간 차지 X(normal flow에서 벗어남)
   - 부모 요소와 관계 없이 viewport를 기준으로 이동
     - 스크롤 시에도 항상 같은 곳 위치

4. sticky : 스크롤에 따라 static >> fixed 로 변경

   - 속성을 적용한 박스는 평소 문서 안에서 position: static 상태와 같이 일반적인 흐름에 따르지만 스크롤 위치가 임계점에 이르면 position: fixed와 같이 박스를 화면에 고정할 수 있음

> CSS 원칙 정리

- CSS 원칙 I, II : Normal flow

  - 모든 요소는 네모(박스모델), 좌측 상단에 배치
  - display에 따라 크기와 배치가 달라짐

- CSS 원칙 III
  - position으로 위치의 기준 변경
    - relative : 본인의 원래 위치
    - 특정 부모의 위치
    - fixed : 화면의 위치
    - sticky : 기본적으로 static이나 스크롤 이동에 따라 fixed 로 변경

---

## CSS layout

### Float

> Float

- 박스를 왼쪽 혹은 오른쪽으로 이동시켜 텍스트를 포함 인라인 요소들이 주변을 wrapping 하도록 함
- 요소가 Normal flow를 벗어나도록 함

> Float 속성

- none : 기본값
- left : 요소를 왼쪽으로 띄움
- right : 요소를 오른쪽으로 띄움

### Flexbox

> CSS Flexible Boy Layout

- 행과 열 형태로 아이템들을 배치하는 1차원 레이아웃 모델
- 축
  - main axis(메인 축)
  - cross axis(교차 축)
- 구성 요소
  - Flex Container(부모 요소)
  - Flex Item(자식 요소)

> Flexbox 축

- flex-direction : row

> Flexbox 구성 요소

- Flex Container(부모 요소)
  - flexbox 레이아웃을 형성하는 가장 기본적인 모델
  - Flex Item들이 놓여있는 영역
  - display 속성을 flex 혹은 inline-flex로 지정
- Flex Item(자식 요소)
  - 컨테이너에 속해 있는 컨텐츠(박스)

> Flex 속성

- 배치 설정

  - flex-direction
  - flex-wrap

- 공간 나누기

  - justify-content (main axis)
  - align-content (cross axis)

- 정렬
  - align-itmes (모든 아이템을 corss axis 기준으로)
  - align-self (개별 아이템)

> Flex 속성 : flex-direction

- main axis 기준 방향 설정
- 역방향의 경우 HTML 태그 선언 순서와 시각적으로 다름.

1. row : 가로로 왼쪽에서 오른쪽
2. row-reverse : 가로로 오른쪽에서 왼쪽
3. column : 세로로 위에서 아래로
4. column-reverse : 세로로 아래에서 위로

> Flex 속성 : flex-wrap

- 아이템이 컨테이너를 벗어나는 경우 해당 영역 내에 배치되도록 설정
- 컨테이너 영역 벗어나지 않도록 함

1. wrap : 벗어날 경우 다음 줄에 배치
2. nowrap : 한 줄에 배치되도록 가로 길이를 줄임

> Flex-flow

- flex-direction과 flex-wrap의 shorthand
- 설정 값을 차례로 작성
  - ex. flex-flow: row nowrap;

> Flex 속성 : justify-content

- main axis를 기준으로 공간 배분

1. flex-start : 왼쪽부터
2. flex-end : 오른쪽부터
3. center : 가운데
4. space-between : 양 끝 배치 후 같은 간격으로
5. space-around : container 를 item 개수만큼 공간을 나눈 후 공간의 가운데 배치
6. space-evenly : 모든 공간을 동일하게

> Flex 속성 : align-content

- cross axis를 기준으로 공간 배분

1. flex-start : 위에서부터
2. flex-end : 아래서부터 (3개일 경우 제일 밑에는 3만 옴)
3. center : 가운데
4. space-between : 양 끝 배치 후 같은 간격으로
5. space-around : 위와 같음
6. space-evenly : 위와 같음

> Flex 속성 : justify-content 와 align-content 정리

- 공간 배분
  - flex-start(기본 값) : 아이템들을 axis 시작점으로
  - flex-end : 아이템들을 axis 끝 쪽으로
  - center : 아이템들을 axis 중앙으로
  - space-between : 아이템 사이의 간격을 균일하게
  - space-around : 아이템을 둘러싼 영역을 균일하게 분배(가질 수 있는 영역을 반으로 나눠서 양쪽에)
  - space-evenly : 전체 영역에서 아이템 간 간격을 균일하게 분배

> Flex 속성 : align-items

- 모든 아이템을 cross axis를 기준으로 정렬

> Flex 속성 : align-self

- 개별 아이템을 Cross axis 기준으로 정렬
  - 해당 속성은 컨테이너에 적용하는 것이 아니라 개별 아이템에 적용

> Flex 속성 : align-items 와 align-self

- cross axis를 중심으로
  - stretch(기본 값) : 컨테이너를 가득 채움
  - flex-start : 위
  - flex-end : 아래
  - center : 가운데
  - baseline(items만) : 텍스트 baseline에 기준선을 맞춤

> Flex에 적용하는 속성

- 기타 속성
  - flex-grow : 남은 영역을 아이템에 분배
  - order : 배치 순서

## Bootstrap

> spacing

- {property}{sides}-{size}
  - property
    - m(margin), p(padding)
  - sides
    - t(top), b(bottom), s(start), e(end), x(left, right), y(top, bottom)
  - size
    - 1 : 0.25rem / 4px
    - 2 : 0.5rem / 8px
    - 3 : 1rem / 16px
    - 4 : 1.5rem / 24px
    - 5 : 3rem / 48px
    - 0 : 0
    - auto : 수평 중앙 정렬, 가로 가운데 정렬

## Bootstrap 컴포넌트

> Components

- Bootstrap의 다양한 UI 요소를 활용할 수 있음
- 아래 Components 탭 및 검색으로 원하는 UI 요소 찾을 수 있음

> Buttons

- 클릭 했을 때 어떤 동작이 일어나도록 하는 요소

> Dropdowns

- 옵션 메뉴 만들수 있음.

> Forms > Form controls

- form-control 클래스를 사용해 input, form 태그를 스타일링할 수 있음.

> Navbar

- 네비게이션 바 제작

> Carousel

- 콘텐츠를 순환시키기 위한 슬라이드 쇼

> Modal

- 사용자와 상호작용 하기 위해서 사용, 긴급 상황을 알리는데 주로 사용
- 현재 열려 있는 페이지 위에 또 다른 레이어를 띄움

> Responsive Web Design

- 다양한 화면 크기를 가진 디바이스들이 등장함에 따라 반응형 웹 디자인 개념이 등장
- 반응형 웹은 별도의 기술 이름이 아닌 웹 디자인에 대한 접근 방식, 반응형 레이아웃 작성에 도움이 되는 사례들의 모음 등을 기술하는데 사용되는 용어

## Bootstrap Grid System

> Grid system (web design)

- 요소들의 디자인과 배치에 도움을 주는 시스템
- 기본 요소
  - Column : 실제 컨텐츠를 포함하는 부분
  - Gutter : 칼럼과 칼럼 사이의 공간
  - Container : Column 들을 담고 있는 공간

> Bootstrap grid System

- Bootstrap Grid system은 flexbox로 제작됨
- container, rows, column으로 컨텐츠를 배치하고 정렬
- 반드시 기억
  1. 12개의 column
  2. 6개의 grid breakpoints

> Grid System breakpoints

- xs : <576px
- sm : 576px < s < 768px
- md : 768px < md < 992px
- lg : 992px < lg < 1200px
- xl : 1200px < xl < 1400px
- xxl : >1400px
