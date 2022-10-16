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

> 개요

- DML 을 통해 데이터 조작(CRUD)
- INSERT, SELECT, UPDATE, DELETE

## Simple query

> 개요

- SELECT문을 사용하여 간단하게 단일 데이터 조회

```sql
SELECT column1, column2 FROM table_name;
```

- 특정 테이블에서 데이터 조회
- 문법 규칙

  1. SELECT 절에서 컬럼 또는 쉼표로 구분된 컬럼 목록 지정
  2. FROM 절에서 데이터를 가져올 테이블 지정

- 다양한 절과 사용 가능

> SELECT statement 실습

- 이름과 나이 조회

```sql
SELECT first_name, age FROM users;
```

- 전체 데이터 조회
  - \*(asterisk) 사용 가능

```sql
SELECT * FROM users;
```

- rowid 컬럼 같이 조회

```sql
SELECT rowid, first_name FROM users;
```

## Sorting rows

> 개요

- ORDER BY 절을 사용하여 쿼리의 결과 정렬

> ORDER BY clause

- SELECT 문에 추가하여 결과 정렬
- ORDER BY 절은 FROM 절 뒤에
- 하나의 컬럼을 기준으로 오름차순, 내림차순 정렬
- 이를위해 ORDER BY 절 다음에 ASC 또는 DESC 키워드 사용

  - ASC : 오름차순(기본)
  - DESC : 내림차순

> ORDER BY clause 실습

- 이름과 나이를 나이가 어린 순서대로 조회하기

```sql
SELECT first_name, age FROM users ORDER BY age ASC;

SELECT first_name, age FROM users ORDER BY age;
```

- 이름과 나이를 나이가 많은 순서대로 조회하기

```sql
SELECT first_name, age FROM users ORDER BY age DESC;
```

- 이름, 나이, 계좌잔고를 나이가 어린순으로, 만약 같은 나이라면 계좌 잔고가 많은 순으로 정렬해서 조회하기

```sql
SELECT first_name, age, balance FROM users
ORDER BY age ASC, balance DESC;
```

- ORDER BY 절은 하나 이상의 컬럼을 정렬할 경우 첫 번째 열을 사용하여 행 정렬하고, 두번째 컬럼을 사용하여 행 정렬
- 먼저 age 기준으로 오름차순 정렬, 이 결과를 balance 기준으로 내림차순 정렬

> Sorting NULLs

- NULL의 정렬 방식
- SQLite는 NULL을 다른 값보다 작은 것으로 간주
- 즉, ASC 사용 시 시작 부분에 NULL, DESC 사용 시 끝 부분에 NULL

## Filtering data

> 개요

- 데이터를 필더링하여 중복 제거, 조건 설정 등

> SELECT DISTINCT clause

- 중복된 행 제거
- SELECT에서 선태적으로 사용할 수 있는 절
- 문법 규칙

  1. SELECT 키워드 바로 뒤에 나타나야 함
  2. DISTINCT 키워드 뒤에 컬럼 또는 컬럼 목록 작성

> SELECT DISTINCT 실습

- 모든 지역 조회하기

```sql
SELECT country FROM users;
```

- 중복 없이 모든 지역 조회하기

```sql
SELECT DISTINCT country FROM users;
```

- 지역 순으로 오름차순 정렬하여 중복 없이 모든 지역 조회하기

```sql
SELECT DISTINCT country FROM users ORDER BY country;
```

- 이름과 지역이 중복 없이 모든 이름과 지역 조회하기

```sql
SELECT DISTINCT first_name, country FROM users;
```

- 이름과 지역 중복 없이 지역 순으로 오름차순 정렬하여 모든 이름과 지역 조회하기

```sql
SELECT DISTINCT first_name, country FROM users
ORDER BY country;
```

> NULL with DISTINCT

- SQLite는 NULL 값을 중복으로 간주
- NULL 값이 있는 컬럼에 DISTINCT 절을 사용하면 SQLite는 NULL 값의 한 행을 유지

> WHERE clause

- 조회 시 특정 검색 조건 지정
- SELECT문에서 선택적으로 사용

  - SELECT 문 외에도 UPDATE, DELETE문에서 WHERE 절 사용가능

- FROM 뒤에 작성

> SQLite comparison operators

