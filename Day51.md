# 20220918 TIL

## Namespace

> Namespace의 필요성

```py
# pages/urls.py

from django.urls import path
from . import views

# 내용이 없더라도 생성해 두어야 한다.
urlpatterns = [
    path('index/', views.index, name='index'),
]

# 쓰고 views.py로 이동

# pages/views.py

def index(request):
    return render(request, 'index.html')
```

```html
<!-- pages/templates/index.html -->

{% extends 'base.html' %} {% block content%} 잊지말기
```

> 2가지 문제 발생

1. articles app index 페이지에 작성한 두 번째 앱 index로 이동하는 하이퍼 링크를 클릭 시 현재 페이지로 다시 이동
   - URL namespace
2. pages app의 index url 로 직접 이동해도 articles app의 index 페이지가 출력됨
   - Template namespace

## URL namespace

- urlpatterns 위에 app_name을 작성하여 구분
- 그 후 {% url 'index'%} 에서 {% url 'articles:index' %}로 변경

## Template namespace

> 디렉토리 생성을 통해 물리적인 이름공간 구분

- app_name/templates/app_name 형태로 변경

> 템플릿 경로 변경

```py
# articles/views.py

return render(request, 'index.html')

# 아래처럼 변경

return render(request, 'articles/index.html')
```

> 반드시 해야하나?

- 단일 앱이라면 상관없음
- 이름이 겹치지 않으면 상관없으나, 대부분 존재

## Database

> 기본 구조

1. 스키마(Schema)
2. 테이블(Table)

> 스키마

- 뼈대
- 데이터베이스에서 자료 구조, 표현 방법, 관계 등

> 테이블

- 필드와 레코드를 사용해 조직된 데이터 요소들의 집합
- 관계라고도 부름

1. 필드(field)
   - 속성, 컬럼(Column)
2. 레코드(record)
   - 튜플, 행(Row)

> PK(Primary Key)

- 기본 키
- 다른 항목과 절대로 중복되어 나타날 수 없는 단일 값

> 쿼리(Query)

- 데이터를 조회하기 위한 명령어
- Query를 날린다 == 데이터베이스를 조작한다.

## Model

- 일반적으로 각각의 모델은 하나의 데이터베이스 테이블에 매핑
  - 모델 클래스 1개 == 데이터베이스 테이블 1개

> 매핑

- Mapping
- 하나의 값을 다른 값으로 대응시키는 것

> Model 작성하기

- django-admin startproject crud .
- python manage.py startapp articles 로 생성
- settings.py의 installed_apps에 articles추가
- models.py 작성
  - 테이블의 스키마 정의

```py
# articles/models.py

class Article(models.Model):
    title = models.charField(max_length=10)
    content = models.TextField()
```

> Model 이해하기

- 각 모델은 django.models.Model 클래스의 서브 클래스

  - 즉, 각 모델은 django.db.models 모듈의 Model 클래스를 상속받아 구성됨
  - 클래스 상속 기반 형태의 Django 프레임워크 개발
    - 프레임워크에서는 잘 만들어진 도구를 가져다가 잘 쓰는 것

- models 모듈을 통해 어떠한 타입의 DB 필드(컬럼)을 정의할 것인지 정의
  - 클래스 변수 title과 content은 DB필드를 나타냄

> 모델 필드 알아보기

- CharField(max_length=None, \*\*options)

  - 길이의 제한이 있는 문자열
  - max_length
    - 필수 인자
    - 데이터베이스와 Django의 유효성 검사에서 활용됨

- TextField(\*\*options)
  - 글자의 수가 많을 때 사용
  - max_length 옵션 작성 시 입력 단계에서는 반영되나, 모델과 데이터베이스 단계에서는 적용되지 않음
    - 저장될 때 길이의 유효성 검증 X

## Migrations

- Django가 모델에 생긴 변화(필드 추가, 모델 삭제 등)을 DB에 반영하는 방법

> Migraitons 관련 주요 명령어

1. makemigrations
2. migrate

> makemigrations

- 모델을 작성, 변경한 것에 기반한 새로운 migration을 만들 때 사용
- 테이블을 만들기 위한 설계도 생성
- python manage.py makemigrations로 실행

> migrate

- makemigrations로 만든 설계도를 실제 db.sqlite3 DB파일에 반영하는 과정
- 결과적으로 모델에서의 변경사항들과 DB의 스키마가 동기화를 이룸
  - 모델과 DB의 동기화
- python manage.py migrate로 실행

> 기타 명령어

1. showmigrations

   - python mange.py showmigrations로 실행
   - migrations파일들이 migrate 됐는지 안됐는지 여부 확인
   - [X]표시가 있으면 migrate 완료

2. sqlmigrate
   - python manage.py sqlmigrate articles 0001로 실행
   - 해당 migrations 파일이 SQL 문으로 어떻게 해석 될 지 미리 확인 할 수 있음

> 설계도는 어떻게 누가 해석할까?

- ORM

## ORM
