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

- 장점

  - SQL을 몰라도 객체지향 언어로 DB 조작 가능
  - 객체 지향적 접근으로 인한 높은 생산성

- 단점
  - ORM 만으로 완전한 서비스 구현 힘듦

> ORM을 사용하는 이유

- 생산성

> Model 변경 사항 반영하기

- models.py에 변경사항이 생겼을 때
- 추가 모델 필드 작성 후 한번더 makemigrations

```py
# articles/models.py

class Article(models.Model):
    created_at = models.DateTimeField(auto_now_add=True)
    updated_at = models.DateTimeField(auto_now=True)
```

- python manage.py makemigrations
- 새로운 설계도를 생성했기 때문에 DB와 동기화
  - python manage.py migrate

> 반드시 기억해야 할 migration 3단ㄷ계

1. models.py에서 변경 사항 발생
2. migrations 파일 생성
   - makemigrations
3. DB반영
   - migrate

> DateTimeField()

- Python의 datetime.datetime 인스턴스로 표시되는 날짜 및 시간을 값으로 사용하는 필드
- DateField를 상속받는 클래스
- 선택 인자

  1. auto_now_add

     - 최초 생성 일자
     - 최초만 현재 날짜와 시간으로 갱신

  2. auto_now
     - 최종 수정 일자
     - save를 할때마다 갱신

> Model 정리

- 웹 애플리케이션의 데이터를 구조화하고 조작하기 위한 도구

## QuerySet API 사전준비

> 외부 라이브러리 설치

- pip install ipython
- pip install django-extensions

```py
# settings.py

INSTALLED_APPS[
    'articles',
    'django_extensions',
    ...,
]
```

- 패키지 목록 업데이트
  - pip freeze > requirements.txt

> IPython and django-extensions

- IPython

  - 파이썬 기본 쉘보다 더 강력한 파이썬 쉘

- django-extensions
  - Django 확장 프로그램 모음
  - shell_plus, graph model 등 다양한 확장 기능 제공

> Shell

- 운영체제 상 다양한 기능과 서비스를 구현하는 인터페이스를 제공하는 프로그램
- 셸은 사용자와 운영 체제의 내부사이의 인터페이스를 감싸는 층

> Python Shell

- 파이썬 코드를 실행해주는 인터프리터

  - 인터프리터 : 코드를 한 줄 씩 읽어 내려가며 실행하는 프로그램

- 인터렉티브 or 대화형 shell

> Django shell

- ORM 관련 구문 연습을 위해 파이썬 쉘 사용
- 일반 파이썬 쉘로는 장고 프로젝트 환경에 영향 X
- python manage.py shell_plus

## QuerySet API

> Database API

- Django가 기본적으로 ORM 제공 > DB 조작 편하게
- Model을 만들면 Django는 객체들을 만들고 읽고 수정하고 지울 수 있는 DB API를 자동으로 만듦

> Database API 구문

- Article.objects.all()

> "objects" manager

- Django 모델이 데이터베이스 쿼리 작업을 가능하게 하는 인터페이스
- Django는 기본적으로 모든 Django 모델 클래스에 대해 objects 라는 Manager 객체를 자동으로 추가
- DB를 Python class로 조작할 수 있도록 여러 메서드를 제공하는 manager

> Query

- 데이터베이스에 특정한 데이터를 보여 달라는 요청
  - 쿼리문을 작성한다 == 원하는 데이터를 얻기 위해 데이터베이스에 요청을 보낼 코드를 작성한다.

> QuerySet

- 데이터베이스에게서 전달 받은 객체 목록(데이터 모음)
  - 순회가 가능한 데이터로써 1개 이상의 데이터를 불러와 사용할 수 있음
- Django ORM을 통해 만들어진 자료형, 필터를 걸거나 정렬 등 수행

## QuerySet API 익히기

> CRUD

- Create / Read / Update / Delete

## CREATE

> 데이터 객체를 만드는 3가지 방법

- 첫 번째 방법

  1. article = Article()

     - 클래스를 통한 인스턴스 생성

  2. article.title

     - 클래스 변수명과 같은 이름의 인스턴스 변수를 생성 후 값 할당

  3. article.save()
     - 인스턴스로 save 메서드 호출
     - save 메서드를 호출해야 DB에 데이터가 저장된다.

- 두 번째 방법

  - 인스턴스 생성 시 초기 값을 함께 작성하여 생성
    - article = Article(title='second', content='django!')
    - article.save()

- 세 번째 방법

  - QuerySet API 중 create() 메서드 활용
  - Article.objects.create(title='third', content='django!')
  - 바로 데이터가 반환된다.

> .save()

- 객체를 데이터베이스에 저장
- save를 호출하기 전에는 객체의 id 값은 None
- save를 호출해야 테이블에 레코드가 생성

## READ

- QuerySet API method는 크게 2가지

  1. Methods that "return new querysets"
  2. Methods that "do not return querysets"

> all()

- Queryset return
- 전체 데이터 조회

> get()

- 단일 데이터 조회
- 찾을수 없다면 DoesNotExist, 둘 이상은 MultipleObjectsReturned 예외 발생
- primary key와 같이 고유성을 보장하는 조회에서 사용

> filter()

