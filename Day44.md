# 20220907 TIL

## Django authentication system

> 개요

- 인증 시스템은 인증(Authentication)과 권한(Authorization) 부여를 함께 제공(처리)하며, 이러한 기능이 어느 정도 결합되어 일반적으로 인증 시스템이라고 함
- 필수 구성은 settings.py에 이미 포함되어 있으며 INSTALLED_APPS에서 확인 가능

  - django.contrib.auth

- Authentication(인증)

  - 신원 확인
  - 사용자가 자신이 누구인지 확인하는 것

- Authorization(권한, 허가)

  - 권한 부여
  - 인증된 사용자가 수행할 수 있는 작업을 결정

- ex.
  - articles : 게시판
  - accounts : 회원, 인증

> 사전 설정

- 두번째 app accounts 생성 및 등록
  - auth 와 관련된 경로나 키워드들을 Django 내부적으로 accounts라는 이름으로 사용하고 있기 때문에 되도록 accounts로 지정하는 것을 권장
  - 다른 이름으로 설정해도 되지만 나중에 추가 설정을 해야할 일들이 생길 수 있다.

## Substituting a custom User model

> 개요

- 커스텀 User 모델로 대체하기
- 기본 User model을 필수적으로 custom User model로 대체하는 이유 이해하기
- 개발자들이 작성하는 일부 프로젝트에서는 django에서 제공하는 built-in User model 의 기본 인증 요구사항이 적절하지 않을 수 있음
  - 예를 들면 내 서비스에서 회원가입 시 username대신 email을 식별 값으로 사용하는 것이 더 적합한 사이트인 경우 django의 User model이 기본적으로 username를 식별 값으로 사용하기 때문에 기본 User model을 수정해야하나 쉽지 않은 작업이기 때문
- 그래서 Django는 현재 프로젝트에서 나타낼 User를 참조하는 AUTH_USER_MODEL 설정 값을 제공하여 default user model을 재정의(override)할 수 있도록 함

> AUTH_USER_MODEL

- 프로젝트에서 User를 나타낼 때 사용하는 모델
- 프로젝트가 진행되는 동안(모델을 만들고 마이그레이션 한 후) 변경할 수 없음
- 프로젝트 시작 시 설정, 참조하는 모델은 첫 번째 마이그레이션에서 사용할 수 있어야 함
  - 첫번째 마이그레이션 전에 확정 지어야 하는 값

> settings의 로드 구조

- AUTH_USER_MODEL은 settings.py에서 보이지 않는다.
  - 우리가 작성하는 settings.py는 사실 global_settings.py를 상속받아 재정의하는 파일임

> 대체하기

- AbstractUser를 상속받는 커스텀 User 클래스 작성
- 기존 User 클래스도 AbstractUser를 상속받기 때문에 커스텀 User 클래스도 완전히 같은 모습을 가지게 됨

> AbstractUser

- 관리자 권한과 함께 완전한 기능을 가지고 있는 User model을 구현하는 추상 기본클래스

- Abstract base classes (추상 기본 클래스)
  - 몇 가지 공통 정보를 여러 다른 모델에 넣을 때 사용하는 클래스
  - 데이터베이스 테이블을 만드는 데 사용되지 않으며, 대신 다른 모델의 기본 클래스로 사용되는 경우 해당 필드가 하위 클래스의 필드에 추가 됨

> 프로젝트 중간에 AUTH_USER_MODEL 변경하기

- 모델 관계에 영향을 미치기 때문에 훨씬 더 어려운 작업

  - 변경사항이 자동으로 수행될 수 없기 때문에 DB 스키마를 직접 수정, 이전 사용자 테이블에서 데이터를 이동, 일부 마이그레이션을 수동으로 다시 적용 등등..

- 결론 : 중간 변경은 권장하지 않음(프로젝트 처음에 진행하자!)

> 데이터베이스 초기화

- 수업 진행을 위한 DB 초기화 후 마이그레이션(프로젝트 중간일 경우)

1. migrations 파일 삭제

   - migrations 폴더 및 init.py는 삭제하지 않음
   - 번호가 붙은 파일만 삭제

