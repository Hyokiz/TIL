# 20220831 TIL

## Django

- ctrl + shift + p > 파이썬 인터프리터 선택 > 가상환경으로 설정

## URL namespace

> 개요

- URL namespace를 사용하면 다른 앱에서 동일한 URL 이름을 사용하는 경우에도 고유하게 사용할 수 있음
- app_name attribute를 작성해 URL namespace를 설정

> 기존 URL tag 변경

- app_name을 지정한 이후에는 url 태그에서 반드시 app_name:url_name 형태로만 사용해야 함. 그렇지 않으면 NoReverseMatch 에러
- NoReverseMatch에러가 났을 때 그 앱의 url 태그 확인.

> URL 참조

- ":"연산자를 사용하여 지정
  - app_name이 articles, URL name이 index인 주소 참조는 articles:index

## Template namespace

> 개요

- Django는 기본적으로 app_name/templates/ 경로에 있는 templates 파일들만 찾을 수 있으며, settings.py의 INSTALLED_APPS에 작성한 app 순서로 template을 검색 후 렌더링

> 디렉토리 생성을 통해 물리적인 이름공간 구분

- 폴더구조를 app_name/templates/app_name/ 형태로 변경
- django templates의 기본 경로 자체를 변경할 수는 없기 때문에 물리적으로 이름 공간을 만드는 것

> 템플릿 경로 변경

- 폴더 구조 변경 후 변경된 경로로 해당하는 모든 부분 수정

> 반드시 Template namespace를 고려해야 할까?

- 단일 앱으로 이루어진 프로젝트라면 상관없음
- 여러 앱이라도 템플릿 이름이 겹치지 않으면 되지만, 대부분 같은 이름 존재

## Django Model

> 개요

- Django는 웹 애플리케이션의 데이터를 구조화하고 조작하기 위한 추상적인 모델을 제공

## Database

> Database

- 체계화된 데이터의 모임
- 조직화된 데이터를 수집하는 저장 시스템

> Database 기본 구조

1. 스키마(Schema)
2. 테이블(Table)

> 스키마(Schema)

- 뼈대(Structure)

> 테이블(Table)

- 필드와 레코드를 사용해 조직된 데이터 요소들의 집합
- 관계(Relation)라고도 부름

1. 필드(field)
   - 속성, 컬럼(Column)
2. 레코드(record)
   - 튜플, 행(Row)

> 필드(field)

- 속성 혹은 컬럼(column)
- 각 필드에는 고유한 데이터 형식 지정
  - int, text 등

> 레코드(record)

- 튜플 혹은 행
- 테이블의 데이터는 레코드에 저장
- 4명의 고객정보 > 4개의 레코드

> PK(Primary Key)

- 기본 키
- 각 레코드의 고유값
- 다른 항목과 절대로 중복되어 나타날 수 없는 단일 값(unique)을 가짐

> PK 예시

- 주민등록번호
  - 주민등록번호는 그 사람을 나타내는 고유한 값

> 쿼리(Query)

- 데이터를 조회하기 위한 명령어
- 조건에 맞는 데이터를 추출, 조작
- Query를 날린다 > 데이터베이스를 조작한다.

## Model

> 개요

- Django는 Model을 통해 데이터에 접속하고 관리
- 사용하는 데이터들의 필수적인 필드들과 동작들 포함
- 일반적으로 각각의 모델은 하나의 데이터베이스 테이블에 매핑
  - 매핑 : 하나의 값을 다른 값으로 대응시키는 것

> Model 작성하기

- 모델 클래스를 작성하는 것은 데이터베이스 테이블의 스키마를 정의하는 것
- models.CharField(max_length=10) : 글자 수 제한을 설정해야함
- models.TextField() : 글자 수 제한이 없음

> Model 이해하기

- 각 모델은 django.models.Model 크래스의 서브 클래스로 표현됨

  - 클래스 상속 기반 형태의 Django 프레임워크 개발

- 클래스 변수명
  - DB 필드의 이름
- 클래스 변수값
  - DB 필드의 데이터 타입

> Django Model Field

- Django는 모델 필드를 통해 테이블의 필드(컬럼)에 저장할 데이터 유형(INT, TEXT 등)을 정의
- 데이터 유형에 따라 다양한 모델 필드 제공
  - DataField(), CharField(), IntegerField()등
  - 공식문서 참고!

> 사용한 모델 필드 알아보기

- CharField(max_length=None, \*\*options)

  - 길이의 제한이 있는 문자열을 넣을 때 사용
  - max_length
    - 필드의 최대 길이(문자)
    - CharField의 필수 인자
    - 데이터베이스와 Django의 유효성 검사에서 활용됨

