# 20221004 TIL

## 데이터베이스

> 데이터베이스의 등장

- 데이터베이스는 많은 형태가 있지만 실제 가장 많이 쓰이는 유형은 RDB(Relational Datebase)라고 부르는 관계형 데이터베이스
- RDB는 각각의 데이터를 테이블에 기입함

> 데이터베이스 학습 목표

- 거대하고 복잡하고 데이터를 다루기 위해서 고안된 도구이기 때문에 매우 많은 기능 제공

  - 기능 많다 == 데이터 관련해서 할 수 있는 일들이 많다.
  - 모든 기능을 학습하는 것은 불필요 > 기초에 집중

- DB 학습의 기초

  - 데이터베이스에 데이터를 어떻게 입력하고 어떻게 출력하는가

- CRUD, 키워드 위주로 학습

> Database 정의

- 체계화된 데이터의 모임
- 검색, 구조화 같은 작업을 보다 쉽게 하기 위해 조직화된 데이터를 수집하는 저장 시스템

  - 내용을 고도로 구조화 함으로써 검색과 갱신의 효율화를 꾀한 것
  - 즉, 자료 파일을 조직적으로 통합하여 중복을 없애고 구조화하여 기억시켜 놓은 자료의 집합체

- 이러한 database를 조작하는 프로그램 = DBMS(Database Management System)

  - Oracle, MySQL, SQLite 등
  - DBMS에서 Database를 조작하기 위해 사용하는 언어를 SQL이라 함

- 웹 개발에서 대부분의 데이터베이스는 '관계형 데이터베이스 관리 시스템(RDBMS)'을 사용하여 SQL로 데이터와 프로그래밍을 구성

## RDB

> RDB란?

- Relational Database(관계형 데이터베이스)
- 데이터를 테이블, 행, 열 등으로 나누어 구조화 하는 방식
- 자료를 여러 테이블로 나누어 관리하고, 이 테이블간 관계를 설정해 여러 데이터를 쉽게 조작
- SQL을 사용하여 데이터 조회, 조작

> RDB 기본 구조

1. 스키마
2. 테이블

   - 필드
   - 레코드
   - 기본키

> 스키마

- 테이블의 구조
- 자료의 구조, 표현 방법, 관계 등 전반적인 명세 기술

> 테이블

- 필드와 레코드를 사용해 조직된 데이터 요소들의 집합
- 관계라고도 부름

1. 필드(field)

   - 속성, 컬럼(Column)

2. 레코드(record) : 테이블의 데이터 저장

   - 튜플, 행(Row)

> PK (Primary Key)

- 기본 키
- 각 레코드의 고유한 값

  - 데이터 구분 가능

- 기술적으로 다른 항목과 절대로 중복될 수 없는 단일 값(unique)

> 관계형 데이터베이스의 이점

- 데이터를 직관적으로 표현
- 관련 데이터에 쉽게 접근
- 대량의 데이터도 효율적으로 관리

> RDBMS

- Relational Database Management System(관계형 데이터베이스 관리 시스템)

> SQLite

- 응용 프로그램에 파일 형식으로 넣어 사용하는 비교적 가벼운 데이터베이스
- 안드로이드, iOS, macOS에 기본탑재, 임베디드 소프트웨어에서도 많이 활용
- 오픈 소스 프로젝트이기 때문에 자유롭게 사용가능

> SQLite 단점

- 대규모 동시 처리 작업에는 적합하지 않음
- 다른 RDMBS에서 지원하는 SQL 기능을 지원하지 않을 수 있음

> SQLite 를 학습하는 이유

- 어떤 환경에서나 실행 가능한 호환성
- 데이터 타입이 비교적 적고 강하지 않기 때문에 유연한 학습 환경 제공
- Django Framework의 기본 데이터베이스

## SQL

> SQL이란?

- Structured Query Language
- RDBMS의 데이터를 관리하기 위해 설계된 특수 목적의 프로그래밍 언어
- RDBMS에서 데이터베이스 스키마 생성, 수정이 가능하고 테이블에서 자료검색 및 관리도 할 수 있음
- 데이터베이스 객체에 대한 처리를 관리하거나 접근 권한을 설정하여 허가된 사용자만 RDBMS를 관리할 수 있도록 할 수 있음

