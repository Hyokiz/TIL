# 20221005 TIL

> RDB 복습

- RDB의 모든 테이블에는 행에서 고유하게 식별 가능한 기본 키라는 속성이 있으며, 외래 키를 사용하여 서로 다른 테이블 간의 관계를 만드는 데 사용할 수 있음

> 관계(Relationship)

- 여러 테이블 간의 논리적인 연결

> 테이블 간 관계 예시

- 고객 테이블(이름, 주소지, 배송지)와 주문 테이블(제품명, 주문일, 배송일, 주문상태)이 존재
- 고객 테이블에는 고객에 관한 데이터가, 주문 테이블에는 주문에 관한 거래 정보 포함
- 배송지 주소를 가지고 있는 고객 테이블의 정보를 포함해야 한다.
- 각 주문 데이터에 고객 정보 입력
- 같은 이름일 때는 어떻게 할까?
- 고객 정보의 기본 키인 고객 id 정보 저장
- 이처럼 관계형 데이터베이스에서 한 테이블의 필드 중 다른 테이블의 행을 식별할 수 있는 키를 외래 키(foreign key, FK)라고 한다.

> RDB에서의 관계

1. 1:1 관계

- 한 테이블의 레코드 하나가 다른 테이블의 레코드 단 한개와 관련된 경우

2. N:1 관계

- 한 테이블의 0개 이상의 레코드가 다른 테이블의 레코드 한 개와 관련된 경우
- ex. 주문 테이블의 0개 이상의 레코드가 고객 테이블의 레코드 한 개와 관련된 경우.

3. M:N 관계

- 한 테이블의 0개 이상의 레코드가 다른 테이블의 0개 이상의 레코드와 관련된 경우
- 양 쪽 모두에서 N:1 관계

> Many to one relationships 예시

- 여러 개의 주문 입장에서 고객 테이블의 PK를 주문 테이블에 FK로 집어 넣어 관계를 표현
- 고객(1)은 여러 주문(N)을 진행할 수 있음

## Forien Key

> 개념

- 외래 키(외부 키)
- 관계형 데이터베이스(RDB)에서 한 테이블의 필드 중 다른 테이블의 행을 식별할 수 있는 키
- 참조되는 측 테이블의 기본 키(Primary Key)를 가리킴
- 참조하는 테이블의 행 1개의 값은 참조되는 측 테이블의 행 값에 대응됨

  - 이 때문에 참조하는 테이블의 행에는 참조되는 테이블에 나타나지 않는 값을 포함할 수 없음

- 참조하는 테이블 행 여러 개가 참조되는 테이블의 동일한 행을 참조할 수 있음

> 특징

- 키를 사용하여 부모 테이블의 유일한 값을 참조(by 참조 무결성)
- 외래 키의 값이 반드시 부모 테이블의 기본 키 일 필요는 없지만 유일한 값이어야 함

> 참조 무결성

- 데이터베이스 관계 모델에서 관련된 2개의 테이블 간의 일관성을 말함
- 참조하는 테이블의 외래 키 속성의 값은 그 테이블의 부모가 되는 테이블의 기본 키 값으로 존재해야 함

# N:1 (Comment Article)

> 개요

- Comment(N) - Article(1)

  - Comment 모델과 Article 모델 간 관계 설정

- 0개 이상의 댓글은 1개의 게시글에 작성될 수 있음

## 모델 관계 설정

> 모델 관계 설정

- 게시판의 게시글과 N:1 관계를 나타낼 수 있는 댓글 구현
- N:1 관계에서 댓글을 담당할 Comment 모델은 N, Article 모델은 1이 될 것

- Comment : 내용, 생성일, 수정일, FK

## Django Relationship fields

> 종류

1. OneToOneField()

   - 1:1 관계

2. ForeignKey()

   - N:1 관계

3. ManyToManyField()

   - M:N 관계

> ForeignKey(to, on_delete, \*\*options)

- N:1 관계를 담당하는 Django의 필드 클래스
- 외래 키 속성을 담당
- 2개의 필수 위치 인자 필요

  1. 참조하는 model class
  2. on_delete 옵션

## Comment Model

> Comment 모델 정의

- 외래 키 필드는 ForeignKey 클래스를 작성하는 위치와 관계없이 필드의 마지막에 작성됨
- ForeignKey() 클래스의 인스턴스 이름은 참조하는 모델 클래스 이름의 단수형(소문자)으로 작성하는 것을 권장(이유는 이어지는 모델 참조에서 확인 예정)

> ForeignKey arguments - on_delete