- TextField(\*\*options)
  - 글자의 수가 많을 때 사용
  - max_length 옵션 작성 시 사용자 입력 단계에서는 반영되지만, 모델과 데이터베이스 단계에는 적용되지 않음(CharField 사용)
    - 실제로 저장될 때 길이에 대한 유효성을 검증하지 않음

> 데이터베이스 스키마

- 지금까지 작성한 models.py는 데이터베이스 스키마를 설계한 것
- 이제 DB에 테이블을 생성하기 위한 설계도 작성이 필요

## Migrations

> 개요

- Django가 모델에 생긴 변화(필드 추가, 모델 삭제 등)를 DB에 반영하는 방법

> Migrations 관련 주요 명령어

1. makemigrations
2. migrate

> makemigrations

- 모델을 작성 혹은 변경한 것에 기반한 새로운 migration(설계도, 청사진 이하 마이그레이션)을 만들 때 사용
- 테이블을 만들기 위한 설계도를 생성하는 것

> migrate

- 모델의 변경사항과 데이터베이스를 동기화
- 설계도를 실제 db.sqlite3 DB파일에 반영

> Migrations 기타 명령어

1. showmigrations

   - migrations 파일들이 migrate 됐는지 안됐는지 여부를 확인하는 용도
   - [x] 표시가 있으면 migrate 완료

2. sqlmigrate
   - 해당 migrations 파일이 SQL 문으로 어떻게 해석 될 지 미리 확인

## 추가 필드 정의

> Model 변경사항 반영하기

- 추가 모델 필드 작성 후 다시 한번 makemigrations 진행
- 1. 다음화면으로 넘어가서 새 컬럼의 기본 값을 직접 입력
- 2. 현재 과정에서 나가고 모델 필드에 default 속성 직접 작성

- 새로운 설계도를 생성했기 때문에 DB와 동기화

> 반드시 기억해야 할 migration 3단계

1. models.py에서 변경사항 발생
2. migrations 파일 생성(설계도 생성)
   - makemigrations
3. DB 반영(모델과 DB의 동기화)
   - migrate

> DateTimeField()

- Python의 datetime.datetime 인스턴스로 표시되는 날짜 및 시간을 값으로 사용하는 필드
- DateField를 상속받는 클래스
- 선택인자

  1. auto_now_add

     - 최초 생성 일자
     - Django ORM이 최초 insert시에만 현재 날짜와 시간으로 갱신

  2. auto_now
     - 최종 수정 일자
     - Django ORM이 save를 할 때마다 현재 날짜와 시간으로 갱신

> Model 정리

- 웹 애플리케이션의 데이터를 구조화하고 조작하기 위한 도구

## ORM

> 개요

- Object-Relational-Mapping
- 호환되지 않는 유형의 시스템 간에(Django <-> SQL) 데이터를 변환하는 프로그래밍 기술

> ORM 장단점

- 장점

  - SQL을 잘 알지 못해도 객체지향 언어로 DB 조작 가능
  - 객체 지향적 접근으로 인한 높은 생산성

- 단점
  - ORM 만으로 완전한 서비스를 구현하기 어려운 경우가 있음

> ORM을 사용하는 이유

- 생산성

## QuerySet API

### 사전 준비

> 외부 라이브러리 설치 및 설정

- 실습 편의를 위한 추가 라이브러리 설치 및 설정

```bash
$ pip install ipython
$ pip install django-extensions
```

```python
# settings.py

INSTALLED_APPS = [
    'articles',
    'django-extensions',
    ...,
]
```

> IPython & django-extensions

- IPython
  - 파이썬 기본 쉘보다 더 강력한 파이썬 쉘
  - django-extensions
- django-extensions
  - Django 확장 프로그램 모음
  - shell_plus, graph model 등 다양한 확장 기능 제공

> Shell

- 운영체제 상에서 다양한 기능과 서비스를 구현하는 인터페이스를 제공하는 프로그램
- 쉘(껍데기)은 사용자와 운영 체제의 내부사이의 인터페이스를 감싸는 층이기 때문에 그러한 이름이 붙음
- "사용자 <-> 쉘 <-> 운영체제"

> Python Shell

- 파이썬 코드를 실행해주는 인터프리터

  - 인터프리터 : 코드를 한 줄 씩 읽어 내려가며 실행하는 프로그램

- 인터렉티브 혹은 대화형 쉘이라고 부름

> Django shell

