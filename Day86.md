# 20221115 TIL

# Vue with DRF

> 개요

- Server와 Client의 통신 방법 이해하기
- CORS 이슈 이해하고 해결하기
- DRF Auth System 이해하기
- Vue와 API server 통신하기

## Server & Client

> Server

- 서버(server)란?

  - 클라이언트에게 정보와 서비스를 제공하는 컴퓨터 시스템
  - 서비스 전체 제공 == Django Web Service
  - 정보 제공 == DRF API Service

- 서비스 전체 제공 == Django Web Service

  - Django를 통해 전달받은 HTML에는 하나의 웹 페이지를 구성할 수 있는 모든 데이터가 포함
  - 즉, 서버에서 모든 내용을 렌더링 하나의 HTML 파일로 제공
  - 정보를 포함한 web 서비스를 구성하는 모든 내용을 서버 측에서 제공

- 정보를 제공 == DRF API Service

  - Django를 통해 관리하는 정보만을 클라이언트에게 제공
  - DRF를 사용하여 JSON으로 변환

> Client

- 클라이언트(Client)란?

  - Server가 제공하는 서비스에 적절한 요청을 통해 Server로부터 반환 받은 응답을 사용자에게 표현하는 기능을 가진 프로그램 혹은 시스템

  - Server가 제공하는 서비스에 적절한 요청

    - Server가 정의한 방식대로 요청 인자를 넘겨 요청
    - Server는 정상적인 요청에 적합한 응답 제공

  - 잘못된 요청 예

    - 아래와 같은 Model이 정의되어 있다면

    ```python
    class Article(models.Model):
      title = models.CharField(max_length=100)
      content = models.TextField()
    ```

    - 잘못된 field 명으로 요청을 보낼 경우 처리할 수 없음

  - Server로부터 반환 받은 응답을 사용자에게 표현

    - 사용자의 요청에 적합한 data를 server에 요청하여 응답 받은 결과로 적절한 화면을 구성

> 정리

- Server는 정보와 서비스를 제공

  - DB와 통신하며 데이터를 생성, 조회, 수정, 삭제를 담당
  - 요청을 보낸 Client에게 정상적인 요청이었따면 처리한 결과를 응답

- Client는 사용자의 정보 요청을 처리, server에게 응답 받은 정보를 표현

  - Server에게 정보(데이터)를 요청
  - 응답 받은 정보를 가공하여 화면에 표현
