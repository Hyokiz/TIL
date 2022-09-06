# 20220906 TIL

## Django Form

> 개요

- 지금까지 태그를 통해서 사용자로부터 데이터를 받았음.
- 요청을 모두 수용하고 있으나, 비정상적이거나 악의적인 요청이 있다는 것을 생각해야 함.
- 유효성 검증이 반드시 필요.
- Django Form은 이 과정에서 과중한 작업과 반복 코드를 줄여줌으로써 쉽게 유효성 검증을 할 수 있게 해줌.

> Form에 대한 Django의 역할

- Form은 유효성 검사 도구 중 하나로 중요한 방어 수단이다.
- Django는 유효성 검사를 단순화하고 자동화 할 수 있는 기능 제공

> Django는 Form에 관련된 작업의 세 부분을 처리

1. 렌더링을 위한 데이터 준비 및 재구성
2. 데이터에 대한 HTML forms 생성
3. 클라이언트로부터 받은 데이터 수신 및 처리

## Django Form Class

> Form Class 선언

- Model Class를 선언하는 것과 비슷. 비슷한 이름의 필드 타입을 많이 가지고 있음
- Model과 마찬가지로 상속을 통해 선언
- Model field와 다르게 TextField가 없음.

- form.as_p 로 간단하게 표현 가능

> From rendering options

1. as_p()

   - 각 필드가 단락(p태그)로 감싸져서 렌더링

> Django의 2가지 HTML input 요소 표현

1. Form fields

   - 입력에 대한 유효성 검사 로직을 처리
   - 템플릿에서 직접 사용됨

2. Widgets

   - 웹 페이지의 HTML input 요소 렌더링을 담당
     - input 요소의 단순한 출력 부분 담당
   - Widgets은 반드시 form fields에 할당

## Widgets

> 개요

- Django의 HTML input element의 표현을 담당
- 단순히 HTML 렌더링을 처리. 유효성 검증과는 관계 없음.

> Textarea 위젯 적용하기

- widget=forms.Textarea 적용

## Django ModelForm

> 개요

- Form Class 를 작성하면서

  - ModelForm이랑 중복

- 이미 Article Model Class에 필드에 대한 정보를 작성했는데 이를 Form에 맵핑하기 위해 Form Class에 필드를 재정의 해야만 했음

- ModelForm을 사용하면 이러한 Form을 더 쉽게 작성할 수 있음

> ModelForm Class

- Model을 통해 Form Class를 만들 수 있는 helper class
- ModelForm 은 Form과 똑같은 방식으로 View 함수에서 사용

> ModelForm 선언

- forms 라이브러리에서 파생된 ModelForm 클래스를 상속받음
- 정의한 ModelForm 클래스 안에 Meta 클래스를 선언
- 어떤 모델을 기반으로 form을 작성할 것인지에 대한 정보를 Meta 클래스에 지정

> ModelForm에서의 Meta Class

- ModelForm의 정보를 작성하는 곳
- ModelForm을 사용할 경우 참조 할 모델이 있어야 하는데, Meta class 의 model 속성이 이를 구성

  - 참조하는 모델에 정의된 field 정보를 Form 에 적용

- fields 속성에 '\_\_all\_\_'를 사용하여 모델의 모든 필드를 포함할 수 있음
- 또는 exclude 속성을 사용하여 모델에서 포함하지 않을 필드를 지정할 수 있음

> Meta data

- 데이터를 표현하기 위한 데이터
- ex. 사진 파일
  - 사진 데이터
  - 사진 데이터의 데이터(시각, 렌즈, 조리개 값 등)
  - 사진 데이터에 대한 데이터(== 사진의 Meta data)

> 참조 값과 반환 값

- ex.

```py
def greeting():
    return '안녕하세요'

print(greeting) # <function greeting at -->
print(greeting()) # 안녕하세요
```

- 첫번째 결과는 참조 값
- 두번째 결과는 반환 값

- 언제 참조 값을 사용할까?

  - 함수를 호출하지 않고 함수 자체를 전달하여, 다른 함수에서 필요한 시점에 호출하는 경우
  - view 함수의 참조값을 그대로 넘김으로써, path 함수가 내부적으로 해당 view함수를 필요한 시점에 사용하기 위해서

- 클래스도 마찬가지이다.
- Article이라는 함수를 "호출하지 않고(==model을 인스턴스로 만들지 않고)" 작성하는 이유는 ArticleForm이 해당 클래스를 필요한 시점에 사용하기 위함
- 더불어 이 경우에는 인스턴스가 필요한 것이 아닌, 실제 Article 모델의 참조 값을 통해 해당 클래스의 필드나 속성 등을 내부적으로 참조하기 위한 이유도 있음

> 주의사항