- 외래 키가 참조하는 객체가 사라졌을 때, 어떻게 처리할 지 정의
- 데이터 무결성을 위해서 중요함
- on_delete 옵션 값

  - CASCADE : 부모 객체가 삭제 돼을 때 이를 참조하는 객체도 삭제
  - PROTECT, SET_NULL, SET_DEFAULT 등 여러 옵션 존재
  - 수업에서는 CASCADE만

> 데이터 무결성(Data Integrity)

- 데이터의 정확성과 일관성을 유지하고 보증하는 것
- 데이터베이스나 RDBMS의 중요한 기능
- 무결성 제한의 유형

  1. 개체 무결성(Entity integrity)
  2. 참조 무결성(Referential integrity)
  3. 범위 무결성(Domain integrity)

> Migration 과정 진행

- migrate 후 Comment 모델 클래스로 인해 생성된 테이블 확인
- ForeignKey 모델 필드로 인해 작성된 컬럼의 이름이 article_id인 것을 확인
- 만약 Foreign 인스턴스를 article이 아닌 abcd로 생성했다면 abcd_id로 만들어짐

  - 이처럼 명시적인 모델 관계 파악을 위해 참조하는 클래스 이름의 소문자(단소형)로 작성하는 것이 권장 되었던 이유

## 관계 모델 참조

> Related manager

- Related manager는 N:1 혹은 M:N 관계에서 사용 가능한 문맥(context)
- Django는 모델 간 N:1 혹은 M:N관계가 설정되면 역참조 할때에 사용할 수 있는 manager를 생성

  - 우리가 이전에 모델 생성 시 objects라는 매니저를 통해 queryset api를 사용했던 것처럼 related manager를 통해 queryset api를 사용할 수 있게 됨

- 지금은 N:1 관계에서의 related manager만을 학습할 것

> 역참조

- 나를 참조하는 테이블(나를 외래 키로 지정한)을 참조하는 것
- 즉, 본인을 외래 키로 참조 중인 다른 테이블에 접근하는 것
- N:1 관계에서는 1이 N을 참조하는 상황

  - 외래 키를 가지지 않은 1이 외래 키를 가진 N을 참조

> article.comment_set.method()

- \_set은 바뀌지 않음
- Article 모델이 Comment 모델을 참조(역참조)할 때 사용하는 매니저
- article.comment 형식으로는 댓글 객체를 참조할 수 없음

  - 실제로 Article 크래스에는 Comment와의 어떠한 관계도 작성되어 있지 않음

- 대신 Django가 역참조 할 수 있는 comment_set manager를 자동으로 생성해 article.comment_set 형태로 댓글 객체를 참조할 수 있음

  - N:1 관계에서 생성되는 Related manager의 이름은 참조하는 "모델명\_set" 이름 규칙으로 만들어짐

- 반면 참조 상황(Comment > Article)에서는 실제 ForeignKey 클래스로 작성한 인스턴스가 Comment 클래스의 클래스 변수이기 때문에 comment.article 형태로 작성 가능

> ForeignKey arguments - related_name

- ForeignKey 클래스의 선택 옵션
- 역참조 시 사용하는 매니저 이름(model_set manager)을 변경할 수 있음
- 작성 후, migration 과정이 필요
- 선택 옵션이지만, 반드시 작성해야 하는 경우 있음.
- 작성 후 다시 원래 코드로 복구

  - 위와 같이 변경하면 기본 article.comment_set은 더 이상 사용 불가, article.comments로 대체됨

> admin site 등록

- 새로 작성한 Comment 모델을 admin site에 등록하기

## Comment 구현

- 폼 : 저장되는 데이터가 아니라 데이터가 저장 외 다른 목적으로 사용될 때
- 모델폼 : 데이터를 받아서 저장이 되어야 할 때
- 사용자로부터 받는 데이터가 그대로 모델 필드에 맞춰서 저장되는거라면, 폼을 새로 만들 필요 없이 모델을 기반으로 만들어주는 폼 > 모델 폼
- 모델의 필드, 조건들을 고려해서 만든 폼 > 모델 폼
- 둘은 역할이 다르다

> CREATE

1. 사용자로부터 댓글 데이터를 입력받기 위한 CommentForm 작성
2. detail 페이지에서 CommentForm 출력(view 함수)

   - 기존에 ArticleForm 클래스의 인스턴스 명을 form 으로 작성했기 때문에 헷갈리지 않도록 comment_form으로 작성

3. detail 페이지에서 CommentForm 출력(템플릿)
4. 사용자의 입력으로 받는 것이 아니라 view 함수 내에서 받아 별도로 처리되어 저장되어야 함.

   - 실 서비스에서는 댓글을 작성할 때 자연스럽게 그 게시글에 댓글이 작성되어야 하기 때문

