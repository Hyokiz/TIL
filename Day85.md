# 20221114 TIL

# Vue with DRF

> 개요

- Server와 Client의 통신 방법 이해하기
- CORS 이슈 이해하고 해결하기
- DRF Auth System 이해하기
- Vue와 API server 통신하기

# Server & Client

> Server

- 서버란?

  - 클라이언트에세 정보와 서비스를 제공하는 컴퓨터 시스템
  - 서비스 전체를 제공 == Django Web Service
  - 정보를 제공 == DRF API Service

- 서비스 전체를 제공 == Django Web Service

  - Django를 통해 전달받은 HTML은 하나의 웹 페이지를 구성할 수 있는 모든 데이터가 포함
  - 즉 서버에서 모든 내용을 렌더링 하나의 HTML 파일로 제공
  - 정보를 포함한 web 서비스를 구성하는 모든 내용을 서버 측에서 제공

- 정보를 제공 == DRF API Service

  - Django를 통해 관리하는 정보만을 클라이언트에게 제공
  - DRF를 사용하여 JSON 으로 변환

> Client

- 클라이언트란?

  - Server가 제공하는 서비스에 적절한 요청을 통해 Server로부터 반환 받은 응답을 사용자에게 표현하는 기능을 가진 프로그램 혹은 시스템

- Server가 제공하는 서비스에 적절한 요청

  - Server가 정의한 방식대로 요청인자를 넘겨 요청
  - Server는 정상적인 요청에 적합한 응답 제공

- 잘못된 요청 예

  - 아래와 같은 Model 이 정의되어 있다면

  ```py
  class Article(models.Model):
    title = models.CharField(max_length=100)
    content = models.TextField()
  ```

- 잘못된 field 명으로 요청을 보낼 경우 처리할 수 없음

- Server로부터 반환받은 응답을 사용자에게 표현

  - 사용자의 요청에 적합한 data를 server에 요청하여 응답 받은 결과로 적절한 화면을 구성

> 정리

- Server는 정보와 서비스를 제공

  - DB와 통신하여 데이터를 생성, 조회, 수정, 삭제를 담당
  - 요청을 보낸 Client에게 정상적인 요청이었다면 처리한 결과를 응답

- Client는 사용자의 정보 요청을 처리, server에게 응답받은 정보를 표현

  - Server에게 정보(데이터)를 요청
  - 응답 받은 정보를 가공하여 화면에 표현

# Cross-Origin Resource Sharing

> What Happened?

- 브라우저가 요청을 보내고 서버의 응답이 브라우저에 도착

  - server의 log는 200(정상) 반환
  - 즉 Server는 정상적으로 응답했지만 브라우저가 막은 것

- 보안상의 이유로 브라우저는 동일 출처 정책(SOP)에 의해 다른 출처의 리소스와 상호작용 하는 것을 제한 함

> SOP(Same-Origin Policy)

- 동일 출처 정책
- 불러온 문서나 스크립트가 다른 출처에서 가져온 리소스와 상호작용 하는 것을 제한하는 보안 방식
- 잠재적으로 해로울 수 있는 문서를 분리함으로써 공격받을 수 있는 경로를 줄임

> Origin - 출처

- URL 의 Protocol, Host, Port를 모두 포함하여 출처라고 부름
- Same Origin 예시

  - 아래의 세 영역이 일치하는 경우에만 동일 출처로 인정
  - http://localhost:3000/posts/3 에서 3000까지만

  - 셋 중에 하나라도 일치 하지 않으면 동일한 출처로 인정하지 않음

> CORS - 교차 출처 리소스 공유

- 추가 HTTP Header를 사용하여, 특정 출처에서 실행 중인 웹 어플리케이션이 다른 출처의 자원에 접근할 수 있는 권한을 부여하도록 브라우저에서 알려주는 체제

  - 어떤 출처에서 자신의 컨텐츠를 불러갈 수 있는지 서버에서 지정할 수 있는 방법

- 리소스가 자신의 출처와 다를 때 교차 출처 HTTP 요청을 실행

  - 만약 다른 출처의 리소스를 가져오기 위해서는 이를 제공하는 서버가 브라우저에게 다른 출처지만 접근해도 된다는 사실을 알려야 함
  - 교차 출처 리소스 공유 정책(CORS Policy)

> CORS policy - 교차 출처 리소스 공유 정책

- 다른 출처에서 온 리소스를 공유하는 것에 대한 정책
- CORS Policy에 위배되는 경우 브라우저에서 해당 응답 결과를 사용하지 않음

  - Server에서 응답을 주더라도 브라우저에서 거절

- 다른 출처의 리소스를 불러오려면 그 출처에서 올바른 CORS header를 포함한 응답을 반환해야 함

