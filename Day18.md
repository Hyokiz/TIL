# 20220822 TIL

## 복습

> 웹 사이트의 구성 요소

- 웹 사이트란 웹 페이지(글)들의 모음이다.

### HTML 문법 위주

> Hyper Text?

- 링크를 통해서 이동하는 것

> Markup Language

- Mark : 글에 역할을 부여하는 것

- html은 단지 문서이고, 기능은 브라우저가 정한다.

- Dom Tree 로 이루어져 있다.

> 요소

- tag + 내용(contents)
- tag 안에 tag가 들어갈 수 있다.

> 속성

- 이름 + 값 
- 태그에 부가적인 것
- 속성명과 값 사이에 공백 없음
- 값은 큰따옴표(")로 감싼다.

> HTML Global Attribute

- id : 문서 전체에서 유일한 고유 식별자 지정
- class : 공백으로 구분된 해당 요소의 클래스의 목록
- style

> 인라인 / 블록 요소

- 인라인 요소 : 글자만큼만 차지
- 블록 요소 : 한 줄 차지

> label 

- label for "" == input id = "" >> ""의 내용이 같아야 한다.

> 모르는 것이 있다면 구글검색에 mdn을 포함하여 검색해보자!

### CSS 문법 위주

> CSS

- 선택자, 결합자, display, position

> CSS 정의방법

- inline
- 내부참조
- 외부참조

> 선택자

1. 전체선택자 : 별표(*)
2. 요소선택자 : html 기본제공 tag 선택
3. id 선택자 : 원하는 것 1개만 선택 >> id 선택 시 #
4. class 선택자 : 원하는 것 여러개 선택 >> 클래스 선택 시 .

> 결합자

1. 자식결합자 : 꺽쇠(>)로 표현. 한 단계만 해당
2. 자손결합자 : 공백(" "). 클래스 하위 안의 모든 것 해당
3. 인접형제결합자 : (+)로 표현. 같은 깊이 일때 바로 뒤에 위치하는 것이 결합. 바로 뒤에 있는 결합만 된다.
4. 일반형제결합자 : (~)로 표현. 뒤에 있는 모든 것에 다 적용

> CSS 원칙

- 모든 요소는 네모(박스모델), 위에서부터 아래로, 왼쪽에서 오른쪽으로 쌓인다.
- 마진 : 바깥, 보더 : 경계선, 패딩 : 속성, content : 내용

> Display

- display: block
  - 줄바꿈 있음
  - 한줄 차지
- display: inline
  - 글자만큼만 차지
  - 줄바꿈 없음
  - width, height, mergin-top, margin-bottom을 지정할 수 없다

- inline block
  - 블록처럼 행동함.
  - 대외적으로는 인라인, 내부적으로는 블록
  - width, height, margin-top, margin-bottom을 쓸 수 있다.

> CSS Position

- 문서상에서 요소에 위치 지정
- 모든 요소는 기본 포지션(static)
 
> CSS Position

1. normal : 기본 포지션. static
2. relative : 상대 위치. static 일때 공간은 남겨두고 이동한다.(모습만 이동한 것)
3. absolute : 절대 위치. 붕 떠있는 느낌. 아무 공간 차지 X. static이 아닌 가장 가까이 있는 부모/조상 요소를 기준으로 이동(없는 경우 브라우저 화면 기준 이동)
   - absolute를 쓸 때는 어떤 position을 기준으로 사용할지 생각하고 주의하자. 
  