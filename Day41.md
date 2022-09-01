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