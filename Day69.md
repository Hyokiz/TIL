# 20221020 TIL 

# 자바스크립트 기초 문법

## 코드 작성법

> 세미콜론

- 세미콜론을 선택적으로 사용 가능
- 없으면 ASI에 의해 자동으로 세미콜론 삽입

  - ASI (Automatic Semicolon Insertion, 자동 세미콜론 삽입 규칙)

> 들여쓰기와 코드 블럭

- JavaScript는 2칸 들여쓰기
- 블럭은 {} 내부

> 주석

- 한 줄 주석 (//)과 여러 줄 주석(/* */)

# 변수와 식별자

> 식별자 정의와 특징

- 카멜 케이스(camelCase, lower-camel-case)

  - 변수, 객체, 함수에 사용

- 파스칼 케이스(PascalCase, upper-camel-case)

  - 클래스, 생성자에 사용

- 대문자 스네이크 케이스(SNAKE_CASE)

  - 상수(constants)에 사용
  - 상수 : 개발자의 의도와 상관없이 변경될 가능성이 없는 값

> 변수 선언 키워드

1. let

   - 블록 스코프 지역 변수 선언(추가로 동시에 값 초기화)

2. const

   - 블록 스코프 읽기 전용 상수 선언(추가로 동시에 값 초기화)

3. var

   - 변수를 선언(추가로 동시에 값 초기화)

> 선언, 할당, 초기화

- 선언

  - 변수를 생성

- 할당

  - 선언된 변수에 값 저장

- 초기화

  - 선언된 변수에 처음으로 값을 저장

> 블록 스코프

- 중괄호({}) 내부
- 블록 스코프를 가지는 변수는 블록 바깥에서 접근 불가