- 지정된 조회 매개 변수와 일치하는 객체를 포함하는 새 QuerySet 반환
- 조회된 객체가 없거나 1개여도 반환

> Update 과정

1. 수정하고자 하는 article 인스턴스 객체를 조회 후 반환값 저장
2. article 인스턴스 객체의 인스턴스 변수 값을 새로운 값으로 할당
3. save() 인스턴스 메서드 호출

```py
article = Article.objects.get(pk=1)

# 인스턴스 변수 변경
article.title = 'byebye'

# 저장
article.save()

# 정상적으로 변경
article.title
# 'byebye'
```

## DELETE

> Delete 과정

1. 삭제하고자 하는 article 인스턴스 객체를 조회 후 반환 값을 저장
2. delete() 인스턴스 메서드 호출
   - article.delete()

> \_\_str\_\_()

- 표준 파이썬 클래스 메서드인 str()을 정의하여 각각의 object가 사람이 읽을 수 있는 문자열을 반환하도록 할 수 있음

## CRUD with view functions

> 사전 준비

- base 템플릿 작성
- url 분리 및 연결

```py
# articles/urls.py

from django.urls import path

app_name = 'articles'
urlpatterns = [

]

# crud/urls.py

from django.contrib import admin
from django.urls import path, include

urlpatterns = [
    path('admin/', admin.site.urls),
    path('articles/', include('articles.urls')),
]
```

- index 페이지 작성

## READ 1(index page)

> 전체 게시글 조회

- index 페이지에서는 전체 게시글을 조회해서 출력한다.

```py
# articles/views.py

from .models import Article

def index(request):
    articles = Article.objects.all()
    context = {
        'articles' : articles,
    }
    return render(request, 'articles/index.html', context)
```

## CREATE

> NEW

```py
# articles/urls.py

urlpatterns = [
    path('', views.index, name='index'),
    path('new/', views.new, name='new'),
]

# articles/views.py

def new(request):
    return render(request, 'articles/new.html')
```

```html
<!-- templates/articles/new.html -->

<form action="#" method="GET"></form>
```

> Create

```py
# articles/urls.py

urlpatterns = [
    ...,
    path('create/', views.create, name='create'),
]

# articles/views.py

def create(request):
    title = request.GET.get('title')
    content = request.GET.get('content')
    article = Article(title=title, content=content)
    article.save()
    return render(request, 'articles/create.html')
```

- 이 생성방식을 사용하는 이유
  - create 메서드가 더 간단해 보이지만 추후 데이터가 저장되기 전에 유효성 검사 과정 거치게 될 예정
  - 유효성 검사가 진행된 후 save 메서드가 호출되는 구조

> 2가지 문제점 발생

1. 게시글 작성 후 index 페이지가 출력되나 게시글은 조회되지 않음

   - create 함수에서 index.html 문서를 렌더링 할때 context 데이터와 함께 렌더링 하지 않음
   - index 페이지 url로 다시 요청을 보내면 정상적으로 출력

2. 게시글 작성 후 URL 은 여전히 create

   - idnex view 함수를 통해 렌더링 된 것이 아니기 때문
   - index view 함수의 반환 값이 아닌 단순히 index 페이지만 렌더 되었을 뿐

> Django shortcut function - redirect()

- 인자에 작성된 곳으로 요청을 보냄
- 사용 가능한 인자
  1. view name(URL pattern name) : return redirect('articles:index')
  2. absolute or relative URL : return redirect('/articles/')

```py
# articles/views.py

from django.shortcuts import render, redirect

def create(request):
    title = request.GET.get('title')
    content = request.GET.get('content')
    article = Article(title=title, content=content)
    article.save()
    return redirect('articles:index')
```

> redirect 동작 이해하기

- 동작원리

  1. 클라이언트가 create url로 요청
  2. create view 함수의 redirect 함수가 302 status code 응답
  3. 응답 받은 브라우저는 redirect 인자가 담긴 주소(index)로 사용자를 이동시키기 위해 index url로 Django에 재요청
  4. index page를 정상적으로 응답 받음(200 status code)

> 302 Found

- HTTP response status code 중 하나
- 해당 상태 코드를 응답 받으면 브라우저는 사용자를 해당 URL 의 페이지로 이동

> HTTP response status code

- 클라이언트에게 특정 HTTP 요청이 성공적으로 완료되었는지 여부를 알려줌
- 응답은 5개의 그룹으로 나뉘어짐

  1. Informational responses (1xx)
  2. Successful responses (2xx)
  3. Redirection messages (3xx)
  4. Client error responses (4xx)
  5. Server error responses (5xx)

> HTTP method GET 재검토

- 데이터를 조회하는 것이 아닌 작성을 원하는 요청

> HTTP request method

- GET

  - 특정 리소스를 가져오도록 요청
  - 데이터를 가져올때만
  - DB에 변화 없음
  - CRUD 의 R

- POST
  - 서버로 데이터 전송할 때 사용
  - 서버에 변경 사항을 만듦
  - 리소스 생성/변경을 위해 데이터를 HTTP body에 담아 전송
  - URL로 보내지지 않음
  - CRUD 의 C, U, D

> POST method 적용하기

```html
<!-- templates/articles/new.html -->

<form action="{% url 'articles:create' %}" method="POST"></form>
```