- Meta 클래스는 왜 여기에 작성할까?

  - 이것은 지금 시점에 중요한 것이 아님
  - 파이썬의 문법적인 개념으로 접근하지 말자.

- 단순히 모델 정보를 Meta라는 이름의 내부 클래스로 작성하도록 ModelForm의 설계가 이렇게 되어있을 뿐 우리는 ModelForm의 역할과 사용법을 숙지해야 함.

## ModelForm with view functions

> 개요

- ModelForm 으로 인한 view 함수의 구조 변화 알아보기

> CREATE

- 유효성 검사를 통과하면

  - 데이터 저장 후
  - 상세 페이지로 리다이렉트

- 통과하지 못하면
  - 작성 페이지로 리다이렉트

> is_valid() method

- 유효성 검사를 실행하고, 데이터가 유효한지 여부를 boolean 으로 반환
- 개발자의 편의를 도움

> The save() method

- form 인스턴스에 바인딩된 데이터를 통해 데이터베이스 객체를 만들고 저장
- ModelForm의 하위 클래스는 키워드 인자 instance 여부를 통해 생성할 지 수정할 지 결정
  - 제공되지 않은 경우 지정된 모델의 새 인스턴스를 만듦(CREATE)
  - 제공되면 해당 인스턴스 수정(UPDATE)

> form 인스턴스의 errors 속성

- is_valid()의 반환값이 False인 경우 form 인스턴스의 errors 속성에 값이 작성되는데, 유효성 검증을 실패한 원인이 딕셔너리 형태로 저장됨.

> UPDATE

- ModelForm의 인자 instance는 수정 대상이 되는 객체(기존 객체)를 지정

1. request.POST
   - 사용자가 form 을 통해 전송한 데이터
2. instance
   - 수정이 되는 대상

> Form 과 ModelForm

- ModelForm이 Form 보다 더 좋은 것이 아니라 각자 역할이 다른 것.

- Form

  - 사용자로부터 받는 데이터가 DB와 연관되어 있지 않은 경우 사용
  - DB에 영향을 미치지 않고 단순 데이터만 사용되는 경우
  - ex. 로그인(인증 과정에서만 사용, 별도로 DB저장 X)

- ModelForm
  - 사용자로부터 받는 데이터가 DB와 연관되어 있는 경우에 사용
  - 데이터의 유효성 검사가 끝나면 데이터를 각각 어떤 레코드에 맵핑해야 할지 이미 알고있기 때문에 곧바로 save() 호출이 가능

---

## Widgets 활용하기

- 위젯은 대단한 역할이 아닌, input 태그의 표현에 관련된 것만 컨트롤함.

## Handling HTTP requests

> 개요

- "HTTPS requests 처리에 따른 view 함수 구조 변화"
- new-create, edit-update의 view 함수 역할을 잘 살펴보면 하나의 공통점과 차이점이 있음
- 공통점

  - new-create는 모두 CREATE 로직을 구현하기 위한 공통 목적
  - edit-update는 모두 UPDATE 로직을 구현하기 위한 공통 목적

- 차이점

  - new와 edit는 GET 요청에 대한 처리만을 >> 페이지 렌더링
  - create와 update는 POST 요청에 대한 처리만을 진행 >> DB 조작

- 이 공통점과 차이점을 기반으로 하나의 view 함수에서 method 에 따라 로직이 분리되도록 변경

## View decorators

> 개요

- View decoratoss를 사용해 view 함수를 단단하게 만들기

> 데코레이터

- 기존에 작성된 함수에 기능을 추가하고 싶을 때, 해당 함수를 수정하지 않고 기능을 추가해주는 함수
- Django 는 다양한 HTTP 기능을 지원하기 위해 view 함수에 적용할 수 있는 여러 데코레이터를 제공

## Allowed HTTP methods

> 개요

- Django.views.decorators.http 의 데코레이터를 사용하여 요청 메서드를 기반으로 접근을 제한할 수 있음
- 일치하지 않는 메서드 요청이라면 405 Method Not Allowed를 반환
- 메서드 목록
  1. require_http_methods()
  2. require_POST()
  3. require_safe()

> 405 method not allowed

- 요청 방법이 서버에게 전달되었으나 사용 불가능한 상태

> require_http_methods()

- View 함수가 특정한 요청 method만 허용하도록 하는 데코레이터

> require_POST()

- View 함수가 POST 요청 method만 허용하도록 하는 데코레이터

> require_safe()

- require_GET 이 있지만 Django에서는 require_safe를 사용하는 것을 권장

## 마무리

> 마무리

- Django Form Class

  - Django 프로젝트의 주요 유효성 검사 도구
  - 공격 및 데이터 손상에 대한 중요한 방어 수단
  - 유효성 검사에 대해 개발자에게 강력한 편의를 제공

- View 함수 구조 변화
  - HTTP requests 처리에 따른 구조 변화