> SQL 정리

- SQL == 데이터베이스와 상호작용 하는 방법
- 따라서 SQL을 배우면서 Database의 동작원리 또한 익힐 수 있음

## SQL Commands

> SQL Commands 종류

- 특성에 따라 세 가지 그룹으로 분류

1. DDL(Data Definition Language) - 데이터 정의 언어
2. DML(Data Manipulation Language) - 데이터 조작 언어(CRUD)
3. DCL(Data Control Language) - 데이터 제어 언어

## SQL Syntax

> SQL Syntax

- 모든 SQL 문(statement)는 SELECT, INSERT, UPDATE 등과 같은 키워드로 시작하고, 하나의 statement는 세미콜론(;)으로 끝남

  - 세미콜론은 각 SQL문을 구분하는 표준 방법

- SQL 키워드는 대소문자 구분 X

  - 즉, SELECT 와 select는 SQL에서 동일한 의미
  - 하지만 대문자로 작성하는 것을 권장

- SQL에 대한 세부적인 문법 사항들은 이어지는 DDL, DML로 익혀보기

> Statement & Clause

- Statement (문)

  - 독립적으로 실행할 수 있는 완전한 코드 조각
  - statement는 clause로 구성됨

- Clause (절)

  - statement의 하위 단위

## DDL

> 개요

- SQL 데이터 정의 언어를 사용하여 테이블 데이터베이스 개체를 만드는 방법 학습
- DDL은 테이블 구조 관리

  - CREATE, ALTER, DROP

### CREATE TABLE

> CREATE TABLE statement

- Create a new table in the database
- 데이터베이스에 새 테이블을 만듦

> CRREATE TABLE 실습

- id 컬럼은 우리가 직접 정의하지 않으면 자동으로 rowid라는 컬럼으로 만들어짐
- 먼저 테이블을 생성 하면서 작성한 데이터 타입과 제약 조건을 알아본다.

### SQLite Data Types

> Data Types 종류

1. NULL

- 정보가 없거나 알 수 없음

2. INTEGER

- 정수
- 크기에 따라 가변 크기

3. REAL

- 실수
- 8바이트 부동 소수점을 사용하는 10진수 값이 있는 실수

4. TEXT

- 문자 데이터

5. BLOB

- 입력된 그대로 저장된 데이터 덩어리(대용 타입 없음)
- 바이너리 등 멀티미디어 파일
- ex. 이미지 데이터

> Boolean type

- SQLite에는 별도의 Boolean 타입이 없음
- 대신 Boolean 값은 정수 0과 1로 저장됨

> Date & Time Datatype

- SQLite에는 날짜 및 시간을 저장하기 위한 타입이 없음
- 대신 buit-in "Date And Time Functions"으로 Text, REAL 또는 INTEGER 값으로 저장할 수 있음

> Binary Data

- 데이터의 저장과 처리를 목적으로 0과 1의 이진 형식으로 인코딩 된 파일

> SQLite 데이터 타입 결정

- 값에 둘러싸는 따옴표와 소수점 또는 지수가 없으면 - INTEGER
- 값이 작은 따옴표나 큰 따옴표로 묶이면 - TEXT
- 값에 따옴표나 소수점, 지수가 없으면 - REAL
- 값이 따옴표 없이 NULL 이면 - NULL

> SQLite Datatypes 특징

- 동적 타입 시스템 사용

  - 컬럼에 저장된 값에 따라 데이터 타입이 결정됨

- 테이블 생성 시 컬럼에 대해 특정 데이터 타입을 따로 선언하지 않아도 됨

  - 동적 타입 시스템 이용 시 기존의 엄격하게 타입이 지정된 데이터베이스에서는 불가능한 작업을 유연하게 수행할 수 있음
  - 정적 타입 시스템이 지정된 데이터베이스에서 작동하는 SQL 문이 SQLite에서 동일한 방식으로 작동한다는 점
  - 다른 데이터베이스와 호환성 문제 때문에 데이터 타입 지정 권장

- SQLite는 데이터가 더 강하다.
- 데이터 타입을 지정하게 되면 SQLite 는 입력된 데이터의 타입을 지정된 데이터 타입으로 변환

> static(정적), rigid(엄격한) typing Database