```py
# articles/views.py

def craete(request):
    title = request.POST.get('title')
    content = request.POST.get('content')
    article = Article(title=title, content=content)
    article.save()
    return render(request, 'articles/create.html')
```

> 403 Forbidden

- 서버에 요청이 전달되었으나, 권한 때문에 거절
- 게시글을 작성할 권한이 없다 > 작성자가 누구인지 모름
- 모델(DB)을 조작하는 것은 단순 조회와 달리 최소한의 신원 확인 필요

> CSRF

- 사이트 간 요청 위조
- 사용자가 자신의 의지와 무관하게 공격자가 의도한 행동을 하여 특정 웹페이지를 보안에 취약하게 하거나 수정, 삭제 등의 작업을 하게 만드는 공격 방법

> CSRF 공격 방어

- Security Toekn 사용 방식 (CSRF Token)
  - 사용자의 데이터에 임의의 난수 값을 부여해 매 요청마다 해당 난수 값을 포함시켜 전송

> csrf_token 템플릿 태그

- 해당 태그가 없다면 403 forbidden
- form 밑에 작성

## READ 2

- 모든 게시글 마다 뷰 함수와 템플릿 파일을 만들 수 없음
  - 글의 번호를 활용하여 하나의 뷰 함수와 템플릿 파일로 대응

> urls

- URL로 특정 게시글을 조회할 수 있는 번호를 받음

```py
# articles/urls.py

urlpatterns = [
    ...,
    path('<int:pk>/', views.detail, name='detail'),
]
```

> views

- Article.objects.get(pk=pk)에서 오른쪽 pk는 variable routing을 통해 받은 pk, 왼쪽 pk는 DB에 저장된 레코드의 id 컬럼

```py
# articles/views.py

def detail(request, pk):
    article = Article.objects.get(pk=pk)
    context = {
        'article' : article,
    }
    return render(request, 'articles/detail.html', context)
```

> redirect 인자 변경

```py
# articles/views.py

def create(request):
    return redirect('articles:detail', article.pk)
```

## DELETE

> urls

- 모든 글을 삭제하는 것이 아니라 삭제하고자 하는 특정 글 조회 후 삭제

```py
# articles/urls.py

urlpatterns = [
    ...,
    path('<int:pk>/delete/', views.delete, name='delete'),
]
```

> views

```py
# articles/views.py

def delete(request, pk):
    article = Article.objects.get(pk=pk)
    article.delete()
    return redirect('articles:index')
```

> templates

- Detail 페이지에 작성하며 DB에 영향을 미치기 때문에 POST method 사용

## UPDATE

- create 과 마찬가지로 2개의 view 함수 필요
- 사용자의 입력을 받을 페이지 렌더링
  - edit
- 사용자가 입력한 데이터를 전송받아 DB에 저장
  - update

> Edit

```py
# articles/urls.py

urlpatterns = [
    path('<int:pk>/edit/', views.edit, name='edit'),
]

# articles/views.py

def edit(request, pk):
    article = Article.objects.get(pk=pk)
    context = {
        'article' : article,
    }
    return render(request, 'articles/edit.html', context)
```

> Update 로직

```py
# articles/urls.py

urlpatterns = [
    path('<int:pk>/update/', views.update, name='update'),
]

# articles/views.py

def update(request, pk):
    article = Article.objects.get(pk=pk)
    article.title = request.POST.get('title')
    article.content = request.POST.get('content')
    article.save()
    return redirect('articles:detail', article.pk)
```

## Admin site

- 관리자 페이지
  - 모델 class 를 admin.py에 등록하고 관리

> admin 계정 생성

- python manage.py createsuperuser

> admin 에 모델 클래스 등록

- 모델의 record 를 보기 위해서는 admin.py에 등록 필요

```py
# articles/admin.py

from django.contrib import admin
from .models import Article

admin.site.register(Article)
```

## 마무리

- Model

  - Django는 Model을 통해 데이터에 접속하고 관리

- ORM

  - 객체 지향 프로그래밍을 이용한 DB 조작

- Migrations

  - 모델에 생긴 변화를 DB에 반영하는 방법

- HTTP request and response
  - 요청에 행동을 표현하는 HTTP request method
  - 요청에 대한 성공 여부 응답을 숫자로 표현하는 HTTP response status codes

## Django Form

- 유효성 검증 필요
- Django Form은 이 과정에서 과중한 작업과 반복 코드를 줄여줌

> Form 에 대한 Django 의 역할

- Form 은 유효성 검사 도구 중 하나로 중요한 방어 수단
- Form과 관련한 유효성 검사를 단순화하고 자동화 할 수 있는 기능 제공
  - 개발자가 필요한 핵심 부분만 집중할 수 있도록 돕는 프레임워크

> Django는 Form에 관련된 작업의 세 부분 처리

1. 렌더링을 위한 데이터 준비 및 재구성
2. 데이터에 대한 HTML forms 생성
3. 클라이언트로부터 받은 데이터 수신 및 처리

## The Django Form Class

> Form Class 선언

- Model Class를 선언하는 것과 비슷
- Model과 마찬가지로 상속을 통해 선언
- 앱 폴더에 forms.py 를 생성 후 ArticleForm Class 선언