- ORM 관련 구문 연습을 위해 파이썬 쉘 환경을 사용
- 다만 일반 파이ㅏ썬 쉘을 통해서는 장고 프로젝트 환경에 영향을 줄 수 없기 때문에 Django 환경 안에서 진행할 수 있는 Django 쉘을 사용
- django-extension이 제공하는 더 강력한 shell_plus로 진행

## QuerySet API

> Database API

- Django가 기본적으로 ORM을 제공함에 따른 것으로 DB를 편하게 조작할 수 있도록 도움
- Model을 만들면 Django는 객체들을 만들고 읽고 수정하고 지울 수 있는 DB API를 자동으로 만듦

> Database API 구문

- Article.objects.all()
  - Article : Model class
  - objects : Manager
  - all() : Queryset API

> "obects" manager

- Django 모델이 데이터베이스 쿼리 작업을 가능하게 하는 인터페이스
- "DB를 Python class로 조작할 수 있도록 여러 메서드를 제공하는 manager"

> Query

- 데이터베이스에 특정한 데이터를 보여 달라는 요청
  - "쿼리문을 작성한다."
    - 원하는 데이터를 얻기 위해 데이터베이스에 요청을 보낼 코드를 작성한다.
- 이 때, 파이썬으로 작성한 코드가 ORM에 의해 SQL로 변환되어 데이터베이스에 전달되며, 데이터베이스의 응답 데이터를 ORM이 QuerySet이라는 자료 형태로 변환하여 우리에게 전달

> QuerySet

- 데이터베이스에게서 전달 받은 객체 목록
  - 순회 가능, 데이터를 불러와 사용 가능
- Django ORM을 통해 만들어진 자료형. 필터, 정렬 등 가능
- "objects" manager를 사용하여 복수의 데이터를 가져오는 queryset method를 사용할 때 반환되는 객체

> QuerySet API

- QuerySet과 상호작용하기 위해 사용하는 도구

## QuerySet API 익히기

> CRUD

- Create, Read, Update, Delete
  - 생성, 조회, 수정, 삭제

### CREATE

> 데이터 객체를 만드는 3가지 방법

- 첫 번째 방법

  1. article = Article()
     - 클래스를 통한 인스턴스 생성
  2. article.title
     - 클래스 변수명과 같은 이름의 인스턴스 변수를 생성 후 값 할당
  3. article.save()
     - 인스턴스로 save 메서드 호출

  - save메서드를 호출해야 DB에 데이터가 저장된다.

- 두 번째 방법

  - 인스턴스 생성 시 초기 값을 함께 작성하여 생성

- 세 번째 방법
  - QuerySet API 중 create() 메서드 활용

> .save()

- Saving object
- 객체를 데이터베이스에 저장
- 데이터 생성 시 save를 호출하기 전에 객체의 id값은 None
  - id값은 Django가 아니라 DB에서 계산되기 때문
- 단순히 모델 클래스를 통해 인스턴스를 생성하는 것은 DB에 영향을 미치지 않기 때문에 반드시 save를 호출해야 테이블에 레코드가 생성됨

## READ

> 개요

- QuerySet API method를 사용해 데이터를 다양하게 조회
- QuerySet API method는 크게 두가지
  1. Methods that "return new querysets"
  2. Methods that "do not return querysets"

> all()

- QuerySet return
- 전체 데이터 조회

> get()

- 단일 데이터 조회
- 객체를 찾을 수 없으면 DoesNotExist, 둘 이상 객체를 찾으면 MultipleObjectsReturned.
- 위와 같은 특징을 가지고 있기 때문에 primary key와 같이 고유성을 보장하는 조회에서 사용해야 함.

> filter()

- 지정된 조회 매개 변수와 일치하는 객체를 포함하는 새 QuerySet을 반환
  - 조회된 객체가 없거나 1개여도 QuerySet을 반환

> Field lookups

- 특정 레코드에 대한 조건을 설정하는 방법
- QuerySet 메서드 filter(), exclude() 및 get()에 대한 키워드 인자로 지정됨
- 다양한 built-in lookups는 공식문서를 참고

## UPDATE

> Update 과정

1. 수정하고자 하는 article 인스턴스 객체를 조회 후 반환 값 저장
2. article 인스턴스 객체의 인스턴스 변수 값을 새로운 값으로 할당
3. save() 인스턴스 메서드 호출

## Delete

> Delete 과정

1. 삭제하고자 하는 article 인스턴스 객체를 조회 후 반환 값을 저장
2. delete() 인스턴스 메서드 호출

> \_\_str\_\_()

- 표준 파이썬 메서드인 str()을 정의하여 각각의 object가 사람이 읽을 수 있는 문자열을 반환하도록 할 수 있음

## CRUD with view functions