2. db.sqlite3 삭제
3. migrations 진행

   - makemigrations
   - migrate

> 반드시 User 모델을 대체해야 할까?

- Django는 새 프로젝트를 시작하는 경우 비록 기본 User모델이 충분하더라도 커스텀 User 모델을 설정하는 것을 강력하게 권장(highly recommended)
- 커스텀 User 모델은 기본 User 모델과 동일하게 작동하면서도 필요한 경우 나중에 맞춤 설정할 수 있기 때문
  - 단, User 모델 대체 작업은 프로그램의 모든 migrations 혹은 첫 migrate를 실행하기 전에 이 작업을 마쳐야 함

## HTTP Cookies

## HTTP

> HTTP

- Hyper Text Transfer Protocol
- HTML 문서와 같은 리소스들을 가져올 수 있도록 해주는 프로토콜(규칙, 규약)
- 웹(www)에서 이루어지는 모든 데이터 교환의 기초
- 클라이언트 - 서버 프로토콜이라고도 부름

> 요청과 응답

- 요청

  - 클라이언트(브라우저)에 의해 전송되는 메시지

- 응답
  - 서버에서 응답으로 전송되는 메시지

> HTTP 특징

1. 비 연결 지향(connectionless)

   - 서버는 요청에 대한 응답을 보낸 후 연결을 끊음
     - 네이버 메인 페이지 보고있을때 > 네이버 서버와 연결된 것이 아님
     - 메인 페이지를 응답하고 연결을 끊은 것

2. 무상태(stateless)

   - 연결을 끊은 순간 클라이언트와 서버 간의 통신이 끝나며 상태 정보 유지되지 앟음
   - 클라이언트와 서버가 주고받는 메세지들은 서로 완전히 독립적

> 어떻게 로그인 상태를 유지할까?

- 페이지를 이동해도 로그인 상태가 유지됨
- 서버와 클라이언트 간 지속적인 상태 유지를 위해 쿠키와 세션이 존재

## 쿠키(Cookie)

> 개요

- HTTP 쿠키는 상태가 있는 세션을 만들도록 해 줌

> 개념

- 서버가 사용자의 웹 브라우저에 전송하는 작은 데이터 조각
- 사용자가 웹사이트를 방문할 경우 해당 웹사이트의 서버를 통해 사용자의 컴퓨터에설치되는 작은 기록 정보 파일

  1. 브라우저(클라이언트)는 쿠키를 로컬에 KEY-VALUE의 데이터 형식으로 저장
  2. 이렇게 쿠키를 저장해 놓았다가, 동일한 서버에 재요청 시 저장된 쿠키를 함께 전송

- 쿠키는 두 요청이 동일한 브라우저에서 들어왔는지 아닌지를 판단할 때 주로 사용됨

  - 이를 이용해 사용자의 로그인 상태를 유지할 수 있음
  - 상태가 없는(stateless) HTTP 프로토콜에서 상태 정보를 기억 시켜 주기 때문

- 즉, 웹페이지에 접속 시 웹 페이지를 응답한 서버로부터 쿠키를 받아 브라우저에 저장. 클라이언트가 같은 서버에 재요청 시마다 요청과 함께 저장해 두었던 쿠키도 함께 전송

> 쿠키 사용 목적

1. 세션 관리

   - 로그인, 아이디 자동완성, 공지 하루 안 보기, 팝업 체크, 장바구니 등 정보 관리

2. 개인화

   - 사용자 선호, 테마 등의 설정

3. 트래킹

   - 사용자 행동을 기록 및 분석

> 세션

- 사이트와 특정 브라우저 사이의 "state(상태)" 를 유지하는 것
- 클라이언트가 서버에 접속하면 서버가 특정 session id를 발급하고, 클라이언트는 session id를 쿠키에 저장

  - 클라이언트가 다시 동일한 서버에 접속하면 요청과 함께 쿠키(session id가 저장된)를 서버에 전달
  - 쿠키는 요청 때마다 서버에 함께 전송되므로 서버에서 session id를 확인해 알맞은 로직을 처리