5. 외래 키 필드를 출력에서 제외 후 확인

6. 그럼 출력에서 제외된 외래 키 데이터는 어디에서 받아와야 할까?

   - detail 페이지의 url을 살펴보면 path('<\int:pk>/', views.detail, name='detail') url에 해당 게시글의 pk값이 사용되고 있음
   - 댓글의 외래 키 데이터에 필요한 정보가 바로 게시글의 pk 값
   - url을 통해 변수를 넘기는 variable routing 사용

7. article 객체를 저장하지 않아서 오류

   - 작성을 마치면 article 객체 저장이 이루어질 타이밍이 보이지 않음
   - 그래서 save() 메서드는 데이터베이스에 저장하기 전에 객체에 대한 추가적인 작업을 진행할 수 있도록 인스턴스만을 반환해주는 옵션 값 제공

> The save() method

- save(commit=False)

  - 아직 데이터베이스에 저장되지 않은 인스턴스를 반환
  - 저장하기 전에 객체에 대한 사용자 지정 처리를 수행할 때 유용하게 사용

> READ

1. 작성한 댓글 목록 출력하기

   - 특정 article 에 있는 모든 댓글을 가져온 후 context 에 추가

2. detail 템플릿에서 댓글 목록 출력하기

3. detail 템플릿에서 댓글 목록 출력 확인하기

> Delete

1. 댓글 삭제 구현하기 (url, view)

2. 댓글을 삭제할 수 있는 버튼을 각각의 댓글 옆에 출력될 수 있도록 함

3. 댓글 삭제 버튼 출력 확인 및 삭제 시도해보기

> 댓글 수정을 지금 구현하지 않는 이유

- 댓글 수정도 게시글 수정과 마찬가지로 구현 가능

  - 언젠간 필요하게 됨

- 하지만 일반적으로 댓글 수정은 수정 페이지로 이동 없이 현재 페이지가 유지된 상태로 댓글 작성 Form 부분만 변경되어 수정할 수 있도록 함

- 이처럼 페이지의 일부 내용만 업데이트 하는 것은 JavaScript의 영역이기 때문에 JavaScript를 학습한 후 별도로 진행

## Comment 추가 사항

> 개요

1. 댓글 개수 출력하기
2. 댓글이 없는 경우 대체 컨텐츠 출력하기

> 댓글 개수 출력하기

1. DTL filter - length 사용
2. Queryset API - count() 사용

3. detail 템플릿에 작성하기
4. 작성 후 출력 확인

> 댓글이 없는 경우 대체 컨텐츠 출력하기

1. DTL for, empty, endfor 활용하기

2. 새로운 게시글 작성이나 모든 댓글 삭제 후 확인

## Referencing the User model

> Django에서 User 모델을 참조하는 방법

1. settings.AUTH_USER_MODEL

   - 반환값 : 'accounts.User' (문자열)
   - User 모델에 대한 외래 키 또는 M:N 관계를 정의할 때 사용
   - models.py의 모델 필드에서 User 모델을 참조할 때 사용

2. get_user_model()

   - 반환값 : User Object(객체)
   - 현재 활성화(active)된 User 모델을 반환
   - 커스터마이징한 User 모델이 있을 경우는 Custom User 모델, 그렇지 않으면 User를 반환
   - models.py가 아닌 다른 모든 곳에서 유저 모델을 참조할 때 사용

> Django에서 User 모델을 참조하는 방법 정리

- User 모델을 참조할 때

  - models.py 에서는 settings.AUTH_USER_MODEL
  - 다른 모든 곳에서는 get_user_model()

## 모델 관계 설정

> Article과 User 간 모델 관계설정

- Article 모델에 User 모델을 참조하는 외래 키 작성

> Migration 진행

1. 기존에 존재하던 테이블에 새로운 컬럼이 추가되어야 하는 상황이기 때문에 makemigrations 진행

2. 첫 번째 화면

   - 기본적으로 모든 컬럼은 NOT NULL 제약 조건이 있기 때문에 데이터 없이는 새로 추가되는 외래 키 필드 user_id가 생성되지 않음
   - 기본값을 어떻게 작성할 지 선택
   - 1을 입력하고 Enter

3. 두 번째 화면

   - article 의 user_id 에 어떤 데이터를 넣을 것인지 직접 입력
   - 1 입력 후 Enter
   - 그러면 기존에 작성된 게시글이 있다면 모두 1번 회원이 작성된 것으로 처리

4. article 테이블 스키마 변경 및 확인

## CREATE

> 개요

- 인증된 회원의 게시글 작성 구현하기
- 작성하기 전 로그인 된 상태로 진행

> ArticleForm