```py
# articles/forms.py

from django import forms

class ArticleForm(forms.Form):
    title = forms.CharField(max_length=10)
    content = forms.CharField()
```

> new의 view함수 업데이트

```py
# articles/views.py

from .forms import ArticleForm

def new(request):
    form = ArticleForm()
    context = {
        'form' : form,
    }
    return render(request, 'articles/new.html', context)
```

> From rendering options

- label & input 쌍에 대한 3가지 출력 옵션

1. as_p()

   - 각 필드가 단락(p태그)으로 감싸져서 렌더링

2. as_ul()

   - 각 필드가 목록 항목(li 태그)으로 감싸져서 렌더링
   - ul태그는 직접 작성

3. as_table()

   - 각 필드가 테이블(tr태그) 행으로 감싸져서 렌더링

- 특별한 상황이 아니면 as_p()만 사용

> Django의 2가지 HTML 요소 표현

1. Form fields

   - 입력에 대한 유효성 검사 로직 처리
   - 템플릿에서 직접 사용됨

2. Widgets

   - 웹 페이지의 HTML input 요소 렌더링 담당

     - input 요소의 단순한 출력 부분을 담당

   - Widgets은 반드시 form fields에 할당 됨

## Widgets

- 단순히 HTML 렌더링 처리, 유효성 검증과 관계 없음

> Textarea 위젯 적용

```py
# articles/forms.py

class ArticleForm(forms.Form):
    title = forms.CharField(max_length=10)
    content = forms.CharField(widget=forms.Textarea)
```

> Form fields와 widget 응용하기

```py
# articles/forms.py

class ArticleForm(forms.Form):
    nation_a = 'kr'
    nation_b = 'ch'
    nation_c = 'jp'
    nations_choices =[
        (nation_a, '한국'),
        (nation_b, '중국'),
        (nation_c, '일본'),
    ]
    title = forms.CharField(max_length=10)
    content = forms.CharField(widget=forms.Textarea())
    nation = forms.ChoiceField(choices=nations_choices)
```

## Django ModelForm

- ModelForm을 사용하면 이러한 Form을 더 쉽게 작성

> ModelForm 선언

```py
# articles/forms.py

from django import forms
from .models import Article

class ArticleForm(forms.ModelForm):

    class Meta:
        model = Article
        fields = '__all__'
```

> ModelForm 에서의 Meta Class

- ModelForm 의 정보를 작성하는 곳
- ModelForm을 사용할 경우 참조할 모델이 있어야 하는데, Meta class의 model 속성이 이를 구성

  - 참조하는 모델에 정의된 field 정보를 Form에 적용

- fields 속성에 all을 사용하여 모델의 모든 필드 포함 가능
- exclude를 사용하여 포함하지 않을 필드 지정 가능

> Meta data

- 데이터를 표현하기 위한 데이터

> 참조값과 반환값

- Article이라는 클래스를 호출하지 않고 작성하지 않는 이유는 ArticleForm이 해당 클래스를 필요한 시점에 사용하기 위함

## ModelForm with view functions

> CREATE

- 유효성 검사를 통과하면

  - 데이터 저장 후
  - 상세 페이지로 리다이렉트

- 통과하지 못하면
  - 작성 페이지로 리다이렉트

```py
# articles/views.py

def create(request):
    form = ArticleForm(request.POST)
    if form.is_valid():
        article = form.save()
        return redirect('articles:detail', article.pk)
    return redirect('articles:new')
```

> is_valid method

- 유효성 검사 실행, 유효한지 boolean으로 반환

> save() method

- form 인스턴스에 바인딩 된 데이터를 통해 데이터베이스 객체를 만들고 저장
- ModelForm의 하위 클래스는 키워드 인자 isntance 여부를 통해 생성할 지, 수정할 지를 결정함
  - 제공되지 않은 경우 save()는 지정된 모델의 새 인스턴스를 만듦(CREATE)
  - 제공되면 save()는 해당 인스턴스를 수정(UPDATE)

```py
# CREATE
form = ArticleForm(request.POST)
form.save()

# UPDATE
form = ArticleForm(request.POST, instance=article)
form.save()
```

> form 인스턴스의 errors 속성

- 유효성 검증을 실패했을 때 사용자에게 실패 결과 메세지 출력 가능

```py
# articles/views.py

def create(request):
    form = ArticleForm(request.POST)
    if form.is_valid():
        article = form.save()
        return redirect('articles:detail', article.pk)
    context = {
        'form' : form,
    }
    return render(request, 'articles/new.html', context)
```

> UPDATE

- ModelForm의 인자 instance는 수정 대상이 되는 객체를 지정

1. request.POST

   - 사용자가 form을 통해 전송한 데이터(새로운 데이터)

2. instance

   - 수정이 되는 대상

> UPDATE

- edit - view 수정

```py
# articles/views.py

def edit(request, pk):
    article = Article.objects.get(pk=pk)
    form = ArticleForm(instance=article)
    context = {
        'article' : article,
        'form' : form,
    }
    return render(request, 'articles/edit.html', context)
```

- update - view 수정

```py
# articles/views.py

def update(request, pk):
    article = Article.objects.get(pk=pk)
    form = ArticleForm(request.POST, instance=article)
    if form.is_valid():
        form.save()
        return redirect('articles:detail', article.pk)
    context = {
        'form' : form,
        'article' : article,
    }
    return render(request, 'articles/edit.html', context)
```