- 컬럼에 선언된 데이터 타입에 의해 결정된다.

> Type Affinity

- 타입 선호도
- 특정 컬럼에 저장된 데이터에 권장되는 타입
- SQLite의 데이터 타입이 아닌 다른 데이터 타입을 선언한다면, 내부적으로 각 타입의 지정된 선호도에 따라 5가지 선호도로 인식됨

1. INTEGER
2. TEXT
3. BLOD
4. REAL
5. NUMERIC

- 타입 선호도 존재 이유

  - 다른 DB 엔진간의 호환성을 최대화
  - 정적이고 엄격한 타입을 사용하는 데이터베이스의 SQL문을 SQLite에서도 작동하도록 하기 위함

### Constraints

> 개요

- 제약 조건
- 사용자가 원하는 조건의 데이터만 유지하기 위한 즉, 데이터의 무결성을 유지하기 위한 보편적인 방법으로 테이블의 특정 컬럼에 설정하는 제약

> 데이터 무결성

- 데이터 베이스 내의 데이터에 대한 정확성, 일관성을 보장하기 위해 데이터 변경, 수정 시 여러 제한을 두어 데이터의 정확성을 보증하는 것

  - 무결성이란 데이터의 정확성, 일관성을 나타냄

> Constraints 종류

1. NOT NULL

- 컬럼이 NULL 값을 허용하지 않도록 지정
- 기본적으로 테이블의 모든 컬럼은 NOT NULL 제약 조건을 명시적으로 사용하는 경우를 제외하고 NULL 값 허용

2. UNIQUE

- 컬럼의 모든 값이 서로 구별되거나 고유한 값이 되도록 함

3. PRIMARY KEY

- 테이블에서 행의 고유성을 식별하는데 사용되는 컬럼
- 각 테이블에는 하나의 기본 키만 있음
- 암시적으로 NOT NULL 제약 조건 포함되어 있음

4. AUTOINCREMENT

- 사용되지 않은 값이나 이전에 삭제된 행의 값을 재사용 하는 것을 방지
- INTEGER PRIMARY KEY 다음에 작성하면 해당 rowid를 다시 재사용하지 못하도록 함

5. 그 외 기타 Constraints

> rowid의 특징

- 테이블을 생성할 때마다 rowid라는 암시작 자동 증가 컬럼이 자동으로 생성됨
- 테이블의 행을 고유하게 식별하는 64비트 부호 있는 정수 값
- 테이블에 새 행을 삽입할 때마다 정수 값을 자동으로 할당

  - 1에서 시작
  - 데이터 삽입 시 INTEGER PRIMARY KEY 컬럼에 명시적으로 값이 지정되지 않은 경우, SQLite는 테이블에서 가장 큰 rowid보다 하나 큰 다음 순차 정수를 자동으로 할당

- 만약 INTEGER PRIMARY KEY 키워드를 가진 컬럼은 직접 만들면 이 컬럼은 rowid 컬럼의 별칭(alias)이 됨

  - 즉, 새 컬럼 이름으로 rowid 에 액세스 할 수 있으며 rowid 이름으로도 여전히 액세스 가능

- 데이터가 최대 값에 도달하고 새 행을 삽입하려고 하면 SQLite는 사용되지 않은 정수를 찾아 사용
- 만약 SQLite가 사용되지 않은 정수를 찾을 수 없으면 SQLITE_FULL 에러 발생

## ALTER TABLE

> 개요

- 기존 테이블의 구조 수정(변경)

1. ALTER TABLE RENAME

- Rename a table (테이블명 변경)

2. ALTER TABLE RENAME COLUMN

- Rename a column(컬럼명 변경)

3. ALTER TABLE ADD COLUMN

- Add a new column to a table(새 컬럼 추가)
- 테이블에 기존 데이터가 있을 경우 에러 발생
- default 제약 조건을 사용하여 해결할 수 있음

4. ALTER TABLE DROP COLUMN

- Delete a column(컬럼 삭제)
- 삭제하지 못하는 경우

  - 컬럼이 다른 부분에서 참조되는 경우
  - PRIMARY KEY인 경우
  - UNIQUE 제약 조건이 있는 경우

## DROP TABLE

> 개요

