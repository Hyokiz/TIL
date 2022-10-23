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

> URL 구조

- Scheme(or protocol)

  - https
  - 브라우저가 리소스를 요청하는 데 사용해야 하는 프로토콜
  - URL의 첫 부분은 브라우저가 어떤 규약을 사용하는지 나타냄
  - 메일을 열기 위한 mailto:, 파일을 전송하기 위한 ftp:등 존재

- Authority