> Form과 ModelForm

- ModelForm이 Form보다 더 좋은 것이 아니라 역할이 다름

- Form

  - 사용자의 입력을 필요로 하며 입력 데이터가 DB 저장에 사용되지 않거나 일부 데이터만 사용될 때
  - ex. 로그인 - 인증 과정에만 사용 후 별도로 DB에 저장하지 않음

- ModelForm

  - 사용자의 입력을 필요로 하며 입력을 받은 것을 그대로 DB 필드에 맞춰 저장할 때
  - 데이터의 유효성 검사가 끝나면 데이터를 각각 어떤 레코드에 맵핑해야 할지 이미 알고있기 때문에 곧바로 save() 호출이 가능

## Widgets 활용하기

> 위젯을 작성하는 방법

```py
# articles/forms.py

class ArticleForm(forms.ModelForm):
    title = forms.CharField(
        label='제목',
        widget=forms.TextInput(
            attrs={
                'class' : 'my-title',
                'placeholder' : 'Enter the title',
            }
        ),
    )

    class Meta:
        model = Article
        fields = '__all__'
```

> Widgets 활용하기

```py
# articles/forms.py

class ArticleForm(forms.ModelForm):
    title = forms.CharField(
        label='제목',
        widget=forms.TextInput(
            attrs={
                'class' : 'my-title',
                'placeholder' : 'Enter the title',
                'maxlength' : 10,
            }
        ),
    )
    content = forms.CharField(
        label='내용',
        widget=forms.Textarea(
            attrs={
                'class' : 'my-content',
                'placeholder' : 'Enter the content',
                'rows' : 5,
                'cols' : 50,
            }
        ),
        error_messages={
            'required' : 'Please enter your content'
        }
    )

    class Meta:
        model = Article
        fields = '__all__'
```

## Handling HTTP requests

- 공통점

  - new-create는 모두 CREATE 로직을 구현하기 위한 공통 목적
  - edit-update는 모두 UPDATE 로직을 구현하기 위한 공통 목적

- 차이점

  - new와 edit은 GET요청에 대한 처리만을
  - create와 update는 POST 요청에 대한 처리만을 진행

- 이 공통점과 차이점을 기반으로 하나의 view 함수에서 method 에 따라 로직이 분리되도록 변경

> CREATE

- new와 create view 함수 합침
- 각각의 역할은 request.method 값을 기준으로 나뉨

```py
# articles/views.py

def create(request):
    if request.method == 'POST':
        form = ArticleForm(request.POST)
        if form.is_valid():
            article = form.save()
            return redirect('articles:detail', article.pk)
    else:
        form = ArticleForm()
    context = {
        'form' : form,
    }
    return render(request, 'articles/create.html', context)
```

> Update

```py
# articles/views.py

def update(request, pk):
    article = Article.objects.get(pk=pk)
    if request.method == 'POST':
        form = ArticleForm(request.POST, instance=article)
        if form.is_valid():
            form.save()
            return redirect('articles:detail', article.pk)
    else:
        form = ArticleForm(instance=article)
    context = {
        'form' : form,
        'article' : article,
    }
    return render(request, 'articles/update.html', context)
```

- POST 요청에 대해서만 삭제가 가능하도록 수정

```py
# articles/views.py

def delete(request, pk):
    article = Article.objects.get(pk=pk)
    if request.method == 'POST':
        article.delete()
        return redirect('articles:index')
    return redirect('articles:detail', article.pk)
```

## View decorators

> 데코레이터

- 기존에 작성된 함수에 기능을 추가하고 싶을 때, 해당 함수를 수정하지 않고 기능을 추가

## Allowed HTTP methods

- django.views.decorators.http의 데코레이터를 사용하여 요청 메서드를 기반으로 접근 제한
- 메서드 목록

  1. require_http_methods()
  2. require_POST()
  3. require_safe()

> require_http_methods()

- View 함수가 특정한 요청 method만 허용하도록 하는 데코레이터

```py
# views.py

from django.views.decorators.http import require_http_methods

@require_http_methods(['GET', 'POST'])
def create(request):
    pass

@require_http_methods(['GET', 'POST'])
def update(request, pk):
    pass
```

> require_POST

- POST 요청 method만 허용하도록 하는 데코레이터

```py
# views.py

from django.views.decorators.http import require_http_methods, require_POST

@require_POST
def delete(request, pk):
    article = Article.objects.get(pk=pk)
    article.delete()
    return redirect('articles:index')
```

> require_safe()

- require_GET이 있지만 Django에서는 require_safe 사용 권장

```py
# views.py

from django.views.decorators.http import require_http_methods, require_POST, require_safe

@require_safe
def index(request):
    ...

@require_safe
def detail(request, pk):
    ...

```

## 마무리

- Django Form Class

  - Django 프로젝트의 주요 유효성 검사 도구
  - 공격 및 데이터 손상에 대한 중요한 방어 수단
  - 강력한 편의 제공

- View 함수 구조 변화

  - HTTP requests 처리에 따른 구조 변화

## Django authentication system

- 인증과 권한 부여를 함께 제공, 일반적으로 인증 시스템이라고 함

> 개요

- Authentication(인증)

  - 신원 확인