- session id는 세션을 구별하기 위해 필요, 쿠키에는 session id만 저장

> 쿠키 Lifetime(수명)

1. Session cookie

   - 현재 세션(cureent session)이 종료되면 삭제됨
   - 브라우저 종료와 함께 세션이 삭제됨

2. Persistent cookies

   - Expires 속성에 지정된 날짜 혹은 Max-Age 속성에 지정된 기간이 지나 삭제됨

> Session in Django

- Django는 database-backed sessions 저장 방식을 기본 값으로 사용

  - session 정보는 Django DB의 django_session 테이블에 저장
  - 설정을 통해 저장방식 변경 가능

- Django는 특정 session id를 포함하는 쿠키를 사용해서 각각의 브라우저와 사이트가 연결된 session을 알아냄
- Django는 우리가 session 메커니즘(복잡한 동작원리)에 대부분을 생각하지 않게끔 많은 도움을 줌

## Authentication in Web requests

> 개요

- Django가 제공하는 인증 관련 built-in forms 익히기

## Login

> 개요

- 로그인은 Session을 Create 하는 과정

> AuthenticationForm

- 로그인을 위한 built-in form

  - 로그인 하고자 하는 사용자 정보를 입력 받음
  - 기본적으로 username과 password를 받아 데이터가 유효한지 검증

- request를 첫번째 인자로 취함

> login()

- login(request, user, backend=None)
- 인증된 사용자를 로그인 시키는 로직으로 view 함수에서 사용
- 현재 세션에 연결하려는 인증된 사용자가 있는 경우 사용
- HttpRequest 객체과 User객체가 필요

> get_user()

- AuthenticationForm의 인스턴스 메서드
- 유효성 검사를 통과했을 경우 로그인 한 사용자 객체를 반환

## Authentication with User

> 현재 로그인 되어있는 유저 정보 출력하기

- 어떻게 base 템플릿에서 context 데이터 없이 user 변수를 사용할까?
  - settings.py의 context processors 설정 값 때문

> context processors

- 템플릿이 렌더링 될 때 호출 가능한 컨텍스트 데이터 목록
- 작성된 컨텍스트 데이터는 기본적으로 템플릿에서 사용 가능한 변수로 포함됨
- 즉, django에서 자주 사용하는 데이터 목록을 미리 템플릿에 로드 해둔 것

> django.contrib.auth.context_processors.auth

- 현재 로그인한 사용자를 나타내는 User 클래스의 인스턴스가 템플릿 변수 {{ user }}에 저장됨
  - 클라이언트가 로그인하지 않은 경우 AnonymousUser 클래스의 인스턴스로 생성

## Logout

> 개요

- 로그아웃은 Session을 Delete 하는 과정

> logout()

- logout(request)
- HttpRequest 객체를 인자로 받고 반환값 없음
- 사용자가 로그인 하지 않은 경우 오류를 발생시키지 않음
- 다음 2가지 일 처리
  1. 현재 요청에 대한 session data를 DB에서 삭제
  2. 클라이언트의 쿠키에서도 sessionid를 삭제
  - 이는 다른 사람이 동일한 웹 브라우저를 사용하여 로그인하고, 이전 사용자의 세션 데이터에 엑세스 방지

## Authentication with User

> 개요

- User Object와 User CRUD에 대한 이해
  - 회원 가입, 탈퇴, 정보 수정, 비밀번호 변경

## 회원가입

> 개요

- User을 Create하는 것. UserCreationForm built-in form 사용

> UserCreationForm

- 주어진 username과 password로 권한이 없는 새 user를 생성하는 ModelForm(일반)
- 3개의 필드를 가짐
  1. username(from the user model)
  2. password1
  3. password2

> 회원가입 진행 후 에러 페이지를 확인

- 회원가입에 사용하는 UserCreationForm이 우리가 대체한 커스텀 유저 모델이 아닌 기존 모델로 인해 작성된 클래스이기 때문.
- CustomUserCreationForm을 forms.py에 작성하여 그 안의 meta를 model = get_user_model()로 변경

## Custom user & Built-in auth forms

