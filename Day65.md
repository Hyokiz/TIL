# 20221016 TIL

> 데이터베이스

- 서비스 혹은 애플리케이션들이 데이터를 저장하는 곳
- 데이터베이스에는 많은 형태가 있지만 실제로 많이 쓰이는 유형은 RDB(Relational Database)라고 불리는 관계형 데이터베이스

> Database 정의

- 체계화된 데이터의 모임
- Database를 조작하는 프로그램 = DBMS(Database Management System)

  - DBMS에서 Database를 조작하기 위해 사용하는 언어를 SQL

- 웹 개발에서 대부분의 데이터베이스는 관계형 데이터베이스 관리 시스템(RDBMS)을 사용하여 SQL로 데이터와 프로그래밍 구성

## RDB

> RDB란?

- Relational Database(관계형 데이터베이스)
- 데이터를 테이블, 행, 열 등으로 나누어 구조화 하는 방식
- 자료를 여러 테이블로 나누어서 관리하고, 이 테이블간 관계를 설정해 여러 데이터를 쉽게 조작할 수 있다는 장점
- SQL을 사용하여 데이터를 조회하고 조작

> 테이블간 관계 설정 예시

- 고객 테이블에서 고객 ID는 기본 키 (primary key)
- 주문 테이블에서 특정 주문을 식별하는 기본 키는 주문 ID

  - 외래 키(foreign key)를 사용하여 고객 테이블의 고객 ID를 연결

> RDB 기본 구조

1. 스키마
2. 테이블

   - 필드
   - 레코드
   - 기본 키

> 스키마

- 테이블의 구조
- DB에서 자료의 구조, 표현 방법, 관계 등 전반적인 명세 기술

> 테이블(Table)

- 필드와 레코드를 사용해 조직된 데이터 요소들의 집합
- 관계(Relation)라고도 부름

  1. 필드(field)

     - 속성, 컬럼(Column)

  2. 레코드(record)

  - 튜플, 행(Row)

> 필드(Field)

- 속성 혹은 컬럼
- 고유한 데이터 형식(타입)

> 레코드(Record)

- 튜플 혹은 행
- 테이블의 데이터 저장

> PK(Primary Key)

- 기본 키
- 각 레코드의 고유한 값

  - 각 데이터 구분

- 기술적으로 다른 항목과 중복될 수 없는 단일 값(unique)

> 관계형 데이터베이스의 이점

- 데이터를 직관적으로 표현
- 관련한 각 데이터에 쉽게 접근
- 대량의 데이터 효율적으로 관리

> RDBMS

- Relational Database Management System(관계형 데이터베이스 관리 시스템)

> SQLite

- 응용 프로그램에 파일 형식으로 넣어 사용하는 비교적 가벼운 DB
- 오픈 소스 프로젝트

## SQL

- Structured Query Language
- 특수 목적의 프로그래밍 언어
- RDBMS에서 데이터베이스의 스키마를 생성 및 수정, 테이블에서의 자료 검색 및 관리
- DB 객체에 대한 처리 관리, 접근 권한을 설정하여 허가된 사용자면 RDBMS관리할 수 있도록 할 수 있음

> SQL 정리

- SQL은 데이터베이스와 상호작용 하는 방법
- SQL을 배우면서 DB의 동작원리도 익힐 수 있다.

## SQL Commands

> SQL Commands 종류

1. DDL(Data Definition Language)

   - 관계형 데이터베이스 구조(테이블, 스키마)를 정의하기 위한 명령어
     - CREATE, DROP, ALTER

2. DML(Data Manipulation Language)

   - 데이터를 조작(추가, 조회, 변경, 삭제)하기 위한 명령어
     - INSERT, SELECT, UPDATE, DELETE

3. DCL(Data Control Language)

## SQL Syntax

- 모든 SQL 문은 SELECT, INSERT, UPDATE 등과 같은 키워드로 시작. 세미콜론(;)으로 끝남

  - 세미콜론은 각 SQL 문을 구분하는 표준 방법

- SQL 키워드는 대소문자 구별 X

  - 동일한 의미지만 대문자로 작성하는 것을 권장

> Statement & Clause

- Statement (문)

  - 독립적으로 실행할 수 있는 완전한 코드 조각
  - statement 는 clause로 구성됨

- Clause (절)

  - statement의 하위 단위

## DDL

> 개요

- Data definition
- 테이블 데이터베이스 개체 만들기
- 테이블 구조 관리

  - CREATE, ALTER, DROP

### CREATE TABLE

> CREATE TABLE statement

- 데이터베이스에 새 테이블 만듦

- contacts 테이블 생성