- Authorization(권한, 허가)

  - 권한 부여

> 사전 설정

- 두 번째 app accounts 생성 및 등록

- url 분리 및 매핑

```py
# accounts/urls.py

from django.urls import path
from . import views

app_name = 'accounts'
urlpatterns = [

]

# crud/urls.py

urlpatterns = [
    ...,
    path('accounts/', include('accounts.urls')),
]
```

## Substituting a custom User model

> 개요

- Custom User Model로 대체하기
- 대부분 개발 환경에서 기본 User Model을 Custom User Model로 대체함

- 일부 프로젝트에서는 django에서 제공하는 기본 인증 요구사항이 적절하지 않을 수 있음
- AUTH_USER_MODEL 설정 값으로 Default User Model을 재정의 할 수 있도록 함

> AUTH_USER_MODEL

- 프로젝트에서 User를 나타낼 때 사용하는 모델
- 프로젝트 진행 중 변경 불가
- 프로젝트 시작 시 설정하기 위한 것
  - 즉 첫번째 마이그레이션 전에 확정 지어야 하는 값

## How to substituting a custom User Model

> 대체하기

- AbstractUser를 상속받는 커스텀 User 클래스 작성
- 기존 User 클래스도 AbstractUser를 상속받기 때문에 같은 모습

```py
# accounts/models.py

from django.contrib.auth.models import AbstractUser

class User(AbstractUser):
    pass
```

- Django 프로젝트에서 User를 나타내는데 사용하는 모델을 방금 생성한 커스텀 User 모델로 지정

```py
# settings.py

AUTH_USER_MODEL = 'accounts.User'
```

- admin.py 에 커스텀 User 모델 등록
  - 기존 User 모델이 아니기 때문에 등록하지 않으면 admin site에 출력되지 않음

```py
# accounts/admin.py

from django.contrib import admin
from django.contrib.auth.admin import UserAdmin
from .models import User

admin.site.register(User, UserAdmin)
```

> AbstractUser

- 관리자 권한과 함께 완전한 기능을 가지고 있는 User model을 구현하는 추상 기본 클래스

> 프로젝트 중간에 AUTH_USER_MODEL 변경하기

- 중간 변경은 권장하지 않음(프로젝트 처음에 진행해야 함)

> 데이터베이스 초기화

- 수업 진행을 위한 데이터베이스 초기화 후 마이그레이션(프로젝트 중간일 경우)

1. migrations 파일 삭제

   - migrations 폴더 및 init.py는 삭제하지 않음
   - 번호가 붙은 파일만 삭제

2. db.sqlite3 삭제
3. migrations 진행

   - makemigrations
   - migrate

> custom User 로 변경된 테이블 확인

- 이제 auth_user 테이블이 아니라 accounts_user 테이블 사용

> 반드시 User 모델을 대체해야 할까?

- 강력 권장
- 기본 User 모델과 동일하게 작동하면서도 필요한 경우 나중에 맞춤 설정할 수 있기 때문

## HTTP

- Hyper Text Transfer Protocol
- HTML 문서와 같은 리소스들을 가져올 수 있도록 해주는 프로토콜

> 특징

1. 비 연결 지향

- 서버는 요청에 대한 응답을 보낸 후 연결 끊음

2. 무상태

- 연결을 끊는 순간 서버 간의 통신이 끝나며 상태 정보가 유지되지 않음

> 어떻게 로그인 상태를 유지할까?

- 지속적인 상태 유지를 위해 쿠키와 세션이 존재

## 쿠키(Cookie)

- 작은 데이터 조각
- 쿠키를 저장해 두었다가, 동일한 서버에 재요청 시 저장된 쿠키를 함께 전송

> 사용 목적

1. 세션 관리

   - 로그인, 아이디 자동완성, 장바구니 등

2. 개인화

   - 사용자 선호, 테마 등 설정

3. 트래킹

   - 사용자 행동 기록 및 분석

> 세션

- 사이트와 특정 브라우저 사이의 상태 유지
- session id는 세션을 구별하기 위해 필요하며, 쿠키에는 session id 만 저장

> 쿠키 수명

1. Session cookie

   - 현제 새션이 종료되면 삭제
   - 브라우저 종료와 함께 삭제

2. Persistent cookies

- expires 속성에 지정된 날짜 혹은 지정된 기간이 지나면 삭제됨

> Session in Django

- database-backed sessions 저장 방식을 기본 값으로 사용
  - session 정보를 django_session 테이블에 저장

## Authentication in Web requests

## Login

> 로그인 페이지 작성

```py
# accounts/views.py

from django.contrib.auth.forms import AuthenticationForm

def login(request):
    if request.method == 'POST':
        pass
    else:
        form = AuthenticationForm()
    context = {
        'form' : form,
    }
    return render(request, 'accounts/login.html', context)
```

> 로그인 로직 작성

- login(request, user, backend=None)

```py
from django.shortcuts import render, redirect
from django.contrib.auth import login as auth_login

def login(request):
    if request.method == 'POST':
        form = AuthenticationForm(request, request.POST)
        if form.is_valid():
            auth_login(request, form.get_user())
            return redirect('articles:index')
    else:
        form = AuthenticationForm()
    context = {
        'form' : form,
    }
    return render(request, 'accounts/login.html', context)

```

