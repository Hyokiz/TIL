# 20220830 TIL

## Django

- 거인의 어깨 위에서 프로그래밍 하기

> Framework 이해하기

- 서비스 개발에 필요한 기능들을 미리 구현해서 모아놓은 것 == 프레임워크(Framework)
- 틀을 가지고 일한다.
- 프레임워크 == 밀키트
- 누군가 만들어 놓은 코드를 재사용 하는 것은 이미 익숙하다.
- 웹 서비스도 누군가가 개발해 놓은 코드를 재사용하면 된다.
- 소프트웨어의 생산성과 품질을 높임.

> 장고를 배워야 하는 이유

1. Python으로 작성된 프레임워크
   - 파이썬이라는 언어의 강력함과 거대한 커뮤니티
2. 수많은 여러 유용한 기능들
3. 검증된 웹 프레임워크
   - 화해, Toss, 두나무, 당근마켓, 요기요 등
   - 유명한 많은 서비스들이 사용한다는 것 == 안정적으로 서비스를 할 수 있다는 검증

## Web

> www(World Wide Web)

- 전 세계에 퍼져 있는 거미줄 같은 연결망

## 클라이언트와 서버

- 클라이언트
  - 크롬 브라우저 등

- 서버
  - 클라이언트가 요청하면 응답해주는 주체

> 정리

- 우리가 사용하는 웹은 클라이언트 - 서버 구조로 이루어져 있음
- 앞으로 배우는 것 클라이언트- 서버 구조를 만드는 방법을 배움

## Web browser와 Web page

> 정적 웹 페이지

- HTML 파일의 내용이 변하지 않고 모든 사용자에게 동일한 모습으로 전달되는 것
  - 같은 상황에서 모든 사용자에게 동일한 정보를 표시

> 동적 웹 페이지

- 사용자의 요청에 따라 웹 페이지에 추가적인 수정이 되어 클라이언트에게 전달되는 웹 페이지
- 웹 페이지의 내용을 바꿔주는 주체 == 서버
  - 서버에서 동작하고 있는 프로그램이 웹 페이지를 변경해줌
  - 이렇게 사용자의 요청을 받아서 적절한 응답을 만들어주는 프로그램을 쉽게 만들 수 있게 도와주는 프레임워크가 Django

## Django 구조 이해하기

## Design Pattern

> Design Pattern

- 자주 사용되는 구조가 있고, 이를 일반화해서 하나의 공법으로 만드는 것

> 소프트웨어 디자인 패턴의 장점

- 다수의 엔지니어들이 일반화된 패턴으로 소프트웨어 개발을 할 수 있도록 한 규칙, 커뮤니케이션의 효율성을 높이는 기법

## Django's Design Pattern

> Django에서의 디자인 패턴

- MTV패턴
- MTV패턴은 MVC 디자인 패턴을 기반으로 조금 변형된 패턴

> MVC 소프트웨어 디자인 패턴

- MVC : Model View Controller

1. Model : 데이터와 관련된 로직을 정리
2. View : 레이아웃과 화면을 처리
3. Controller : 명령을 model과 view부분으로 연결

> MTV

- Model Template View
- Django에서는
  - Model >> Model
  - View >> Template
  - Controller >> View

> MTV 디자인 패턴

- Model
  - 데이터와 관련된 로직을 관리

- Template
  - 레이아웃과 화면을 처리

- View
  - Model & Template과 관련된 로직을 처리해서 응답을 반환
  - 클라이언트의 요청에 대해 처리를 분기하는 역할
  - 동작 예시
    - 데이터가 필요하다면 model에 접근해서 데이터를 가져오고 가져온 데이터를 template로 보내 화면을 구성하고 구성된 화면을 응답으로 만들어 클라이언트에게 반환
  - MVC에서 Controller의 역할

> 정리

- Django는 MTV 디자인 패턴을 가지고 있음
  - Model : 데이터 관련
  - Template : 화면 관련
  - View : Model & Template 중간 처리 및 응답 반환

## Django Quick start

1. 가상환경 만들기  
  - python -m venv venv

2. 가상환경 활성화
  - source venv/Scripts/activate 
  - source venv/bin/activate (MAC)

3. 가상환경 비활성화
  - deactivate

4. django 설치하기
  - pip install django==3.2.13

5. 가상환경 패키지 목록 조회
  - pip list

6. requirements.txt 생성
  - pip freeze > requireents.txt
  - 한번 더 입력하면 덮어쓰기 가능

7. requirements.txt 목록 설치
  - pip install -r requirements.txt

8. django 프로젝트 생성
 - django-admin startproject firstpjt .(firstpjt에는 아무거나 상관 없음)
 - .을 찍지 않으면 폴더 안에 폴더 생성(.은 현재폴더)

9. django 서버 실행
   - python manage.py runserver

10. django 애플리케이션 생성
  - python manage.py startapp articles

11. INSTALLED_APPS에 앱을 등록
  - 반드시 생성 후 등록.
  - 사용자가 만든 애플리케이션은 제일 윗줄에 등록.

12. urls.py에 path 등록
  - url 끝 주소는 slash를 적어줘야 한다.(트레일링 슬래시)
  - request 는 제일 위에 와야한다.

13. views.py에 함수 생성

14. template 생성

15. 크롬에서 해당 URL로 요청

## Django Template

> Django Template Language(DTL)

- 조건, 반복, 변수, 치환, 필터 등의 기능 제공
  - 제공한다고 남발하면 안된다.

> DTL Syntax

1. Variable
   - render()의 세번째 인자로 딕셔너리 형태로 넘겨주어 사용 가능

2. Filters

3. Tags

4. Comments