```sql
CREATE TABLE contacts(
    name TEXT NOT NULL,
    age INTEGER NOT NULL,
    email TEXT NOT NULL UNIQUE
);
```

- 쿼리 실행 후 스키마 확인
- id 컬럼은 기본 키 역할의 컬럼을 정의 하지 않으면 rowid라는 컬럼으로 생성

## SQLite Data Types

> Data Types 종류

1. NULL

   - NULL value
   - 정보가 없거나 알 수 없음

2. INTEGER

   - 정수
   - 크기에 따라 가변 크기

3. REAL

   - 실수

4. TEXT

   - 문자 데이터

5. BLOB(Binary Large Object)

   - 입력된 그대로 저장된 데이터 덩어리
   - 바이너리 등 멀티미디어 파일

> Boolean type

- SQLite에는 별도의 Boolean 타입 없다.
- 대신 0과 1로 저장됨

> Date & Time Datetype

- SQLite 에는 날짜 및 시간을 저장하기 위한 타입이 없다
- 대신 built-in 'Date And Time Functions'으로 Text, REAL 또는 INTEGER 값으로 저장할 수 있다.

> Binary Data

- 데이터 저장, 처리를 목적으로 0과 1의 이진 형식으로 인코딩 된 파일

> SQLite 규칙

- 값이 작은 따옴표나 큰 따옴표로 둘러 쌓이면 - TEXT
- 값에 둘러싸는 따옴표가 있고, 소수점 또는 지수가 없으면 - INTEGER
- 값에 따옴표가 없고, 소수점 또는 지수가 있으면 - REAL
- 값이 따옴표 없이 NULL이면 - NULL

> SQLite Datatypes 특징

- SQLite는 다른 모든 SQL의 정적이고 엄격한 타입(static, rigid typing)이 아닌 동적 타입(dynamic type system)사용

  - 컬럼에 저장된 값에 따라 데이터 타입 결정

- 또한 테이블을 생성할 때 컬럼에 대해 특정 데이터 타입을 선언하지 않아도 됨

  - 동일한 컬럼에 정수 1 넣을 경우 INTEGER, '1'을 넣을 경우 TEXT 타입
  - 다른 DB에서 불가능한 작업을 유연하게 수행 가능
  - 하지만 호환성 문제가 있기 때문에 데이터 타입 지정 권장

- 데이터 타입 지정 시 지정된 데이터 타입으로 변환

> static, rigid typing 데이터베이스

- statically, rigidly typed databases 라고도 부름
- 저장되는 값의 데이터 타입은 컬럼에 선언된 데이터 타입에 의해 결정
- ex.

```sql
CREATE TABLE my_table(
    a INTEGER NOT NULL,
    b TEXT NOT NULL,
);
```

- a 컬럼에 '123', b 컬럼에 456 데이터 삽입하면 123은 정수로 456은 문자열'456'으로 변환

> Type Affinity

- 타입 선호도
- 특정 컬럼에 저장된 데이터에 권장되는 타입
- 데이터 타입 작성 시 SQLite 의 5가지 데이터 타입이 아닌 다른 데이터 타입을 선언한다면 내부적으로 각 타입의 지정된 선호도에 따라 5가지 선호도로 인식됨

1. INTEGER
2. TEXT
3. BLOB
4. REAL
5. NUMERIC

- 타입 선호도 존재 이유

  - 다른 데이터베이스 엔진 간의 호환성 최대화
  - 정적이고 엄격한 타입을 사용하는 데이터베이스의 SQL문을 SQLite에서도 작동하도록 하기 위함

## Constraints

> 개요

- 제약조건
- 입력하는 자료에 대해 제약을 정함
- 제약에 맞지 않다면 입력이 거부
- 사용자가 원하는 조건의 데이터만 유지하기 위한. 즉, 데이터의 무결성을 유지하기 위한 보편적인 방법으로 테이블의 특정 컬럼에 설정하는 제약

> 데이터 무결성

- 데이터베이스 내 데이터에 대한 정확성, 일관성을 보장하기 위해 데이터 변경 혹은 수정 시 여러 제한을 두어 데이터의 정확성을 보증하는 것

  - 무결성이란 데이터의 정확성, 일관성

- 데이터베이스에 저장된 데이터의 무결성을 보장하고 데이터베이스의 상태를 일관되게 유지하는 것이 목적

> Constraints 종류

1. NOT NULL

   - 컬럼이 NULL 값을 허용하지 않도록 지정
   - 기본적으로 NOT NULL을 명시적으로 사용하는 경우를 제외하고 NULL 허용

2. UNIQUE

   - 컬럼의 모든 값이 서로 구별되거나 고유한 값이 되도록 함