# How to set CORS

> How to set CORS

- CORS 표준에 의해 추가된 HTTP Response Header를 통해 이를 통제 가능
- HTTP Response Header 예시

  - Access-Control-Allow-Origin

- Access-Control-Allow-Origin

  - 단일 출처를 지정하여 브라우저가 해당 출처가 리소스에 접근하도록 함

> django-cors-headers library 사용하기

- 응답에 CORS header를 추가해주는 라이브러리
- 다른 출처에서 Django 애플리케이션에 대한 브라우저로 내 요청을 허용함

# Vue with DRF(feat. CORS)

# Article Read

# DRF Auth System

# Authentication and Authorization

> Authentication - 인증, 입증

- 자신이라고 주장하는 사용자가 누구인지 확인하는 행위
- 모든 보안 프로세스의 첫 번째 단계(가장 기본 요소)
- 즉, 내가 누구인지를 확인하는 과정
- 401 Unauthorized

  - 비록 HTTP 표준에서는 미승인(unauthorized)을 명확히 하고 있지만, 의미상 이 응답은 비인증(unauthenticated)을 의미

> Authorization - 권한 부여, 허가

- 사용자에게 특정 리소스 또는 기능에 대한 엑세스 권한을 부여하는 과정(절차)
- 보안 환경에서 권한 부여는 항상 인증이 먼저 필요함

  - 사용자는 조직에 대한 엑세스 권한을 부여 받기 전에 먼저 자신의 ID가 진짜인지 먼저 확인해야 함

- 서류의 등급, 웹 페이지에서 글을 조회, 삭제, 수정 할 수 있는 방법, 제한 구역

  - 인증이 되었어도 모든 권한을 부여 받는 것은 아님

- 403 Forbidden

  - 401과 다른 점은 서버는 클라이언트가 누구인지 알고 있음

# How to authentication determined

> 인증 여부 확인 방법

- settings.py에 작성하여야 할 설정

  - 기본적인 인증 절차를 어떠한 방식으로 둘 것이냐를 설정하는 것
  - 예시의 2가지 방법 외에도 각 framework마다 다양한 인증 방식이 있음

- 우리가 사용할 방법은 DRF가 기본으로 제공해주는 인증 방식 중 하나인 TokenAuthentication
- 모든 상황에 대한 인증 방식을 정의 하는 것이므로, 각 요청에 따라 다른 인증 방식을 거치고자 한다면 다른 방식이 필요

- view 함수마다(각 요청마다) 다른 인증 방식을 설정하고자 한다면 decorator 활용

- permission_classes

  - 권한 관련 설정
  - 권한 역시 특정 view 함수마다 다른 접근 권한을 요청할 수 있음

> 다양한 인증 방식

- BasicAuthentication

  - 가장 기본적인 수준의 인증 방식
  - 테스트에 적합

- SessionAuthentication

  - Django에서 사용하였던 session 기반의 인증 시스템
  - DRF와 Django의 session 인증 방식은 보안적 측면을 구성하는 방법에 차이가 있음

- RemoteUserAuthentication

  - Django의 Remote user 방식을 사용할 때 활용하는 인증 방식

- TokenAuthentication

  - 매우 간단하게 구현할 수 있음
  - 기본적인 보안 기능 제공
  - 다양한 외부 패키지가 있음

- (중요) settings.py 에서 DEFAULT_AUTHENTICATION_CLASSES를 정의

  - TokenAuthentication 인증 방식을 사용할 것임을 명시

> TokenAuthentication 사용 방법

- User는 발급 받은 Token을 headers에 담아 요청과 함께 전송

  - 단, 반드시 Token 문자열 함께 삽입

    - 삽입해야 할 문자열은 각 인증 방식마다 다름(ex. Bearer, Auth, JWT 등)

  - 주의) Token 문자열과 발급받은 실제 token 사이를 ' '(공백)으로 구분

- Authorization HTTP headers 작성 방법

  - Authorization: Token 9944b~

> 토큰 생성 및 관리 문제점

- 기본 제공 방식에서 고려하여야 할 사항들

  1. Token 생성 시점
  2. 생성한 Token 관리 방법
  3. User와 관련된 각종 기능 관리 방법

  - 회원가입
  - 로그인
  - 회원 정보 수정
  - 비밀 번호 변경 등

# dj-rest-auth

> Dj-Rest-Auth

- 회원가입, 인증, 비밀번호 재설정, 사용자 세부 정보 검색, 회원 정보 수정 등을 위한 REST API end point 제공

- 주의) django-rest-auth는 더 이상 업데이트를 지원하지 않음. dj-rest-auth 사용