- 데이터베이스에서 테이블을 제거
- 존재하지 않는 테이블을 제거하면 SQLite에서 오류 발생

> DROP TABLE 특징

- 한번에 하나의 테이블만 삭제 가능
- 여러 테이블을 제거하려면 여러 DROP TABLE문을 실행해야 함
- 실행 취소, 복구 X

## DML

> 개요

- DML을 통해 데이터를 조작하기(CRUD)
- INSERT(Create), SELECT(READ), UPDATE, DELETE

### Simple query

> 개요

- SELECT 문을 사용하여 간단하게 단일 테이블에서 데이터 조회

> SELECT statement

- 특정 테이블에서 데이터를 조회하기 위해 사용
- 문법 규칙

  1. SELECT 절에서 컬럼 또는 쉼표로 구분된 컬럼 목록을 지정
  2. FROM 절에서 데이터를 가져올 테이블을 지정

### Sorting rows

> 개요

- ORDER BY 절을 사용하여 쿼리의 결과를 정렬하기

> ORDER BY clause

- SELECT 문에 추가하여 결과를 정렬
- ORDER BY 절은 FROM 절 뒤에 위치함
- 하나 이상의 컬럼을 기준으로 결과를 오름차순, 내림차순으로 정렬할 수 있음
- 이를 위해 ORDER BY 절 다음에 'ASC' 또는 'DESC' 키워드 사용

  - ASC : 오름차순(기본값)
  - DESC : 내림차순

> Sorting NULLs

- NULL 의 정렬방식
- 정렬과 관련하여 SQLite 는 NULL 을 다른 값보다 작은 것으로 간주
- 즉, ASC 사용 시 시작부분에 표시, DESC사용 시 끝에 NULL 표시

### Filtering data

> 개요

- 데이터를 필터링하여 중복 제거, 조건 설정 등 쿼리 제어

> SELECT DISTINCT clause

- 조회 결과에서 중복된 행 제거
- DISTINCT 절은 SELECT에서 선택적으로 사용할 수 있는 절
- 문법 규칙

  1. DISTINCT 절은 SELECT 키워드 바로 뒤에 나타나야 함
  2. DISTINCT 키워드 뒤에 컬럼 또는 컬럼 목록 작성

> NULL with DISTINCT

- SQLite 는 NULL 값을 중복으로 간주
- NULL 값이 있는 컬럼에 DISTINCT 절을 사용하면 SQLite는 NULL값의 한 행을 유지

> WHERE clause

- 조회 시 특정 검색 조건을 지정
- WHERE 절은 SELECT 문에서 선택적으로 사용할 수 있는 절

  - SELECT 문 외에도 UPDATE 및 DELETE 문에서 WHERE 절을 사용할 수 있음

- FROM 절 뒤에 작성

> SQLite compraison operators (비교연산자)

- 두 표현식이 동일한지 테스트

  - =
  - <> or !=
  - <
  - \>
  - <=
  - \>=

> SQLite logical operators (논리연산자)

- 일부 표현식의 truth를 테스트 할 수 있음
- 1, 0 또는 NULL 값을 반환
- SQLite는 Boolean 데이터 타입을 제공하지 않으므로 1은 TRUE를 의미하고 0은 FALSE를 의미
- ALL, AND, ANY, BETWEEN, IN, LIKE, NOT, OR 등

> LIKE operator

- 패턴 일치를 기반으로 데이터 조회
- SELECT, DELETE, UPDATE 문의 WHERE 절에서 사용
- 기본적으로 대소문자 구분 x
- 패턴 구성을 위한 두 가지 와일드카드 제공

  1. %(percent)

     - 0개 이상의 문자가 올 수 있음을 의미

  2. \_(underscore)

     - 단일(1개) 문자가 있음을 의미

> % wildcard 예시

- 영% 패턴은 영으로 시작하는 모든 문자열과 일치
- %도 패턴은 도로 끝나는 모든 문자열과 일치
- %강원% 패턴은 강원을 포함하는 모든 문자열과 일치

> \_ wildcard 예시

- 영\_ 패턴은 영으로 시작하고 총 2자리인 문자열과 일치
- \_도 패턴은 도로 끝나고 총 2자리인 문자열과 일치

> wildcards character

