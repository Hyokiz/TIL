# 20221018 TIL

## 어제 내용 복습

## REST API

## HTTP

> HTTP

- 요청과 응답

  - 요청

    - 클라이언트에 의해 전송되는 메시지

  - 응답

    - 서버에서 응답으로 전송되는 메시지

> HTTP 특징

- Stateless(무상태)

  - 동일한 연결(connection)에서 연속적으로 수행되는 두 요청 사이에 링크가 없음
  - 즉, 응답을 마치고 연결을 끊는 순간 클라이언트, 서버 간의 통신이 끝나며 상태 정보가 유지되지 않는다.

- 이를 해결 하기 위해 쿠키와 세션을 사용해 서버 상태를 요청과 연결하도록 함

> HTTP Request Methods

- 리소스에 대한 행위
- 리소스에 대해 수행할 원하는 작업을 나타내는 메서드 모음
- GET, PUSH, PUT, DELETE, ...

> 리소스 (resource)

- HTTP 요청의 대상

> 대표 HTTP Request Methods

1. GET

   - 서버에 리소스의 표현 요청
   - 데이터만 검색

2. POST

   - 데이터를 지정된 리소스에 제출
   - 서버의 상태를 변경

3. PUT

   - 요청한 주소의 리소스를 수정

4. DELETE

   - 지정된 리소스 삭제

> HTTP response status codes

- 특정 HTTP 요청이 성공적으로 완료 되었는지 여부
- 응답은 5개의 그룹

1. Informational responses (100-199)
2. Successful responses (200-299)
3. Redirection messages (300-399)
4. Client error responses (400-499)
5. Server error responses (500-599)

## Identifying resources on the Web

> 개요

- 웹에서 리소스를 식별하는 방법

> 웹에서의 리소스 식별

- HTTP 요청의 대상 > 리소스(자원)
- 리소스는 문서, 사진, 기타 등 어떤 것이든
- 리소스는 식별을 위해 URI로 식별됨

## URI

- Uniform Resource Identifier (통합 자원 식별자)
- 인터넷에서 하나의 리소스를 가리키는 문자열
- 가장 일반적인 URI는 웹 주소로 알려진 URL

- 특정 이름공간에서 이름으로 리소스를 식별하는 URI는 URN

> URL

- Uniform Resource Locator (통합 자원 위치)
- 웹에서 주어진 리소스의 주소
- 네트워크 상에 리소스가 어디 있는지(주소)를 알려주기 위한 약속

  - 이러한 리소스는 HTML, CSS, 이미지 등

- URL은 여러 부분으로 구성. 일부는 필수, 나머지는 선택

- http://www.example.com:80/path/to/myfile.html?key1=value1&key2=value2#SomewhereInTheDocument

> URL 구조

- Scheme (or protocol)

  - 브라우저가 리소스를 요청하는 데 사용해야 하는 프로토콜
  - URL의 첫 부분은 브라우저가 어떤 규약을 사용하는지를 나타냄
  - 기본적으로 웹은 HTTP(S), 메일(mailto:), 파일(ftp:) 등 다양하게 존재

- Authority

  - Scheme 다음은 문자 패턴 ://로 구분된 Authority(권한)이 작성
  - Authority는 domain과 port 모두 포함. 둘은 :(콜론)으로 구분

  1. Domain Name

  - 요청중인 웹 서버
  - IP주소를 직접 사용가능하나, 주로 Domain Name으로 사용
  - 예를 들어 gogole.com의 IP 주소는 142.251.42.142

  2. Port

  - 웹 서버의 리소스에 접근하는데 사용되는 기술적인 문(Gate)
  - HTTP 프로토콜의 생략 가능한 표준 포트(나머지는 생략 불가능)

    - HTTP - 80
    - HTTPS - 443

  - Django의 경우 8000(80 + 00)이 기본 포트

- Path

  - 웹 서버의 리소스 경로
  - 초기에는 실제 파일이 위치한 물리적 위치를 나타냈지만, 오늘날은 추상화된 형태의 구조 표현
  - 예를 들어 /articles/create/가 실제 articles폴더 안의 create 폴더 안을 나타내는 것은 아님