> get_user()

- AuthenticationForm의 인스턴스 메서드
- 유효성 검사를 통과했을 경우 로그인 한 사용자 객체 반환

## Authentication with User

> 현재 로그인 되어있는 유저 정보 출력하기

- 템플릿에서 인증 관련 데이터를 출력하는 방법
- {{ user }}

- 사용할 수 있는 이유?
  - settings.py의 context processors 설정 값 때문

> context processors

- 템플릿이 렌더링 될 때 호출이 가능한 컨텍스트 데이터 목록
- django에서 자주 사용하는 데이터 목록을 미리 템플릿에 로드 해 둔 것

> django.contrib.auth.context_processors.auth

- 현재 로그인 한 사용자를 나타내는 User 클래스의 인스턴스가 템플릿 변수 {{ user }}에 저장됨

## Logout

> logout()

- logout(request)
- 반환값 없음
- 로그인하지 않은 경우 오류 발생 안함
- 다음 두 가지 일 처리

  1. 현재 요청에 대한 session data를 DB에서 삭제
  2. 클라이언트의 쿠키에서도 sessionid를 삭제

```py
# accounts/views.py

from django.contrib.auth import logout as auth_logout

def logout(request):
    auth_logout(request)
    return redirect('articles:index')
```

## 회원가입

> UserCreationForm

- 주어진 username과 password로 권한이 없는 새 user 를 생성하는 ModelForm
- 3개의 필드를 가짐

  1. username
  2. password1
  3. password2

> 회원 가입 페이지 작성

```py
# accounts/views.py

from django.contrib.auth.forms import AuthenticationForm, UserCreationForm

def signup(request):
    if request.method == 'POST':
        pass
    else:
        form = UserCreationForm()
    context = {
        'form' : form,
    }
    return render(request, 'accounts/signup.html', context)
```

> 회원가입 로직 작성

```py
# accounts/views.py

def signup(request):
    if request.method == 'POST':
        form = UserCrationForm(request.POST)
        if form.is_valid():
            form.save()
            return redirect('articles:index')
    else:
        form = UserCreationForm()
    context = {
        'form' : form,
    }
    return render(request, 'accounts/signup.html', context)
```

## Custom user

> AbstractBaseUser의 모든 subclass와 호환되는 forms

- 아래 Form 클래스는 User 모델을 대체하더라도 커스텀 하지 않아도 사용 가능

  1. AuthenticationForm
  2. SetPasswordForm
  3. PasswordChangeForm
  4. AdminPasswordChangeForm

- 기존 User 모델을 참조하는 Form이 아니기 때문

> 커스텀 유저 모델을 사용하려면 바꿔야하는 forms

1. UserCreationForm
2. UserChangeForm

> UserCreationForm() 커스텀하기

```py
# accounts/forms.py

from django.contrib.auth import get_user_model
from django.contrib.auth.forms import UserCreationForm, UserChangeForm

class CustomUserCrationForm(UserCrationForm):

    class Meta(UserCreationForm.Meta):
        model = get_user_model()

class CustomUserChangeForm(UserChangeForm):

    class Meta(UserChangeForm.Meta):
        model = get_user_model()

```

> get_user_model()

- 현재 프로젝트에서 활성화된 사용자 모델을 반환
- 직접 참조하지 않는 이유

  - user모델을 커스텀 한 상황에서는 커스텀 user 모델을 자동으로 반환해주기 때문

- 직접 참조하는 대신 get_user_model로 참조해야한다고 강조

> CustomUserCreationForm()으로 대체하기

```py
# accounts/views.py

from django.contrib.auth.forms import AuthenticationForm, UserCreationForm
from .forms import CustomUserCreationForm, CustomUserChangeForm

def signup(request):
    if request.method == 'POST':
        form = CustomUserCreationForm(request.POST)
        if form.is_valid():
            form.save()
            return redirect('articles:index')
    else:
        form = CustomUserCreationForm()
    context = {
        'form' : form,
    }
    return render(request, 'accounts/signup.html', context)
```

> 회원가입 후 곧바로 로그인

```py
# accounts/views.py

def signup(request):
    if request.method == 'POST':
        form = CustomUserCreationForm(request.POST)
        if form.is_valid():
            user = form.save()
            auth_login(request, user)
            return redirect('articles:index')
    else:
        form = CustomUserCreationForm()
    context = {
        'form' : form,
    }
    return render(request, 'accounts/signup.html', context)
```

## 회원탈퇴

> 회원탈퇴 로직 작성

```py
# accounts/views.py

def delete(request):
    request.user.delete()
    return redirect('articles:index')
```

> 탈퇴하면서 유저의 세션 정보도 함께 지우고 싶을 경우

- 탈퇴 후 로그아웃

  - 먼저 로그아웃하면 해당 요청 객체 정보가 없어지기 때문

```py
# accounts/views.py

def delete(request):
    request.user.delete()
    auth_logout(request)
```

## 회원정보 수정

> UserChangeForm

- ModelForm이기 때문에 instance인자로 기존 user 데이터 정보를 받는 구조 또한 동일
- CustomUserChangeForm 사용

> 회원정보 수정 페이지 작성