- 파일을 지정할때, 구체적인 이름 대신에 여러 파일을 동시에 지정할 목적으로 사용하는 특수 기호

  - \*, ? 등

- 주로 특정한 패턴이 있는 문자열 혹은 파일을 찾거나, 긴 이름을 생략할 때 쓰임

> IN operator

- 값이 값 목록 결과에 있는 값과 일치하는지 확인
- 표현식이 값 목록의 값과 일치하는지 여부에 따라 true, false를 반환
- IN 연산자의 결과를 부정하려면 NOT IN 연산자 사용

> BETWEEN operator

- 값이 값 범위에 있는지 테스트
- SELECT, DELETE, UPDATE문의 WHERE절에서 사용 가능
- NOT BETWEEN 있음

> LIMIT clause

- 쿼리에서 반환되는 행 수를 제한
- SELECT 문에서 선택적으로 사용할 수 있는 절
- row_count는 반환되는 행 수를 지정하는 양의 정수를 의미

> OFFSET keyword

- OFFSET과 함께 사용하면 특정 지정된 위치에서부터 데이터 조회 가능

### Grouping data

> GROUP BY clause

- 특정 그룹으로 묶인 결과를 생성
- 선택된 커럼 값을 기준으로 데이터(행)들의 공통 값을 묶어서 결과로 나타냄
- SELECT문에서 선택적으로 사용가능한 절

> Aggregate function

- 집계 함수
- 값 집합의 최대값, 최소값, 평균, 합계 및 개수를 계산
- SELECT 문의 GROUP BY 절과 함께 종종 사용됨
- 제공 함수 목록

  - AVG, COUNT, MAX, MIN, SUM

- AVG, MAX, MIN, SUM은 반드시 컬럼의 데이터 타입이 숫자(INTEGER)일 때만 사용 가능

> COUNT 참고사항

- 이전 쿼리에서 column의 이름만 다르지 COUNT(), COUNT(age), COUNT(last_name) 등 어떤 컬럼을 넣어도 결과는 같음
- 현재 쿼리에서는 그룹화 된 country를 기준으로 카운트 하는 것이기 때문에 어떤 컬럼을 카운트해도 전체 개수는 동일하기 때문

### Changing data

> 개요

- 데이터 삽입, 수정, 삭제

  - INSERT
  - UPDATE
  - DELETE

> INSERT statement

- 새 행을 테이블에 삽입
- 문법 규칙

  1. 먼저 INSERT INTO 키워드 뒤에 데이터를 삽입할 테이블의 이름을 지정
  2. 테이블 이름 뒤에 쉼표로 구분된 컬럼 목록을 추가

     - 컬럼 목록은 선택사항이지만, 컬럼 목록을 포함하는 것이 권장됨

  3. VALUES 키워드 뒤에 쉼표로 구분된 값 목록을 추가

     - 만약 컬럼 목록을 생략하는 경우 값 목록의 모든 컬럼에 대한 값을 지정해야 함
     - 값 목록의 값 개수는 컬럼 목록의 컬럼 개수와 같아야 함

> UPDATE statement

- 테이블에 있는 기존 행의 데이터를 업데이트 한다.
- 문법 규칙

  1. UPDATE 절 이후에 업데이트 할 테이블 지정
  2. SET 절에서 테이블의 각 컬럼에 대해 새 값을 설정
  3. WHERE 절의 조건을 사용하여 업데이트할 행을 지정

     - WHERE 절은 선택사항이며, 생략하면 모든 행에 있는 데이터를 업데이트 함

  4. 선택적으로 ORDER BY 및 LIMIT 절을 사용하여 업데이트 할 행수를 지정할 수도 있음

> DELETE statement

- 테이블에서 행을 제거
- 테이블의 한 행, 여러 행 및 모든 행 삭제 가능
- 문법 규칙

  1. DELETE FROM 키워드 뒤에 행을 제거하려는 테이블의 이름을 지정
  2. WHERE 절에 검색 조건을 추가하여 제거할 행을 식별

     - WHERE 절은 선택 사항이며, 생략하면 DELETE 문은 테이블의 모든 행을 삭제

  3. 선택적으로 ORDER BY 및 LIMIT 절을 사용하여 삭제할 행 수를 지정할 수도 있음
