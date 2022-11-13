# 20221113 TIL

> Level에 따른 차이

- block level : div
- inline level : span

> 정리

- inline : 물건
- inline-block : 한 줄에 여러개가 가능한 상자
- block : 한 줄에 하나씩만 

> position 

- relative : 원래 자리에서 ~만큼 이동(상대적)
- absolute : 가장 가까이에 있는 container 안에서 이동(절대적)
- fixed : window 기준
- sticky : 원래 자리에 있으면서 scroll 해도 원래 자리 고정

> flexbox

- float : 이미지와 text 를 배치하기 위한 도구

  - float left
  - float center
  - float right

- container 에 꾸며줄 수 있는 것

  - display
  - flex-direction
  - flex-wrap
  - flex-flow
  - justify-content
  - align-items
  - align-content

- item에 넣을 수 있는 것

  - order
  - flex-grow
  - flex-shrink
  - flex
  - align-self

- 100% vs 100vh

  -  % : item에 맞게 높이 지정. 부모의 높이의 %만큼 채우겠다.
  -  vh(viewport height): 부모에 상관 없이 보이는 vh의 몇을 쓰겠다.

> color tool

- 색깔에 따른 마음에 드는 색을 고를 수 있음
- 색깔 코드 복사 후 css 에 넣기

> container 속성값들

```css
.container {
  display: flex;
  flex-direction: row;
  flex-direction: row-reverse;
  flex-direction: column;
  flex-direction: column-reverse;
  flex-wrap: nowrap; 기본값
  flex-wrap: wrap;
  flex-wrap: wrap-reverse;
  flex-flow: column nowrap;

  justify-content: flex-start; 기본값
  justify-content: flex-end; 
  justify-content: center;
  justify-content: space-around;
  justify-content: space-evenly;
  justify-content: space-between;
  align-items: center;
  align-items: baseline;
  align-content: space-between;
  align-content: center;
}
```

> 참고 사이트

- css tricks

> 속성값들

- flex-grow : 웹의 크기가 달라지면 같이 달라짐. 기본값 0
- flex-shrink: container가 작아졌을 때 행동하는 것. 기본값 0
- flex-basis: grow + shrink 합친 것. 기본값 auto. %로 사용