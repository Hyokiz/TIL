# 20220805 TIL

## 복습

### CSS우선순위

1. 속성 값 뒤에 !important를 붙인 속성 (10000점)
2. HTML style 직접 지정한 속성(1000점)
3. #id 로 지정한 속성 (100점)
4. .클래스, :추상클래스로 지정한 속성 (10점)
5. 태그이름으로 지정한 속성 (1점)
6. 상위 객체에 의해 상속된 속성

- 같은 클래스의 경우 style에서 나중에 선언된 것 적용
- 더 정확하게 명시할 수록 점수가 높다. 
- ex. body> .parent == 10 + 100 // .parent == 100

### Grid

- float, flexbox, grid(bootstrap)
- float는 잘 안씀, 시험에 나올 수 도 있으니 개념 정리
- flexbox가 1차원이라면, grid는 2차원 정렬
- grid : container, row, col // flexbox로 구현되어 있다.
- col 만 쓰면 알아서 개수만큼 똑같이 나뉜다.