- 두 표현식이 동일한지 테스트

  - =
  - <> or !=
  - <
  - \>
  - <=
  - \>=

> SQLite logical operators

- 일부 표현식의 truth 테스트
- 1, 0 또는 NULL 반환
- ALL, AND, ANY, BETWEEN, IN, LIKE, NOT, OR 등

> WHERE 실습

- 나이가 30살 이상인 사람들의 이름, 나이, 계좌 잔고 조회

```sql
SELECT first_name, age, balance FROM users
WHERE age >= 30;
```

- 나이가 30살 이상이고 계좌 잔고가 50만원 초과인 사람들의 이름, 나이, 계좌 잔고 조회하기

```sql
SELECT first_name, age, balance FROM users
WHERE age >= 30 AND balance > 500000;
```

> LIKE operator

- 패턴 일치를 기반으로 데이터 조회
- SELECT, DELETE, UPDATE 문의 WHERE 절에서 사용
- 대소문자 구분 X
- 두 개의 와일드카드 제공

1. % (percent)

   - 0개 이상의 문자가 올 수 있음

2. \_ (underscore)

   - 단일(1개) 문자가 있음

> wildcard 종합 예시

- 2% : 2로 시작하는 패턴
- %2 : 2로 끝나는 패턴
- %2% : 2를 포함하는 패턴
- \_2% : 첫 번째 자리에 아무값, 두번째가 2로 시작하는 패턴(최소 2자리)
- 1\_\_\_ : 1로 시작하는 4자리 패턴(반드시 4자리)
- 2\_%\_% or 2\_\_% : 2로 시작하고 최소 3자리인 패턴(3자리 이상)

> wildcards character

- 파일을 지정할 때, 구체적인 이름 대신에 여러 파일을 동시에 지정할 목적으로 사용하는 특수 기호

  - \*, ? 등

- 주로 특정한 패턴이 있는 문자열 혹은 파일을 찾거나, 긴 이름을 생략할 때
- 텍스트 값에서 알 수 없는 문자를 사용할 수 있는 특수 문자로, 유사하지만 동일한 데이터가 아닌 여러 항목을 찾기에 매우 편리한 문자
- 지정된 패턴 일치를 기반으로 데이터를 수집하는 데도 도움이 될 수 있음

> LIKE 실습

- 이름에 '호'가 포함되는 사람들의 이름과 성 조회하기

```sql
SELECT first_name, last_name FROM users
WHERE first_name LIKE '%호%';
```

- 이름이 '준'으로 긑나는 사람들의 이름 조회하기

```sql
SELECT first_name FROM users WHERE first_name LIKE '%준';
```

- 서울 지역 전화번호를 가진 사람들의 이름과 전화번호 조회하기

```sql
SELECT first_name, phone FROM users
WHERE phone LIKE '02-%';
```

- 나이가 20대인 사람들의 이름과 나이 조회하기

```sql
SELECT first_name, age FROM users WHERE age LIKE '2_';
```

- 전화번호 중간 4자리가 51로 시작하는 사람들의 이름과 전화번호 조회하기

```sql
SELECT first_name, phone FROM users
WHERE phone LIKE '%-51__-%';
```

> IN operator

- 값이 값 목록 결과에 있는 값과 일치하는지 확인
- true, false 반환
- IN 연산자의 결과를 부정하려면 NOT IN 연산자

> IN 실습

- 경기도 혹은 강원도에 사는 사람들의 이름과 지역 조회하기

```sql
SELECT first_name, country FROM users
WHERE country IN ('경기도', '강원도');
```

- IN 연산자 대신 OR 연산자를 사용하여 동일한 결과를 반환할 수 있음

```sql
SELECT first_name, country FROM users
WHERE country = '경기도' OR country = '강원도';
```

- 경기도 혹은 강원도에 살지 않는 사람들의 이름과 지역 조회하기

```sql
SELECT first_name, country FROM users
WHERE country NOT IN ('경기도', '강원도');
```

> BETWEEN operator

- 값이 값 범위에 있는지 테스트
- 있다면 True
- SELECT, DELETE 및 UPDATE 문의 WHERE 절에서 사용할 수 있음
- BETWEEN 연산자의 결과를 부정하려면 NOT BETWEEN 연산자 사용

