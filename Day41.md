# 20220901 TIL

## CRUD with view functions

### READ 1

> 전체 게시글 조회

- index 페이지에서는 전체 게시글을 조회해서 출력한다.

### CREATE

> 개요

- CREATE 로직을 구현하기 위해서는 몇 개의 view 함수가 필요할까?
  - 사용자의 입력을 받을 페이지를 렌더링 하는 함수 1개
    - "new" view function
  - 사용자가 입력한 데이터를 전송 받아 DB에 저장하는 함수 1개
    - "create" view function

---

## 복습

> Django Framework

- 사용자 > 요청 > urls > view > model > DB
- DB > model > view > template > 응답 > 사용자
- model의 class 1개가 DB table1개와 mapping (설계도 작성) : ORM을 통해 상호작용
  1. models.py 에 클래스 작성
  2. 마이그레이션 파일 생성 > 설계도 (make migrations)
  3. DB반영(migrate)

> CRUD 4가지

- Create
- Read
- Update
- Delete