- Parameters

  - 웹 서버에 제공하는 추가적인 데이트
  - 파라미터는 '&'기호로 구분되는 key-value 쌍 목록
  - 서버는 리소스를 응답하기 전에 이러한 파라미터를 사용하여 추가 작업을 수행할 수 있음

- Anchor

  - 리소스의 다른 부분에 대한 앵커
  - 리소스 내부 일종의 북마크. 해당 북마크 지점의 컨텐츠 표시

    - 예를 들어 HTML 문서에서 브라우저는 앵커가 정의한 지점으로 스크롤

  - fragment identifier(부분 식별자)라고 부르는 '#' 이후 부분은 서버에 전송되지 않는다.

    - 서버에 전달되지 않고 해당 지점으로 이동할 수 있도록 함

> Anchor(앵커)

- 하이퍼링크와 비슷한 기능을 하는 인터넷상의 다른 문서와 연결된 문자 혹은 그림

> URN

- Uniform Resource Name (통합 자원 이름)
- URL 과 달리 자원의 위치에 영향을 받지 않는 유일한 이름 역할 (독립적 이름)
- URL의 단점 극복 > 어디 위치한지 관계 없이 이름만으로 자원 식별
- 그러나 보편화 되어 있지 않아 현재는 URL을 대부분 사용

## 정리

- 웹에서의 리소스 식별

  - 자원의 식별자(URI)

    - 자원의 위치로 자원 식별(URL)
    - 고유한 이름으로 자원 식별(URN)

---

## REST API

> API

- Application Programming Interface
- 애플리케이션과 프로그래밍으로 소통하는 방법

  - 개발자가 복잡한 기능을 보다 쉽게 만들 수 있도록 프로그래밍 언어로 제공되는 구성

- API를 제공하는 애플리케이션과 다른 소프트웨어 및 하드웨어 등의 것들 사이의 간단한 계약(인터페이스)
- API는 복잡한 코드를 추상화 > 쉬운 구문 제공

  - 예를 들어 집의 가전 제품에 전기를 공급해야 한다고 가정
  - 우리는 플러그를 소켓에 꽂으면 제품이 작동
  - 중요한 것은 직접 배선하지 않는다.
  - 이는 위험하면서도 비효율적인 일

> Web API

- 웹 서버 또는 웹 브라우저를 위한 API
- 현재 웹 개발은 여러 Open API 활용
- 대표적인 Third Party Open API 서비스 목록

  - Youtube API
  - Naver papago API
  - Kakao Map API

- API는 다양한 타입의 데이터를 응답

  - HTML, XML, JSON 등

> Open API

- 개발자라면 누구나 사용할 수 있도록 공개된 API
- 개발자에게 사유 응용 소프트웨어나 웹 서비스의 프로그래밍적 권한 제공

> REST

- API Server를 개발하기 위한 일종의 소프트웨어 설계 방법론
- REST 원리를 따르는 시스템을 RESTful 하다고 부름
- REST의 기본 아이디어는 리소스, 즉 자원

  - 자원을 정의하고 자원에 대한 주소를 지정하는 전반적인 방법을 서술

> JSON

- JavaScript의 표기법을 따른 단순 문자열
- key-value 형태의 구조를 갖고 있음(C 계열 언어의 자료구조로 쉽게 변환)
- 사람이 읽고 쓰기 쉽고 기계가 파싱(해석 & 분석)하고 만들어내기 쉽기 때문에 현재 API에서 가장 많이 사용

## REST 정리

- 자원을 정의하고 자원에 대한 주소를 지정하는 방법의 모음

1. 자원을 식별 - URI
2. 자원에 대한 행위 - HTTP Methods
3. 자원을 표현 - JSON

- 설계 방법론은 지키지 않았을 때 잃는 것 보다 지켰을 때 얻는 것이 더 많음

  - 지키지 않더라도 동작 여부에는 큰 영향이 없다.
  - 방법론일 뿐이며 규칙, 규약은 아님

---

## Response JSON

> 서버가 응답하는 것

- 지금까지는 페이지(html)만 응답하고 있었음
- 다양한 데이터 타입을 응답할 수 있다.