> AbstractBaseUser의 모든 subclass와 호환되는 forms

- 아래 Form 클래스는 User 모델을 대체하더라고 커스텀 하지 않아도 사용 가능

  1. AuthenticationForm
  2. SetPasswordForm
  3. PasswordChangeForm
  4. AdminPasswordChangeForm

- 기존 User모델을 참조하는 Form이 아니기 때문.

> 커스텀 유저 모델을 사용하려면 다시 작성하거나 확장해야하는 forms

1. UserCreationForm : 회원가입
2. UserChangeForm : 정보수정

- 두 form 모두 class Meta: model = User가 등록된 form이기 때문에 반드시 커스텀(확장)해야 한다.

> get_user_model()

- 현재 프로젝트에서 활성화된 사용자 모델을 반환
- 직접 참조하지 않는 이유

  - 예를 들어 기존 User 모델이 아닌 커스텀 한 상황에서는 커스텀 User 모델을 자동으로 반환해주기 때문

- Django는 User 클래스를 직접 참조하는 대신 get_user_model()을 사용해 참조해야 한다고 강조.

> UserCreationForm 의 save 메서드

- user를 반환하는 것을 확인

## 회원탈퇴

> 탈퇴하면서 해당 유저의 세션 정보도 함께 지우고 싶을 경우

- 탈퇴 후 로그아웃의 순서가 바뀌면 안된다.
  - 먼저 로그아웃 해버리면 해당 요청 객체 정보가 없어지기 때문에 탈퇴에 필요한 정보도 없어진다.

## 회원정보 수정

> 개요

- User를 Update하는 것

> UserChangeForm

- 사용자의 정보 및 권한을 변경하기 위해 admin 인터페이스에서 사용되는 ModelForm
- UserChangeForm 또한 ModelForm이기 때문에 instance 인자로 기존 user 데이터 정보를 받는 구조 또한 동일
- 이미 이전에 확장했기 때문에 CustomUserChangeForm 사용

> UserChangeForm 사용 시 문제점

- 일반 사용자가 접근해서는 안될 정보들까지 모두 수정이 가능해짐
- 따라서 CustomUserChangeForm에서 접근 가능한 필드 조정

## 비밀번호 변경

> PasswordChangeForm

- 사용자가 비밀번호를 변경할 수 있도록 하는 Form
- 이전 비밀번호 없이 비밀번호를 설정할 수 있는 SetPasswordForm을 상속받는 서브 클래스

> 암호 변경 시 세션 무효화 방지하기

- 비밀번호가 변경되면 기존 세션과의 회원 인증 정보가 일치하지 않게 되어 로그인 상태 유지 불가

> update_session_auth_hash()

- update_session_auth_hash(request, user)
- 암호가 변경되어도 로그아웃 되지 않도록 새로운 password의 session data로 session을 업데이트

## Limiting access to logged-in users

> 개요

- 로그인 사용자에 대해 접근 제한 2가지

1. is_authenticated attribute
2. The login_required decorator

> is_authenticated

- User model의 속성(attributes) 중 하나
- 사용자가 인증 되었는지 여부를 알 수 있음
- 모든 User 인스턴스에 항상 True
  - AnonymousUser에 대해 항상 False
- 일반적으로 request.user에서 이 속성 사용

> 두 데코레이터로 인해 발생하는 구조적 문제

1. 비로그인 상태로 detail 페이지에서 게시글 삭제 시도
2. delete view 함수의 @login_required로 인해 로그인 페이지로 리다이렉트
3. redirect로 이동한 로그인 페이지에서 로그인 진행
4. delete view 함수의 @require_POST로 인해 405 상태 코드를 받게 됨
   - 405(Method Not Allowed) status code 확인

- POST method 만 허용하는 delete 같은 함수는 내부에서 is_authenticated 속성 값을 사용해서 처리

## 마무리

- Django authentication system

  - User 모델 대체하기

- HTTP Cookies

  - 상태가 있는 세션 구성

- Authentication in Web requests

  - Auth built-in form 사용하기

- Authentication with User
  - User Object와 User CRUD
