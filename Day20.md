# 20220804 TIL

## float

- float : 띄우기
- 다수를 띄울 경우 자리가 없어서 옆으로 붙는다.
- clear : 그 라인에 해당하는 float 취소

## flexbox

- flex container : 부모
- flexbox : 기존의 float, absolute는 각각 수치를 설정해야 되기 때문에 그것의 보완으로 css의 속성을 이용하여 정렬하는 것.
- axis 의 경우 방향이 아닌 main axis, cross axis로 구분
- 축이 정해지는 기준 : item이 쌓이는 방향

- flexbox는 부모 >> 자식 까지만 적용. 부모 >> 자손까지는 적용되지 않는다.
- 자손까지 적용하고 싶은 경우 자식에 flexbox를 걸어서 자식 >> 자손으로 적용되게 해야 한다.

- flexbox 속성 2가지
  - 부모 컨테이너에 적용하는 것
  - 자식 아이템에 적용하는 것

> flexbox 속성 : 부모 컨테이너에 적용법

- display : flex; 적용
  - 안의 item들이 main axis 를 기준으로 정렬
  - flex-direction : axis 정하기. 기본값은 row
  - flex-wrap : 기본값 nowrap
    - wrap : 넘치면 다음 axis로 넘어감. 
    - no wrap : 넘치면 item의 크기를 줄인다.
    - wrap reverse : 넘치면 위로 올라간다.
  - flex-flow : flex-direction과 flex-wrap을 한 줄로 표현 가능
  - justify : main axis와 함께 사용. 부모 컨테이너에 적용
    - justify-content : main axis 를 기준으로 item을 어떻게 배치?
      - flex-start : 좌측정렬
      - flex-end : 우측정렬
      - center : 가운데정렬
      - space-between : 양 쪽 끝에 item을 붙이고 그 사이 간격을 동등하게
      - space-evenly : 모든 item의 간격을 동등하게
      - space-around : container / len(item)만큼 공간을 나눠서 그 공간의 가운데에 item을 배치
    - align : cross axis 기준
      - alien items
        - baseline : 글자 밑선 기준
    - 일반적으로 justify-content 랑 align-items를 같이 사용.
    - justify : 메인, aline : 교차, content : 여러개, itmes : 하나
      - justify itmes : flexbox에서 무시당함 >> 안쓰는 기능
      - justify self : flexbox에서 무시당함 >> 다른 곳에서는 사용

> flexbox 속성 : 자식 item에 적용

- flex-grow : 남는 공간에 정해주는 비율 만큼 값을 채운다.
- align-self : 교차축을 기준으로 각각의 items를 정렬하려고 할 때 사용
- order : 각각의 순서 적용. 순서 바꾸기. 실제론 바뀌지 않고 눈으로 보여주는 것만 바뀜