> BETWEEN 실습

- 나이가 20살 이상, 30살 이하인 사람들의 이름과 나이 조회하기

```sql
SELECT first_name, age FROM users
WHERE age BETWEEN 20 AND 30;
```

- AND 연산자를 사용하여 이전 쿼리와 동일한 결과 반환

```sql
SELECT first_name, age FROM users WHERE age >= 20 and age <= 30;
```

- 나이가 20살 이상, 30살 이하가 아닌 사람들의 이름과 나이 조회하기

```sql
SELECT first_name, age FROM users
WHERE age NOT BETWEEN 20 AND 30;
```

- OR 연산자를 사용하여 이전 쿼리와 동일한 결과 반환

```sql
SELECT first_name, age FROM users WHERE age < 20 or age > 30;
```

> LIMIT clause

- 쿼리에서 반환되는 행 수를 제한
- SELECT 문에서 선택적으로 사용할 수 있는 절
- row_count는 반환되는 행 수를 지정하는 양의 정수를 의미

> LIMIT 실습

- 첫 번째부터 열 번째 데이터까지 rowid 와 이름 조회하기

```sql
SELECT rowid, first_name FROM users LIMIT 10;
```

- 계좌 잔고가 가장 많은 10명의 이름과 계좌 잔고 조회하기

```sql
SELECT first_name, balance FROM users
ORDER BY balance DESC LIMIT 10;

-- ORDER BY 절과 함께 사용하여 지정된 순서로 여러 행을 가져올 수도 있음
-- LIMIT 절에 지정된 행 수를 가져오기 전에 결과를 정렬하기 때문
```

- 나이가 가장 어린 5명의 이름과 나이 조회하기

```sql
SELECT first_name, age FROM users
ORDER BY age LIMIT 5;
```

> OFFSET keyword

- LIMIT 절을 사용하면 첫 번째 데이터부터 데이터를 받아올 수 있지만, OFFSET과 함께 사용하면 특정 지정된 위치에서부터 데이터를 조회할 수 있음

- 11번째부터 20번째 데이터의 rowid와 이름 조회하기

```sql
SELECT rowid, first_name FROM users
LIMIT 10 OFFSET 10;
```

## Grouping data

> GROUP BY clause

- 특정 그룹으로 묶인 결과 생성
- 선택된 컬럼 값을 기준으로 데이터들의 공통 값을 묶어서 결과로 나타냄
- SELECT 문에서 선택적으로 사용가능한 절
- SELECT 문의 FROM 절 뒤에 작성

  - WHERE 절이 포함된 경우 WHERE 절 뒤에

- 각 그룹에 대해 MIN, MAX, SUM, COUNT 또는 AVG와 같은 집계 함수를 적용하여 각 그룹에 대한 추가적인 정보를 제공할 수 있음

> Aggregate function

- 값 집합의 최대값, 최소값, 평균, 합계 및 개수 계산
- 값 집합에 대한 계산을 수행하고 단일 값 반환

  - 여러 행으로부터 하나의 결과 값을 반환하는 함수

- SELECT 문의 GROUP BY 절과 함께 종종 사용됨
- 제공 함수 목록

  - AVG(), COUNT(), MAX(), MIN(), SUM()

- 이들은 숫자를 기준으로 계산이 되어져야 하기 때문에 반드시 타입이 숫자 일때만 사용 가능

> Aggregate function 예시

- users 테이블의 전체 행 수 조회하기

```sql
SELECT COUNT(*) FROM users;
```

- 나이가 30살 이상인 사람들의 평균 나이 조회하기

```sql
SELECT AVG(age) FROM users WHERE age >= 30;
```

> GROUP BY 사용해보기

- 각 지역별로 몇 명씩 살고 있는지 조회하기

  - country 컬럼으로 그룹화

```sql
SELECT country FROM users GROUP BY country;
```

- 마지막으로 몇 명씩 사는지 계산하기 위해서 COUNT 사용

```sql
SELECT country, COUNT(*) FROM users GROUP BY country;

-- 각 지역별로 그룹이 나뉘어졌기 때문에 COUNT(*)는 지역별 데이터 개수를 세게 됨
```

> COUNT 참고사항