- 이제는 JSON 데이터를 응답하는 서버로의 변환
- JSON 데이터를 받아 화면을 구성하여 사용자에게 보여주는 것은 Front-end Framework가 담당
- Front-end Framework는 Vue.js 사용
- Front-end, Back-end 분리

## Response

> 개요

- 다양한 방법으로 JSON 데이터 응답해보기

1. HTML
2. JsonResponse()
3. Django Serializer
4. Django REST framework

> 1. HTML

- 지금까지 하던 방식
- urls, viws, templates

> Content-Type entitiy header

- 리소스의 media type(MIME type, content type)을 나타내기 위해 사용됨
- 응답 내에 있는 컨텐츠의 컨텐츠 유형이 실제로 무엇인지 클라이언트에게 알려줌

> 2. JsonResponse()

- 이제는 문서가 아닌 JSON 데이터 응답
- Django가 기본적으로 제공하는 JsonResponse 객체를 활용하여 Python 데이터 타입을 손쉽게 JSON으로 변환하여 응답 가능

- JsonResponse()

  - JSON-encoded response를 만드는 클래스
  - 'safe' parameter

    - 기본 값 True
    - False로 설정 시 모든 타입의 객체를 serialization 할 수 있음 (그렇지 않으면 dict 인스턴스만)

> 3. Django Serializer를 사용한 JSON

- 내장 HttpResponse() 활용
- 이전에는 JSON 의 모든 필드를 작성해야 했으나, 이제는 그렇지 않음

> Serialization

- 직렬화
- 데이터 구조나 객체 상태를 동일 또는 다른 컴퓨터 환경에 저장하고, 나중에 재구성할 수 있는 포맷으로 변환하는 과정

  - 즉, 어떠한 언어나 환경에서도 나중에 다시 쉽게 사용할 수 있는 포맷으로 변환하는 과정

- 변환 포맷은 대표적으로 json, xml, yaml이 있으며 json이 가장 보편적으로 쓰임

> Serializers in Django

- Django의 serialize()는 Queryset 및 Model Instance와 같은 복잡한 데이터를 JSON, XML 등의 유형으로 쉽게 변환할 수 있는 Python 데이터 타입으로 만들어 줌

> 4. Django REST framework

- Django REST framework(DRF)

  - Django에서 Restful API 서버를 쉽게 구축할 수 있도록 도와주는 오픈소스 라이브러리
  - Web API 구축을 위한 강력한 toolkit 제공
  - REST framework를 작성하기 위한 여러 기능 제공

## 정리

- DRF를 활용하여 JSON 데이터에 응답하는 Django 서버 구축

---

## Django REST framework - Single Model

> 개요

- 단일 모델의 data를 Serialization 하여 JSON으로 변환하는 방법에 대한 학습

## ModelSerializer

> ModelSerializer 작성

- articles/serializers.py 생성

  - serializers.py의 위치나 파일명은 자유롭게

- ModelSerializer 작성

> ModelSerializer

- ModelSerializer 클래스는 모델 필드에 해당하는 필드가 있는 Serializer 클래스를 자동으로 만들 수 있는 shortcut 제공

1. Model 정보에 맞춰 자동으로 필드 생성
2. serializer에 대한 유효성 검사기를 자동으로 생성
3. .create() 및 .update()의 간단한 기본 구현 포함

> ModelSerializer의 'many' option

- 단일 객체 인스턴스 대신 QuerySet 또는 객체 목록을 serialize 하려면 many=True를 작성해야 함


## Build RESTful API - Article

> GET - List

- 게시글 데이터 목록 조회하기
- DRF 에서 api_view 데코레이터 작성 필수

> api_view decorator

- DRF view 함수가 응답해야 하는 HTTP 메서드 목록을 받음
- 기본적으로 GET 메서드만 허용되며 다른 메서드 요청에 대해서는 405 Method Not Allowed로 응답

> GET - detail

- 단일 게시글 데이터 조회하기
- 각 데이터의 상세 정보를 제공하는 ArticleSerializer 정의

> POST