```py
# accounts/views.py

def update(request):
    if request.method == 'POST':
        pass
    else:
        form = CustomUserChangeForm(instance=request.user)
    context = {
        'form' : form,
    }
    return render(request, 'accounts/update.html', context)
```

> UserChangeForm 사용 시 문제점

- 일반 사용자가 접근 해서는 안될 정보들(fields)까지 모두 수정이 가능해짐

  - admin 인터페이스에서 사용되는 ModelForm이기 때문

- CustomUserChangeForm 에서 접근 가능한 필드를 조정해야 함

```py
# accounts/forms.py

class CustomUserChangeForm(UserChangeForm):

    class Meta(UserChangeForm.Meta):
        model = get_user_model()
        fields = ('email', 'first_name', 'last_name',)
```

> 회원정보 수정 로직 작성

```py
# accounts/views.py

def update(request):
    if request.method == 'POST':
        form = CustomUserChangeForm(request.POST, instance=request.user)
        if form.is_valid():
            form.save()
            return redirect('articles:index')
    else:
        form = CustomUserChangeForm(instance=request.user)
    context = {
        'form' : form,
    }
    return render(request, 'accounts/update.html', context)
```

## 비밀번호 변경

> PasswordChangeForm

- 비밀번호를 변경할 수 있도록 하는 Form
- 이전 비밀번호를 입력하지 않고 비밀번호를 설정할 수 있는 SetPasswordForm을 상속받는 서브 클래스

> 비밀번호 변경 페이지 작성

```py
# accounts/urls.py

urlpatterns = [
    path('password/', views.change_password, name='change_password')
]


# accounts/views.py

from django.contrib.auth.forms import PasswordChangeForm

def change_password(request):
    if request.method == 'POST':
        pass
    else:
        form = PasswordChangeForm(request.user)
    context = {
        'form' : form,
    }
    return render(request, 'accounts/change_password.html', context)
```

> 비밀번호 변경 로직 작성

```py
# accounts/views.py

from django.contrib.auth.forms import PasswordChangeForm

def change_password(request):
    if request.method == 'POST':
        form = PasswordChangeForm(request.user, request.POST)
        if form.is_valid():
            form.save()
            return redirect('articles:index')
    else:
        form = PasswordChangeForm(request.user)
    context = {
        'form' : form,
    }
    return render(request, 'accounts/change_password.html', context)
```

> 암호 변경 시 세션 무효화 방지

- 회원 인증 정보가 일치하지 않게 되버려 로그인 풀림

> update_session_auth_hash()

- update_session_auth_hash(request, user)
- 업데이트 된 사용자 객체를 가져오고, 업데이트 해줌

```py
from django.contrib.auth.forms import PasswordChangeForm
from django.contrib.auth import update_session_auth_hash

def change_password(request):
    if request.method == 'POST':
        form = PasswordChangeForm(request.user, request.POST)
        if form.is_valid():
            form.save()
            update_session_auth_hash(request, form.user)
            return redirect('articles:index')
    else:
        form = PasswordChangeForm(request.user)
    context = {
        'form' : form,
    }
    return render(request, 'accounts/change_password.html', context)
```

## Limiting access to logged-in users

- 로그인 사용자에 대해 접근을 제한하는 2가지 방법

1. is_authenticated attribute
2. login_required decorator

> is_authenticated

- User model의 속성
- 사용자가 인증되었는지 여부를 알 수 있는 방법
- 일반적으로 request.user에서 이 속성 사용

> is_authenticated 적용하기

- 로그인와 비로그인 상태에서 출력되는 링크 다르게 설정하기
- base.html에서 if else endif 작성
- 인증된 사용자라면 로그인 로직을 수행할 수 없도록 처리

```py
# accounts/views.py

def login(request):
    if request.user.is_authenticated:
        return redirect('articles:index')

```

> login_required

- login_required decorator
- 사용자가 로그인 되어있으면 정상적으로 view 함수 실행
- 로그인 상태에서만 글 작성, 수정, 삭제 할 수 있도록 변경

> next query string parameter

- 로그인이 정상적으로 진행되면 이전에 요청했던 주소로 redirect 하기 위해 django가 제공해 주는 쿼리 스트링 파라미터

> next query string parameter 대응

```py
# accounts/views.py

def login(request):
    if request.user.is_authenticated:
        return redirect('articles:index')

    if request.method == 'POST':
        form = AuthenticationForm(request, request.POST)
        if form.is_valid():
            auth_login(request, form.get_user())
            return redirect(request.GET.get('next') or 'articles:index')
```

> 주의사항

- login 템플릿에서 form action 이 작성되어 있다면 동작하지 않음

> 두 데코레이터로 인해 발생하는 구조적 문제

- 두 가지 문제 발생

1. redirect 과정에서 POST 요청 데이터의 손실
2. redirect로 인한 요청은 GET 요청 메서드로만 요청됨

- 해결방안

  - @login_required는 GET request method 를 처리할 수 있는 view 함수에서만 사용
  - POST method 만 허용하는 delete 같은 함수는 내부에서 is_authenticated 속성 값을 사용해서 처리

## 마무리

- django authentication system

  - user 모델 대체하기

- http cookies

  - 상태가 있는 세션 구성

- Authentication in Web requests

  - auth built-in form 사용하기

- authentication with user

  - user object와 crud