- 이전 쿼리에서 COUNT(), COUNT(age), COUNT(last_name) 등 어떤 컬럼을 넣어도 결과는 같음
- 그룹화된 country 를 기준으로 카운트 하는 것이기 때문에 어떤 컬럼을 카운트 해도 전체 개수는 똑같기 때문

> GROUP BY 실습

- 각 성씨가 몇 명씩 있는지 조회하기

```sql
SELECT last_name, COUNT(*) FROM users
GROUP BY last_name;
```

- AS 키워드를 사용해 컬럼명을 임시로 변경

```sql
SELECT last_name, COUNT(*) AS number_of_name
FROM users GROUP BY last_name;
```

- 인원이 가장 많은 성씨 순으로 조회하기

```sql
SELECT last_name, COUNT(*) FROM users
GROUP BY last_name ORDER BY COUNT(*) DESC;
```

- 각 지역별 평균 나이 조회하기

```sql
SELECT country, AVG(age) FROM users
GROUP BY country;
```

## Changing data

> 개요

- 데이터를 삽입, 수정, 삭제

  - INSERT
  - UPDATE
  - DELETE

> INSERT statement

- 새 행을 테이블에 삽입
- 문법 규칙

  1. 먼저 INSERT INTO 키워드 뒤에 데이터를 삽입할 테이블의 이름 지정
  2. 테이블 이름 뒤에 쉼표로 구분된 컬럼 목록 추가

     - 컬럼 목록은 선택 사항이지만 컬럼 목록을 포함하는 것이 권장됨

  3. VALUES 키워드 뒤에 쉼표로 구분된 값 목록 추가

     - 만약 컬럼 목록을 생략하는 경우 값 목록의 모든 컬럼에 대한 값을 지정해야 함
     - 값 목록의 값 개수는 컬럼 목록의 컬럼 개수와 같아야 함

> INSERT 사용해보기

- 단일 행 삽입하기

```sql
INSERT INTO classmates (name, age, address)
VALUES ('홍길동', 23, '서울');
```

- 이렇게도 가능

```sql
INSERT INTO classmates
VALUES ('홍길동', 23, '서울');
```

- 여러 행 삽입하기

```sql
INSERT INTO classmates
VALUES
('김철수', 30, '경기'),
('이영미', 31, '강원'),
('박진성', 26, '전라'),
('최지수', 12, '충청'),
('정요한', 28, '경상');
```

> UPDATE statement

- 테이블에 있는 기존 행의 데이터를 업데이트
- 문법 규칙

  1. UPDATE 절 이후에 업데이트 할 테이블 지정
  2. SET 절에서 테이블의 각 컬럼에 대해 새 값을 설정
  3. WHERE 절의 조건을 사용하여 업데이트 할 행 지정

     - WHERE 절은 선택 사항이며, 생략하면 UPDATE 문은 테이블의 모든 행에 있는 데이터를 업데이트 함

  4. 선택적으로 ORDER BY 및 LIMIT 절을 사용하여 업데이트 할 행 수를 지정할 수도 있음

> UPDATE 실습

- 2번 데이터의 이름을 '김철수한무두루미', 주소를 '제주도'로 수정하기

```sql
UPDATE classmates
SET name='김철수한무두루미',
    address='제주도'
WHERE rowid = 2;
```

> DELETE statement

- 테이블에서 행을 제거
- 한 행, 여러 행, 모든 행 삭제할 수 있음
- 문법 규칙

  1. DELETE FROM 키워드 뒤에 행을 제거하려는 테이블의 이름을 지정
  2. WHERE 절에 검색 조건을 추가하여 제거할 행을 식별

     - WHERE 절은 선택 사항이며, 생략하면 DELETE 문은 테이블의 모든 행을 삭제

  3. 선택적으로 ORDER BY 및 LIMIT 절을 사용하여 삭제할 행 수를 지정할 수도 있음

> DELETE 사용해보기

- 5번 데이터 삭제하기

```sql
DELETE FROM classmates WHERE rowid = 5;
```

- 삭제 확인

```sql
SELECT rowid, * FROM classmates;
```

> DELETE 실습

- 이름에 '영'이 포함되는 데이터 삭제하기

```sql
DELETE FROM classmates WHERE name LIKE '%영%';
```

- 테이블의 모든 데이터 삭제하기

```sql
DELETE FROM classmates;
```