- 게시글 데이터 생성
- 요청에 대한 데이터 생성 성공 시 - 201 Created 상태 코드 / 실패 시 - 400 Bad request

> Raising an exception on invalid data

- is_valid()는 유효성 검사 오류가 있는 경우 ValidationError 예외를 발생시키는 선택적 raise_exception 인자를 사용할 수 있음
- 자동으로 처리, 기본적으로 HTTP 400 응답

> DELETE

- 게시글 데이터 삭제
- 삭제 성공 시 204 No Content 응답

> PUT

- 게시글 데이터 수정
- 수정 성공 시 200 OK 상태코드 응답

## Django REST framework - N:1 Relation

> 개요

- N:1 관계에서의 모델 data 를 Serialization 하여 JSON으로 반환

> GET - List

- 댓글 데이터 목록 조회
- Article List와 비교하며 작성

> GET - Detail

- 단일 댓글 데이터 조회
- Article과 달리 같은 serializer 사용

> POST

- 단일 댓글 데이터 생성

> Passing Additional attributes to .save()

- save() 메서드는 특정 Serializer 인스턴스를 저장하는 과정에서 추가적인 데이터를 받을 수 있음
- CommentSerializer를 통해 Serialize 되는 과정에서 Parameter로 넘어온 article_pk에 해당하는 article 객체를 추가적인 데이터를 넘겨 저장

- 에러가 난다.

  - CommentSerializer에서 article field 데이터 또한 사용자로부터 입력 받도록 설정되어 있기 때문

> 읽기 전용 필드 설정

- read_only_fields를 사용해 외래 키 필드를 읽기 전용 필드로 설정
- 해당 필드를 유효성 검사에서 제외시키고 데이터 조회 시에는 출력

> DELETE & PUT

## N:1 - 역참조 데이터 조회

> 개요

1. 특정 게시글에 작성된 댓글 목록 출력하기

   - 기존 필드 override

2. 특성 게시글에 작성된 댓글의 개수 출력하기

   - 새로운 필드 추가

> 1. 특정 게시글에 작성된 댓글 목록 출력하기

- 기존 필드 override - Article Detail

  - 게시글 조회 시 해당 게시글의 댓글 목록까지 함께 출력
  - 기존 필드를 override하거나 추가적인 필드 구성 가능

1. PrimaryKeyRelatedField()

   - 댓글이 있는 게시글 응답 예시

- models.py에서 related_name을 통해 이름 변경 가능
- 역참조 시 생성되는 comment_set을 override 할 수 있음

2. Nested relationships

- 모델 관계 상으로 참조된 대상은 참조하는 대상의 표현에 포함되거나 중첩(nested)될 수 있음
- 이러한 중첩된 관계는 serializers를 필드로 사용하여 표현할 수 있음
- 두 클래스의 상/하 위치를 변경해야 함

> 2. 특정 게시글에 작성된 댓글의 개수 출력하기

- 새로운 필드 추가 - Article Detail

  - 게시글 조회 시 해당 게시글의 댓글 개수까지 함께 출력하기

- source

  - serializers field's argument
  - 필드를 채우는 데 사용할 속성의 이름
  - 점 표기법(dotted notation)을 사용하여 속성을 탐색할 수 있음

> 읽기 전용 필드 지정 이슈

- 특정 필드를 override 혹은 추가한 경우 read_only_fields 가 동작하지 않으니 주의

## Django shortcuts functions

> 개요

- django.shortcuts 패키지는 개발에 도움이 될 수 있는 여러 함수와 클래스 제공
- 제공되는 shortcuts 목록

  - render(), redirect(), get_object_or_404(), get_list_or_404()

> get_object_or_404()

- 모델 manager objects에서 get()을 호출하지만, 해당 객체가 없을 때 기존 DoesNotExist 예외 대신 HTTP404를 raise

> get_list_or_404()

- 모델 manager objects에서 filter()의 결과를 반환하고 해당 객체 목록이 없을 땐 HTTP 404를 raise

> 왜 사용해야할까?

- 올바른 에러 전달

---

## 마무리

- REST API
- Response JSON
- Django REST framework - Single Moel
- Django REST framework - N:1 Relation



