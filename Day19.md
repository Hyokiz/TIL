# 20220803 TIL

## CSS Layout

> CSS layout techniques

- Display
- Position
- Float(1996)
- Flexbox(2012)
- Grid(2017)
- 기타
  - Responsive Web Design, Media Queries

## Float

> CSS 원칙1

- Normal Flow
  - 좌측 최상단부터 쌓인다.
- 모든 요소는 네모(박스모델)이고, 위에서부터 아래로, 왼쪽에서 오른쪽으로 쌓인다.(좌상단부터 배치)

> Float

- 박스를 왼쪽 혹은 오른쪽으로 이동시켜 텍스트를 포함 인라인요소들이 주변을 wrapping 하도록 함
- 요소가 Normal flow를 벗어나도록 함

> Float 속성

- none : 기본
- left : 요소를 왼쪽으로 띄움
- right : 요소를 오른쪽으로 띄움

## Flexbox

> CSS Flexible Box Layout

- 행과 열 형태로 아이템들을 배치하는 1차원 레이아웃 모델

- 축
  - main axis (메인 축)
  - cross axis (크로스 축)
- 구성 요소
  - Flex Container(부모 요소)
  - Flex Item(자식 요소)

> Flexbox 축

- flex-direction : row
- 꼬치가 으론쪽으로 있으니 왼쪽부터 채워짐

> Flex 속성

- 배치 설정
  - flex-direction
  - flex-wrap
- 공간 나누기
  - justify-content(main axis)
  - align-content(cross axis)
- 정렬
  - alignj-items (모든 아이템을 cross axis 기준으로)
  - align-self (개별 아이템)

> flex-direction

- Main axis 기준 방향 설정
- 역방향의 경우 HTML 태그 선언 순서와 시각적으로 다름
  - row : 좌 >> 우
  - row-reverse : 우 >> 좌
  - column : 상 >> 하
  - column-reverse : 하 >> 상

> flex-wrap

- 아이템이 컨테이너를 벗어나는 경우 해당 영역 내에 배치되도록 설정
- 기본적으로 컨테이너 영역을 벗어나지 않도록 함
- nowrap(기본) : 한 줄에 배치
- wrap : 넘기면 그 다음줄로 배치

> flex-direction & flex-wrap

- flex-direction : Main axis 의 방향을 설정

- flex-wrap : 요소들이 강제로 한 줄에 배치 되게 할 것인지 여부 설정

  - nowrap(기본) : 한줄배치
  - wrap : 넘치면 그 다음줄 배치

- flex-flow
  - flex-direction과 flex-wrap의 shorthand
  - flex-direction과 flex-wrap에 대한 설정 값을 차례로 작성

> justify-content

- Main axis를 기준으로 공간 배분

1. flex-start : 왼쪽정렬
2. flex-end : 오른쪽정렬
3. center : 가운데정렬
4. space-between : 왼쪽 오른쪽 여백 없이 content 사이만 같은 간격으로
5. space-aruound : 공간을 n으로 나눠서 같은 간격으로
6. space-evenly : 왼쪽 오른쪽 여백 합쳐서 같은 간격으로

> align-content

- Cross axis를 기준으로 공간 배분(아이템이 한 줄로 배치되는 경우 확인 X)

1. flex-start : 위로 배치
2. flex-end : 아래로 배치
3. center : 가운데 배치
4. space-between : 가운데 남겨놓고 양옆
5. space-around : 위와 같음
6. space-evenly : 위와 같음

> justify-content & align-content 정리

- 공간 배분
  - flex-start(기본) : 아이템들을 axis 시작점으로
  - flext-end : 아이템들을 axis 끝쪽으로
  - center : 아이템들을 axis 중앙으로
  - space-between : 아이템 사이의 간격을 균일하게 분배
  - space-around : 아이템을 둘러싼 영역을 균일하게 분배
  - space-evenly : 전체 영역에서 아이템 간 간격을 균일하게 분배

> align-items

- 모든 아이템들을 Cross axis 기준으로 정렬

1. stretch : 꽉 채워서 기본정렬
2. baseline : 글자 선 기준으로

> align-self

- 개별 아이템을 Cross axis 기준으로 정렬
  - 컨테이너에 적용하는 것이 아닌 개별 아이템에 적용

> align-items & align-self 정리

- Cross axis를 중심으로
  - stretch(기본값) : 컨테이너를 가득 채움
  - flex-start : 위
  - flex-end : 아래
  - center : 가운데
  - baseline : 텍스트 baseline에 기준선을 맞춤

> Flex 기타 속성

- flex-grow : 남은 영역을 아이템에 분배
- order : 배치 순서

## Bootstrap

### spacing

> spacing (Margin and padding)

- {property}{sides}-{size}
- property : margin, padding
- sides : t(top), b(bottom), s(start), e(end), x(left and right), y(top and bottom), blank(all 4 side)
- size : 0, 1, 2, 3, 4, 5, auto

> spacing

- 1rem : 16px
- 0.25rem : 4px
- size : 1 == 4px, 2 == 8px, 3 == 16px, 4 == 24px, 5 == 48px, 0 == 좌우마진0
- .mx-auto : 수평 중앙 정렬, 가로 가운데 정렬

### color

- bg-{color} = background color
- text-{color} = text color

### position

- position-{position} : position을 {position}으로 설정

## Bootstrap 컴포넌트

> Components

> Form

> Navbar

- 많이 쓴다.

> Carousel

- 온라인 쇼핑몰에서 슬라이드가 있고, 슬라이드를 넘기는 부분

> Modal

- 중첩해서 넣으면 안됨.

> Card, grid card

### Bootcamp Grid System

> Grid system(web design)

- 요소들의 디자인과 배치에 도움을 주는 시스템
- 기본 요소
  - Column : 실제 컨텐츠를 포함하는 부분
  - Gutter : 칼럼과 칼럼 사이의 공간(사이 간격)
  - Container : Column들을 담고 있는 공간

> Bootstrap grid System

- flexbox로 제작됨
- container, rows, column으로 컨텐츠 배치하고 정렬
- 반드시 기억해야 할 2가지
  - 12개의 column
  - 6개의 grid breakpoints

> Grid system breakpoints
