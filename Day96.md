# 20230105 TIL

# JIRA

- 사용 이유

1. Issue Tracking(Project Management)
2. Agile
3. DevOps
4. SRE

> Agile

- Scrum vs Kanban

> DevOps

- 운영


--- 

# JIRA 사용법

1. Create Issue

- 현재, Jira Cloud로 변환이 됨(SASS)

> Epic

1. 내가 속한 프로젝트가 나옴
2. 이슈 타입 - test, story, bug, epic, (subtask)

   - Epic: 사용자 권리라는 큰 틀을 만들고 할일을 집어넣는 개념

3. Epic 안에 Todo, In Progress, DONE 상태가 있음
4. Summary : 개요 -> 제목이라고 생각하면 된다.
5. Epic 에서만 Epic Name 작성 -> 다른 이슈 타입에서 Epic Name을 지정 할 수 있음
6. Component는 Epic하고 헷갈릴 수 있으나, 하나의 단위이다. ex. UX, 인프라 분류

   - 이름과 설명과 리더를 정할 수 있다. 이 컴포넌트를 지정해줄 때 assign(담당자) 지정 가능
   - 카테고리로 묶는 개념

7. 관련된 이슈가 있으면 link
8. Fix version : 실제로 어떤 버전에서 release 할 것인지.
9. Assign: 담당자 지정
10. Priority
11. Label: 라벨링 하는 것. 미리 선택해주고 카테고리화 가능

    - 특징 : 컴포넌트는 미리 지정해주고 그 안에서만 선택할 수 있었으나, label은 자유형식으로 사용 가능
    - 대소문자를 구분하기 때문에 라벨을 잘못 적으면 다르게 분류될 수 도 있다.

12. Epic Link
13. Sprint: 어떤 Sprint를 할당할 지 미리 지정 가능

- 보통 Epic 안에 Story, Task, Bug 가 담기게 됨

  - Story : User Story를 작성
  - Task : User Story가 아닌 데에 해야할 일
  - Bug : 이미 개발이 되었으나 버그가 일어났을 경우 작성

> Bug

- Affects version, fix version 이 다르다.

  - Affects: 버그가 영향 받는 version
  - fix : 버그를 고칠 version

# JQL

- Jira Query Language
- Jira Issue 를 구조적으로 검색하기 위해 제공하는 언어
- SQL(Standard Query Language) 과 비슷한 문법
- Jira 의 각 필드들에 맞는 특수한 예약어 들을 제공
- 쌓인 Issue 들을 재가공해 유의미한 데이터를 도출해 내는데 활용(Gadget, Agile Board 등)

> Basic Query & Advanced Query

- Basic Query

  - 선택을 해서 검색을 하는 Query

- Advanced Query

  - 작성을 해서 검색

- 미리보기 제공

> JQL Operators

- =, !=, >, >=
- in, not in
- ~ (contains), !~(not contains)
- is empty, is not empty, is null, is not null

> JQL Keywords

- AND
- OR
- NOT
- EMPTY
- NULL
- ORDER BY

> JQL Dates

- Relative Dates

  - 오늘 기준으로 내일 날짜는 1d, 어제 날짜는 -1d, 다음주 목요일은 1w 등으로 표현 가능

> JQL Functions

- endOfDay() : 오늘 하루 끝
- startOfDay() : 오늘 하루 첫시간
- endOfWeek() : 한 주의 끝(토요일)
- startOfWeek() : 한 주의 시작(일요일)
- endOfMonth(), startOfMonth, endOfYear(), startOfMonth()
- currentUser() : 현재 로그인 한 사용자
- endOfWeek(-1d) : 월요일부터 금요일까지

> JQL 활용 예시 : filter share

- issue 에 JQL 을 사용하여 걸러내고
- filter로 저장하고 사용할 수 있음