3. PRIMARY KEY

   - 행의 고유성을 식별하는데 사용되는 컬럼
   - 각 테이블에는 하나의 기본 키만
   - 암시적으로 NOT NULL

4. AUTOINCREMENT

   - 사용되지 않은 값이나 이전에 삭제된 행의 값을 재사용하는 것 방지
   - INTEGER PRIMARY KEY 다음에 작성하면 해당 rowid를 다시 재사용하지 못하도록 함
   - Django에서 테이블 생성 시 id 컬럼에 기본적으로 사용하는 제약조건

5. 그 외 기타

> rowid의 특징

- 테이블을 생성할 때마다 rowid라는 암시적 자동 증가 컬럼이 자동으로 생성
- 테이블의 행을 고유하게 식별
- 새 행을 삽입할 때마다 정수 값을 자동으로 할당

  - 값은 1에서 시작
  - 데이터 삽입 시 rowid 또는 INTEGER PRIMARY KEY 컬럼에 명시적으로 값이 지정되지 않은 경우, SQLite는 테이블에서 가장 큰 rowid보다 하나 큰 다음 순차 정수를 자동으로 할당

- 만약 INTEGER PRIMARY KEY 키워드를 가진 컬럼을 직접 만들면 이 컬럼은 rowid 컬럼의 별칭(alias)이 됨

  - 즉, 새 컬럼 이름으로 rowid에 액세스 할 수 있으며 rowid 이름으로도 여전히 액세스 가능

- 데이터가 최대 값에 도달하고 새 행을 삽입하려고 하면 SQLite는 사용되지 않는 정수를 찾아 사용
- 찾을 수 없다면 SQLITE_FULL 에러

  - 일부 행을 삭제하고 새 행을 삽입하면 SQLite는 삭제된 행에서 rowid값을 재사용하려고 시도

## ALTER TABLE

> 개요

- 기본 테이블의 구조 수정(변경)

> 1. ALTER TABLE RENAME

- 테이블 명 변경

```sql
ALTER TABLE contacts RENAME TO new_contacts;
```

> 2. ALTER TABLE RENAME COLUMN

- 컬럼명 변경

```sql
ALTER TABLE new_contacts RENAME COLUMN name TO last_name;
```

> 3. ALTER TABLE ADD COLUMN

- 새 컬럼 추가

```sql
ALTER TABLE new_contacts ADD COLUMN address TEXT NOT NULL;
```

- 테이블에 기존 데이터가 있을 경우 에러

```sql
Cannot add NOT NULL column with default value NULL
```

- 이전에 이미 저장된 데이터들은 새롭게 추가되는 컬럼에 값이 없기 때문에 NULL
- 그런데 새로 추가되는 컬럼에 NOT NULL 제약조건이 있기 때문에 기본 값 없이는 추가될 수 없다는 에러

- 다음과 같이 DEFAULT 제약 조건 사용하면 해결

```sql
ALTER TABLE new_contacts ADD COLUMN address TEXT NOT NULL DEFAULT 'no address';
```

- 이렇게 하면 기존 데이터들의 address 컬럼값은 'no address'

> DEFAULT 제약 조건

- column 제약 조건 중 하나
- 데이터 추가할 때 값을 생략할 시 기본 값 설정

> 4. ALTER TABLE DROP COLUMN

- 컬럼 삭제

```sql
ALTER TABLE new_contacts DROP COLUMN address;
```

- 삭제하지 못하는 경우

  - 컬럼이 다른부분에서 참조되는 경우

    - FOREIGN KEY(외래 키) 제약 조건에서 사용되는 경우

  - PRIMARY KEY인 경우
  - UNIQUE 제약 조건이 있는 경우

```sql
ALTER TABLE new_contacts DROP COLUMN email;

Cannot drop UNIQUE column: 'email'
```

## DROP TABLE

- 데이터베이스에서 테이블 제거

```sql
DROP TABLE table_name;
```

- 존재하지 않는 테이블 제거 시 SQLite에서 오류 발생

```sql
no such table: table_name
```

```sql
DROP TABLE new_contacts;
```

> DROP TABLE 특징

- 한 번에 하나의 테이블만 삭제
- 여러 테이블을 제거하려면 여러 DROP TABLE 문을 실행해야 함
- 실행 취소, 복구 불가

> DDL 정리

- 데이터 정의 언어
- CREATE TABLE

  - 데이터 타입, 제약 조건

- ALTER TABLE

  - RENAME
  - RENAME COLUMN
  - ADD COLUMN
  - DROP COLUMN

- DROP TABLE

## DML