1. ArticleForm 출력을 확인해보면 create 템플릿에서 불필요한 필드(user)가 출력

   - 이전에 CommentForm에서 외래 키 필드 article과 동일한 상황
   - user필드도 마찬가지로 url의 variable routing을 통해 처리

2. ArticleForm 의 출력 필드 수정

3. 수정 확인 후 게시글 작성

> 외래 키 데이터 누락

1. 게시글 작성 시 NOT NULL constraint failed: articles_article.user_id 에러 발생

- NOT NULL 제약 조건이 실패. articles_article 테이블의 user_id 컬럼에서
- 게시글 작성 시 외래 키에 저장되어야 할 작성자 정보가 누락

2. 게시글 작성 시 작성자 정보가 함께 저장될 수 있도록 save 의 commit 옵션 활용

3. 수정 후 게시글이 잘 작성되는지 확인

## DELETE

> 게시글 삭제 시 작성자 확인

- 이제 개시글에는 작성자 정보가 함께 들어있기 때문에 현재 삭제를 요청하려는 사람과 게시글을 작성한 사람을 비교하여 본인의 게시글만 삭제할 수 있도록 함

## UPDATE

> 게시글 수정 시 작성자 확인

1. 수정도 마찬가지로 본인의 게시글만 수정할 수 있도록 함

2. 추가로 해당 게시글의 작성자가 아니라면, 수정/삭제 버튼을 출력하지 않도록 함

3. 다른 계정으로 접속하여 게시글 확인

## READ

> 게시글 작성자 출력

1. index 템플릿과 detail 템플릿에서 각 게시글의 작성자 출력

2. 출력 확인

# N:1 (Comment - User)

> 개요

- Comment(N) - User(1)

  - Comment 모델과 User 모델 간 관계 설정

- 0개 이상의 댓글은 1개의 회원에 의해 작성될 수 있음

## 모델 관계 설정

> Comment 와 User 간 모델 관계 설정

- Comment 모델에 User 모델을 참조하는 외래 키 작성

> migration 진행

1. 기존에 존재하던 테이블에 컬럼을 추가해야 하므로 makemigrations

2. 기본적으로 컬럼은 NOT NULL이므로 데이터 없이는 외래 키 필드 user_id가 생성되지 않음

   - 그래서 기본값을 어떻게 작성할 것인지 선택해야 함
   - 1 입력 후 Enter

3. comment의 user_id에 어떤 데이터를 넣을 것인지 입력

   - 마찬가지로 1 입력 후 Enter
   - 그러면 기존에 작성된 댓글이 있다면 모두 1번 회원이 작성한 것으로 처리됨

4. Comment 테이블 스키마 변경 및 확인

## CREATE

> 개요

- 인증된 회원의 댓글 작성 구현하기
- 작성하기 전 로그인을 진행

> CommentForm

1. create 템플릿에서 불필요한 필드(user)가 출력됨

   - 마찬가지로 url의 variable routing을 통해 처리

2. CommentForm의 출력 필드 수정

3. 수정 확인 후 댓글 작성

> 외래 키 데이터 누락

1. 게시글 작성 시 NOT NULL constraint failed: articles_comment.user_id 에러 발생

   - NOT NULL 제약 조건 실패. articles_comment 테이블의 user_id 컬럼에서
   - 댓글 작성 시 외래 키에 저장되어야 할 작성자 정보 누락

2. 댓글 작성 시 작성자 정보가 함께 저장될 수 있도록 save의 commit 옵션 활용

3. 수정 후 댓글이 잘 작성 되는지 확인

## READ

> 댓글 작성자 출력

1. detail 템플릿에서 각 게시글의 작성자 출력

2. 출력 확인

## DELETE

> 댓글 작성 시 작성자 확인

1. 현재 삭제를 요청하는 사람과 댓글을 작성한 사람을 비교하여 본인의 댓글만 삭제할 수 있도록 함

2. 추가로 해당 댓글 작성자가 아니라면, 삭제 버튼을 출력하지 않도록 함

3. 다른 계정으로 접속하여 detail 템플릿에서 다른 회원이 작성한 댓글 확인

# 인증된 사용자에 대한 접근 제한하기

> 개요

- is_authenticated 와 View decorator를 활용하여 코드 정리하기

> 인증된 사용자인 경우만 댓글 작성 및 삭제하기

- views.py에서 입력

> 비인증 사용자는 CommentForm을 볼 수 없도록 하기

- detail.html에 작성

# 마무리

> 마무리 INDEX

- A many to one relationship

  - Foreign Key
  - Django Relationship fields
  - Related manager

- N:1 모델 관계 설정

  1. Comment - Article
  2. Article - User

     - Referencing the User model

  3. Comment - User
