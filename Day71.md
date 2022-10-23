# 20221023 TIL

# REST API

## HTTP

> HTTP

- HyperText Transfer Protocol
- HTML 문서와 같은 리소스(resource, 자원)들을 가져올 수 있도록 하는 프로토콜(규칙, 약속)
- 클라이언트와 서버간의 통신

  - 요청

    - 클라이언트에 의해 전송되는 메시지

  - 응답

    - 서버에서 응답으로 전송되는 메시지

> HTTP 특징

- 무상태

  - 응답을 마치고 연결을 끊는 순간 통신이 끝나고, 상태 정보가 유지되지 않음

- 이를 해결하기 위해 쿠키와 세션을 사용해 서버 상태를 요청과 연결하도록 함

> HTTP Request Methods

- 리소스에 대한 행위를 정의
- 메서드 모음
- HTTP Method 예시

  - GET, POST, PUT, DELETE

> 리소스

- HTTP 요청의 대상

> 대표 HTTP Request Methods

1. GET

- 서버에 대한 리소스의 표현 요청
- GET을 사용하는 요청은 데이터만 검색

2. POST

- 데이터를 지정된 리소스에 제출
- 서버의 상태 변경

3. PUT

- 요청한 주소의 리소스 수정

4. DELETE

- 저장된 리소스 삭제

> HTTP response status codes

- 특정 HTTP 요청이 성공적으로 완료 되었는지 여부
- 응답 5가지

1. Informational responses(100 - 199)
2. Successful responses(200 - 299)
3. Redirection messages(300 - 399)
4. Client error responses(400 - 499)
5. Server error responses(500 - 599)

# Identifying resources on the Web

> 개요

- 웹에서 리소스를 식별하는 방법

> 웹에서의 리소스 식별

- HTTP 요청의 대상을 리소스라고 함
- 리소스는 문서, 사진, 기타 어떤 것이든 될 수 있음
- 각 리소스는 식별을 위해 URI로 식별됨

## URI

> URI

- Uniform Resource Identifier(통합 자원 식별자)
- 인터넷에서 하나의 리소스를 가리키는 문자열
- 가장 일반적인 URI는 웹 주소로 알려진 URL
- 특정 이름 공간에서 이름으로 리소스를 식별하는 URI는 URN

> URL

- Uniform Resource Locator(통합 자원 위치)
- 웹에서 주어진 리소스의 주소
- 네트워크 상에 리소스가 어디 있는지(주소)를 알려주기 위한 약속

  - 이러한 리소스는 HTML, CSS, 이미지 등

- URL은 여러 부분으로 구성되고 일부는 필수이고 나머지는 선택

> URN

- URL과 달리 자원의 위치에 영향을 받지 않는 유일한 이름 역할
- URL의 단점 보완으로 이름만으로 자원 식별 가능
- 보편화 되어 있지 않아 현재는 대부분 URL 사용중
- 예시

  - ISBN(국제표준 도서번호)

    - 국제적으로 책에 붙이는 고유 식별자

  - ISAN(국제표준 시청각 자료번호)

    - 도서의 ISBN과 유사한 시청각 작품 및 관련 버전의 고유 식별자

## 정리

- 웹에서의 리소스 식별

  - 자원의 식별자(URI)

    - 자원의 위치로 자원 식별(URL)
    - 고유한 이름으로 자원 식별(URN)

---

# REST API

> API

- 애플리케이션과 프로그래밍으로 소통하는 방법

  - 개발자가 복잡한 기능을 보다 쉽게 만들 수 있도록 프로그래밍 언어로 제공되는 구성

- API를 제공하는 애플리케이션과 다른 소프트웨어 및 하드웨어 등의 것들 사이의 간단한 계약(인터페이스)이라고 볼 수 있음

- API는 복잡한 코드를 추상화하여 대신 사용할 수 있는 몇 가지 쉬운 구문을 제공

  - 가전 제품에 공기를 공급한다고 가정
  - 우리는 전기를 공급하기 위해 직접 배선하지 않음
  - 이는 매우 위험하면서 비효율적

> Web API

- 웹 서버 또는 웹 브라우절르 위한 API
- 현재 웹 개발은 여러 Open API를 활용하는 추세
- 대표적인 Third Party Open API 목록

  - Youtube API
  - Naver Papago API
  - Kakao Map API

- 다양한 타입의 데이터 응답

  - HTML, XML, JSON 등

> Open API

- 개발자라면 누구나 사용할 수 있도록 공개된 API
- 개발자에게 사유 응용 소프트웨어나 웹 서비스의 프로그래밍적 권한 제공

> REST

- Representational State Transfer
- API Server를 개발하기 위한 일종의 소프트웨어 설계 방법론
- 소프트웨어 아키텍쳐 디자인 제약 모음
- REST원리를 따르는 시스템을 RESTful 하다고 부름
- REST의 기본 아이디어는 리소스 즉 자원

  - 자원을 정의하고 자원에 대한 주소를 지정하는 전반적인 방법을 서술

> REST에서 자원을 정의하고 주솔르 지정하는 방법

1. 자원의 식별

   - URI

2. 자원의 행위

   - HTTP method

3. 자원의 표현

   - 자원의 행위를 통해 궁극적으로 표현되는 결과물
   - JSON으로 표현된 데이터를 제공

> JSON

- JavaScript의 표기법을 따른 단순 문자열
- key-value 형태의 구조
- 사람이 읽고 쓰기 쉽고 기계가 파싱(해석 & 분석)하고 만들어내기 쉽기 때문에 현재 API에서 가장 많이 사용하는 데이터 타입

## REST 정리

- 자원을 정의하고 자원에 대한 주소를 지정하는 방법의 모음

1. 자원을 식별 - URI
2. 자원에 대한 행위 - HTTP Methods
3. 자원을 표현 - JSON

- 설계 방법론을 지켰을 때 얻는 것이 훨씬 많음

---

# Response JSON

> 개요

- JSON 형태로의 서버 응답 변화
- 다양한 방법의 JSON 응답

## Intro

> 서버가 응답하는 것

- 페이지(html) 뿐만 아니라 데이터 타입을 응답할 수 있음

# Response

> 개요

- 다양한 방법으로 JSON 응답

1. HTML 응답
2. JsonResponse()를 사용한 JSON 응답
3. Django Serializer를 사용한 JSON 응답
4. Django REST framework를 사용한 JSON 응답

> 1. HTML 응답

- 문서(HTML) 한 장을 응답하는 서버 확인하기

> Content-Type entitiy header

- 리소스의 media type(MIME type, content type)을 나타내기 위해 사용됨
- 응답 내에 있는 컨텐츠의 컨텐츠 유형이 실제로 무엇인지 클라이언트에게 알려줌

> 2. JsonResponse()를 사용한 JSON 응답

- Django가 기본적으로 제공하는 JsonResponse객체를 활용하여 Python 데이터 타입을 손쉽게 JSON으로 변환하여 응답가능
