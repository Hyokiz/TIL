# 0718 복습

## 프로그래밍 학습 마인드셋

> 개념 구조화 하기 in 프로그래밍

> > 개념 구조화

- 개념의 정의
- 개념의 포함 관계
- 두 개념의 차이점

> 기본기 탄탄하게 쌓기\
> 동료 학습

> > 동료 학습의 장점

- 현업 기반의 학습 환경
- 실제 회사에서도 함께 일하게 됨
- 커뮤니케이션 스킬 증진

## 프로그래밍이란?

> 프로그래밍의 정의

컴퓨터에게 일을 시키기 위해서 프로그램을 만드는 행위

> 프로그래밍 용어 정리

- 프로그래밍 : 컴퓨터에게 일을 시키기 위해서 프로그램을 만드는 행위
- 프로그램 : 컴퓨터가 해야할 일들의 모음
- 프로그래머 : 프로그램을 만드는사람(소프트웨어 개발자)
- 소프트웨어 : 엄밀히 따지면 다르지만, 프로그램과 유사한 의미로 사용
- 코딩 : 엄밀히 따지면 다르지만, 프로그래밍과 유사한 의미로 사용

> 프로그래밍 언어란?

기계어의 대안으로 사람이 이해할 수 있는 새로운 언어

> > 프로그래밍의 특징

- 사람이 이해할 수 있는 문자로 구성
- 기본적인 규칙과 문법이 존재

> 프로그래밍 언어의 구성

> > 소스 코드

- 프로그래밍 언어로 작성된 프로그램

> > 번역기(interpreter 혹은 compiler)

- 소스 코드를 컴퓨터가 이해할 수 있는 기계어로 번역
- 파이썬의 경우 인터프리터를 사용

## 파이썬이란?

> 파이썬을 배워야 하는 이유
>
> > 1.  알고리즘 코딩 테스트에 유리
> > 2.  구현 코딩 테스트에 유리
> > 3.  가장 인기 많은 언어

> Easy to Learn

파이썬은 다른 프로그래밍 언어보다 문법이 간결하고, 유연함.

> 인터프리터 언어(Interpreter)

파이썬은 소스 코드를 기계어로 변환할 때 통역(interprete) 하듯이 1줄씩 변환

객체 지향 프로그래밍

- 현대 프로그래밍의 기본적인 설계 방법론으로 자리잡은 객체 지향 프로그래밍
- 파이썬은 객체 지향 언어이며, 모든 것이 객체로 구현되어 있음

> 파이썬 개발 환경 종류

- IDE(Intergrated Development Environment)
- Jupyter Notebook
- IDLE(Intergrated Development and Learning Environment)

> IDE란?

- 통합 개발 환경의 약자로 개발에 필요한 다양하고 강력한 기능들을 모아둔 프로그램

> Jupyter Notebook

- 문법 학습을 위한 최적의 도구. 소스 코드와 함께 실행 결과와 마크다운 저장 가능
- 다양한 프로그래밍 언어 지원, 셀 단위 실행이 가능한 것이 특징

## 코드 작성법

> 들여쓰기

- Space Sensitive
  - 문장을 구분할 때, 중괄호 대신 들여쓰기
  - 들여쓰기를 할 때는 4칸 혹은 1탭을 입력.
  - Tab으로 들여쓰면 계속 탭으로 들여써야 함.
  - 원칙적으로는 공백(space)사용 권장

> 주석(Comment)

- 코드에 대한 설명

  - 코드를 보다 이해하기 쉽게 하여 분석 및 수정 용이해짐
  - 주석은 코드에 영향을 주지 않으며, 오로지 개발자만.

- 초기부터 들여야 할 가장 중요한 습관
  - 개발자에게 주석을 다는 습관은 매우 중요
  - 잘 달린 주석은 그 어떤 정보보다 유용함
    - 주석은 실행에 영향 X
    - 프로그램의 속도를 느리게 하지 않고, 용량을 늘리지 않음

> 한 줄 주석

- 주석으로 처리될 내용 앞에 '#'을 입력
  - 한 줄을 온전히 사용할 수도 있고, 코드 뒷부분에 작성할 수도 있음

> 여러 줄 주석

- 한 줄씩 #을 사용하거나, """ 또는 '''으로 묶어서 표현

> 주석의 장점

- 개발자에게 주석을 다는 습관은 매우 중요

  - 코드의 내용을 잘 이해할 수 있도록 작성
  - 무분별한 사용은 자제

- 코드를 쉽게 이해할 수 있어서 코드 수정 및 협업에 유리

## 기초 문법

> 변수(Variable)

- 변수란?

  - 데이터를 저장하기 위해서 사용
  - 변수를 사용하면 복잡한 값들을 쉽게 사용할 수 있음(추상화)

- 동일 변수에 다른 데이터를 언제든 할당(저장)할 수 있기 때문에, '변수'라고 불림

> 추상화(변수를 사용해야 하는 이유)

- 코드의 가독성 증가
- 숫자를 직접 적지 않고, 의미 단위로 작성 가능
- 코드 수정이 용이해짐

> 변수의 할당

- 변수는 할당 연산자(=)를 통해 값을 할당(assignment)
- 같은 값을 동시에 할당할 수 있음
- 다른 값을 동시에 할당할 수 있음

> 각 변수의 값을 바꿔서 저장하기

x = 10, y = 20일 때, 각각 값을 바꿔서 저장하는 코드를 작성하시오.

- 방법1. 임시 변수 활용
  x, y = 10, 20

tmp = x\
x = y\
y = tmp\
print(x, y) # 20, 10

- 방법2. Pythonic!

x, y = 10, 20\
y, x = x, y\
print(x, y) # 20 10

> 식별자

변수 이름 규칙

- 식별자의 이름은 영문 알파벳, 언더스코어(\_), 숫자로 구성
- 첫 글자에 숫자가 올 수 없음
- 길이 제한 없고, 대소문자 구별
- 여러 키워드는 예약어(reserved words)로 사용할 수 없음
- 내장 함수나 모듈 등의 이름도 사용하지 않아야 함.

print(5)\
print - 'hi'\
print(5) # 에러 발생 (TypeError : 'str' object is not callable) #내장 함수 print가 아닌, 문자열 hi 가 할당된 변수 print로 사용됨

## 연산자

> 산술 연산자(Arithmetic Operator)

- 기본적인 사칙연산 및 수식 계산

// : 몫
\*\* : 거듭제곱

i = 5\
j = 3\
print(i // j) # 5 / 3의 몫은 1\
print(i \*\* j) # 5의 3제곱은 125

> 연산자 우선순위

- 기본적으로 수학에서 우선순위와 같음

## 자료형

> 자료형(Datatype) 분류

- 프로그래밍에서는 다양한 종류의 값(데이터)를 쓸 수 있음
  - 사용할 수 있는 데이터의 종류들을 자료형(Datatype)이라고 함
- 수치형(Numeric Type)
  - int(정수, integer)
  - float(부동소수점, 실수, floating point number)
  - complex(복소수, complex number)
- 문자열(String Type)
- 불린형(Boolean Type)
- None

### 수치형

> 정수 자료형(int)

- 0, 100, -200과 같은 정수를 표현하는 자료형
  - 일반적인 수학 연산(사칙연산 가능)

> 진수 표현

- 여러 진수 표현 가능
  - 2진수(binary) : 0b
  - 8진수(octal) : 0o
  - 16진수(hexadecimal) : 0x

print(0b10) # 2\
print(0o30) # 24\
print(0x10) # 16

> 실수 자료형(float)

- 유리수와 무리수를 포함하는 '실수'를 다루는 자료형
  - 0.1, 100.0, -0.001 등

> 실수 연산시 주의할 점(부동 소수점)

- 실수의 값을 처리할 때 의도치 않은 값이 나올 수 있음

  - 연산의 결과가 0.1이 아니다.

- 원인은 부동 소수점 때문
  - 컴퓨터는 2진수, 사람은 10진법
  - 이때 10진수 0.1은 2진수로 표현하면 0.0001100110011... 무한
  - 무한대 숫자를 그대로 저장할 수 없어서 사람이 사용하는 10진법의 근사값만 표시
  - 0.1의 경우 3602879701896397 / 2 \*\* 55 이며 0.1에 가깝지만 정확히 동일하지 않음.
  - 이런 과정에서 예상치 못한 결과가 나타남(이런 증상을 Floating point rounding error라고 함)

> 실수 연산시 주의할 점(부동 소수점) - 해결책

- 값 비교하는 과정에서 정수가 아닌 실수면 주의할 것
  - 매우 작은 수보다 작은지를 확인하거나 math 모듈 활용

a = 3.2 - 3.1 # 0.100000000000000009\
b = 1.2 - 1.1 # 0.099999999999999987\
#1. 임의의 작은 수 활용\
print(abs(a - b) <= 1e-10) # True\

#2. python 3.5 이상\
import math\
print(math.isclose(a, b)) # True

> 문자열 자료형의 정의

- 모든 문자는 str 타입
- 문자열은 작은따옴표(')나 큰따옴표(")를 활용하여 표기
  - 문자열을 묶을 때 동일한 문장부호를 활용
  - PEP8에서는 소스코드 내에서 하나의 문장부호를 선택하여 유지하도록 함

print('hello') # hello\
print(type('hello')) # <class 'str'>\
print("hello") # hello

> 중첩 따옴표

- 따옴표 안에 따옴표를 표현할 경우
  - 작은따옴표가 들어 있는 경우는 큰따옴표로 문자열 생성
  - 큰따옴표가 들어 있는 경우는 작은따옴표로 문자열 생성

print("문자열 안에 '작은따옴표'를 사용하려면 큰따옴표로 묶는다.")\
#문자열 안에 '작은따옴표'를 사용하려면 큰따옴표로 묶는다.\
print('문자열 안에 "큰따옴표"를 사용하려면 작은 따옴표로 묶는다.')\
#문자열 안에 "큰따옴표"를 사용하려면 작은따옴표로 묶는다.

> 삼중 따옴표(Triple Quotes)

- 작은따옴표나 큰따옴표를 삼중으로 사용
  - 따옴표 안에 따옴표를 넣을 때
  - 여러 줄을 나눠 입력할 때 편리

print(''' 문자열 안에 '작은따옴표'나\
"큰따옴표"를 사용할 수 있고\
여러 줄을 사용할 때도 편리하다.''')\
\
#출력 결과
문자열 안에 '작은따옴표'나\
"큰따옴표"를 사용할 수 있고\
여러 줄을 사용할 때도 편리하다.

> Escape sequence

- 역슬래시(backslash)뒤에 특정 문자가 와서 특수한 기능을 하는 문자 조합
- 폰트에 따라 \가 다르게 표시되는 경우도 있으나 같은 의미

\n : 줄바꿈\
\t : 탭\
\r : 캐리지 리턴\
\0 : 널(Null)\
\\\ : \ \
\' : 단일인용부호(')\
\" : 이중인용부호(")

> Escape Sequence(예시)

- 띄어쓰기, 줄 바꿈과 같은 기능을 문자로 표현

print('철수 \'안녕\'') # 철수 '안녕'\
print('이 다음은 엔터. \n그리고 탭\t탭')\
\
#출력결과\
'''\
이 다음은 엔터.\
그리고 탭 탭\
'''

> 문자열 연산

- 덧셈
  - 파이썬에서 문자열 덧셈은 문자열을 연결
  - 영어로는 String Concatenation이라고 함

print("Hello"+"World") # HelloWorld

- 곱셈
  - 문자열 "Python" \* 3은?

print("Python" \* 3) # PythonPythonPython

> String Interpolation(문자열을 변수로 활용하여 만드는 법)

- %-formatting

name = 'Kim'\
score = 4.5\
\
print('Hello, %s' % name) # Hello, Kim\
print('내 성적은 %d' % score) # 내 성적은 4\
print('내 성적은 %f' % score) # 내 성적은 4.50000

- str.format()

name = 'Kim'\
score = 4.5\
\
print('Hello, {}! 성적은 {}'.format(name, score))
#Hello, Kim! 성적은 4.5

> String Interpolation(문자열을 변수를 활용하여 만든느 법)

- f-strings : python 3.6+

name = 'Kim'\
score = 4.5\
\
print(f'Hello, {name}! 성적은 {score}')\
#Hello, Kim! 성적은 4.5\
\
import datetime\
today = datetime.datetime.now()\
print(today) # 2022-07-08 16:04:15.200411\
\
print(f'오늘은 {today:%y}년 {today:%m}월 {today:%d}일')\
#오늘은 22년 07월 08일\
\
pi = 3.141592\
print(f'원주율은 {pi:.3}, 반지름이 2일 때 원의 넓이는 {pi*2 *2}')\
#원주율은 3.14, 반지름이 2일때 원의 넓이는 12.566368

> None

- 파이썬 자료형 중 하나
- 값이 없음을 표현하기 위해 None 타입이 존재
- 일반적으로 반환 값이 없는 함수에서 사용하기도 함

## 불린형

> 불린형(Boolean)이란?

- 논리 자료형으로 참과 거짓을 표현하는 자료형
- True or False
- 비교 / 논리 연산에서 활용

> 비교연산자

- 수학에서 등호와 부등호와 동일한 개념
- 주로 조건문에서 사용, 값을 비교
- 결과는 True/False값을 리턴함

!= : 같지 않음\
is : 객체 아이덴티티(OOP)\
is not : 객체 아이덴티티가 아닌 경우

> 비교 연산자 활용 예시

print(3.0 == 3) # True\
print('3' != 3) # True\
print('Hi' == 'hi') # False

> 논리 연산자

- 여러 가지 조건이 있을 때
  - 모든 조건을 만족하거나(and), 여러 조건 중 하나만 만족해도 될 때(or), 특정 코드를 실행하고 싶을 때 사용
  - 일반적으로 비교연산자와 함께 사용됨

> 논리 연산자 사용 예시

- and는 2개 다 True인 경우에 True
- or는 1개라도 True면 True

- 22시가 지나고 졸리면 True, 졸리지 않다면 False인 코드를 만들고 싶다면?

#23시가 되었고, 잠이 오는 경우\
hour = 23\
status = 'sleepy'\
print(hour >= 22 and status == 'sleepy') # True\
\
#23시가 되었지만, 잠이 안 오는 경우\
hour = 23\
status = 'nice'\
print(hour >= 22 and status == 'nice') # False

> 논리 연산자 주의할 점 / not ㅇ녀산자

- Falsy : False는 아니지만 False로 취급 되는 다양한 값

  - 0, 0.0, (), [], {}, None, ""(빈 문자열)

- 논리 연산자도 우선순위가 존재
  - not, and, or 순으로 우선순위가 높음

print(not True and False or not False) # True\
print(((not True) and False) or (not False)) # True

> 논리 연산자의 단축 평가

- 결과가 확실한 경우 두번째 값은 확인하지 않고 첫번째 값 반환
- and 연산에서 첫번째 값이 False인 경우 무조건 False > 첫번째 값 반환
- or 연산에서 첫번째 값이 True인 경우 무조건 True > 첫번째 값 반환
- 0은 False, 1은 True

print(3 and 0) # 0\
print(0 or 3) # 3\
\
a = 5 and 4\
print(a) # 4\
b = 5 or 3\
print(b) # 5\
c = 0 and 5\
print(c) # 0\
d = 5 or 0\
print(d) # 5

## 컨테이너

> 컨테이너란?

- 여러 개의 값(데이터)를 담을 수 있는 것(객체)으로, 서로 다른 자료형을 저장할 수 있음.

  - 예시 : List

- 컨테이너의 분류
  - 순서가 있는 데이터(Ordered) vs 순서가 없는 데이터(Unordered)
  - 순서가 있다 != 정렬되어 있다.

> 컨테이너의 분류

컨테이너는 시퀀스형, 비시퀀스형으로 분류되어 있다.\
시퀀스형에는 리스트, 튜플, 레인지\
비시퀀스형에는 세트, 딕셔너리가 있다.\
그 중 리스트, 세트, 딕셔너리는 가변형(mutable), 튜플 레인지는 불변형이다(immutable).

## 시퀀스형

### 리스트

> 리스트

- 리스트는 여러 개의 값을 순서가 있는 구조로 저장하고 싶을 때 사용

> 리스트의 생성과 접근

- 리스트는 대괄호([]) 혹은 list()를 통해 생성
  - 파이썬에서는 어떠한 자료형도 저장할 수 있으며, 리스트 안에 리스트도 넣을 수 있음.
  - 생성된 이후 내용 변경 가능 > 가변 자료형
  - 이러한 유연성으로 파이썬에서 흔히 사용
- 순서가 있는 시퀀스로 인덱스를 통해 접근 가능
  - 값에 대한 접근은 list[i]

#리스트명 = [요소1, 요소2, 요소3, ...]\
list_a = []\
list_b = [1, 2, 3]\
list_c = ['Life', 'is', 'too', 'short']\
list_d = [1, 2, 3, 'Python', ['리스트', '안에', '리스트']]

> 리스트의 생성과 접근 예시

my_list = []\
another_list = list()\
print(type(my_list)) # <class 'list'>\
print(type(another_list)) # <class 'list'>\
location = ['서울', '대전', '구미', '광주', '부울경']\
print(location) # ['서울', '대전', '구미', '광주', '부울경']\
print(type(location)) # <class 'list'>\
print(location[0]) # 서울

- 리스트를 담고 있는 요소를 바꿀 수 있다. > 가변 자료형(mutable)

location[0] = '양양'\
print(location) # ['양양', '대전', '구미', '광주', '부울경']

### 튜플

> 튜플의 정의

- 튜플은 여러 개의 값을 순서가 있는 구조로 저장하고 싶을 때 사용
  - 리스트와의 차이점은 생성 후, 담고 있는 값 변경 불가(불변 자료형)
- 항상 소괄호 형태로 사용

print((1, 2, 3, 1)) # (1, 2, 3, 1)\
print(tuple((1, 2, 3, 1))) # (1, 2, 3, 1)\
print(type((1, 2, 3, 1))) # <class 'tuple'>

> 튜플의 생성과 접근

- 소괄호(()) 혹은 tuple()을 통해 생성
- 튜플은 수정 불가능한(immutable) 시퀀스로 인덱스로 접근 가능
- 값에 대한 접근은 my_tuple[i]

#값 접근\
a = (1, 2, 3, 1)\
print(a[1]) # 2\
\
#값 변경 > 불가능\
a[1] = '3' # TypeError: 'tuple' object does not support item assignment

> 튜플(Tuple) 생성 주의사항

- 단일 항목의 경우
  - 하나의 항목으로 구성된 튜플은 생성 시 값 뒤에 쉼표를 붙여야 함
- 복수 항목의 경우,
  - 마지막 항목에 붙은 쉼표는 없어도 되지만, 넣는 것을 권장(Trailing comma)

tuple_a = (1,)\
print(tuple_a) # (1,)\
print(type(tuple_a)) # <class 'tuple'>\
\
tuple_b = (1, 2, 3,)\
print(tuple_b) # (1, 2, 3)\
print(type(tuple_b)) # <class 'tuple>\
둥근 괄호를 사용하여 튜플 생성하기

a = 1,\
print(a) # (1,)\
print(type(a)) # <class 'tuple'>\
\
b = 1, 2, 3\
print(b) # (1, 2, 3)\
print(type(b)) # <class 'tuple'>\
둥근 괄호 없이 튜플 생성하기

> 튜플 대입(Tuple assignment)

- 튜플 대입이란?

  - 우변의 값을 좌변의 변수에 한 번에 할당하는 과정

- 튜플은 일반적으로 파이썬 내부에서 활용
  - 추후 함수에서 복수의 값을 반환할 때에도 활용

x, y = 1, 2\
print(x, y) # 1 2\
\
#실제로 tuple로 처리\
x, y = (1, 2)\
print(x, y) # 1, 2

### Range

> Range의 정의

- 숫자의 시퀀스를 나타내기 위해 사용
- 주로 반복문과 함께 사용됨

print(range(4)) # range(0, 4)\
\
#담겨 있는 숫자를 확인하기 위하여 리스트로 형변환(실제 활용 시 형변환 필요 없음)\
print(list(range(4))) # [0, 1, 2, 3]\
\
print(type(range(4))) # <class 'range'>

> Range의 사용 방법

- 기본형 : range(n)
  - 0부터 n-1까지의 숫자의 시퀀스

print(list(range(3))) # [0, 1, 2]

- 범위 지정 : range(n, m)
  - n부터 m-1까지의 숫자의 시퀀스

print(list(range(1, 5))) # [1, 2, 3, 4]

- 범위 및 스텝 지정 : range(n, m, s)
  - n부터 m-1까지 s만큼 증가시키며 숫자의 시퀀스

print(list(range(1, 5, 2))) # [1, 3]

> Range의 사용 방법 2

#역순
print(list(range(6, 1, -1))) # [6, 5, 4, 3, 2]\
print(list(range(6, 1, -2))) # [6, 4, 2]\
print(list(range(6, 1, 1))) # []

### 슬라이싱 연산자

> 시퀀스를 특정 단위로 슬라이싱

- 인덱스와 콜론을 사용하여 문자열의 특정 부분만 잘라낼 수 있음
- 슬라이싱을 이용하여 문자열을 나타낼 때 콜론을 기준으로 앞 인덱스에 해당하는 문자는 포함되지만, 뒤 인덱스에 해당 문자는 미포함

#리스트([1:4]에서 1은 포함 4는 미포함)\
print([1, 2, 3, 5][1:4]) # [2, 3, 5]\
\
#튜플\
print((1, 2, 3)[:2]) # (1, 2)\
\
#range\
print(range(10)[5:8]) # range(5, 8)\
\
#문자열\
print('abcd'[2:4]) # cd

> 시퀀스를 k간격으로 슬라이싱

#리스트\
print([1, 2, 3, 5][0:4:2]) # [1, 3]\
\
#튜플\
print((1, 2, 3, 5)[0:4:2]) # (1, 3)\
\
#range\
print(range(10)[1:5:3]) # range(1, 5, 3)\
\
#문자열\
print('abcdefg'[1:3:2]) # b

> 문자열 슬라이싱 예제

- s = 'abcdefghi'
- s[2:5] > 'cde'
- s[2:5:2] > 'ce'
- s[5:2:-1] > 'fed'
- s[:3] > 'abc'
- s[5:] > 'fghi'
- s[::] > 'abcdefghi'
  - s[0:len(s):1]과 동일
- s[::-1] > 'ihgfedcba'
  - s[-1:-(len(s)+1):-1]과 동일

## 비시퀀스형 컨테이너

### 셋(set)

- set이란 중복되는 요소 없이, 순서 상관 없는 데이터들의 묶음

  - 데이터의 중복을 허용하지 않기 때문에 중복되는 원소가 있다면 하나만 저장
  - 순서가 없기 때문에 인덱스를 이용한 접근 불가능

- 수학에서의 집합을 표현한 컨테이너

  - 집합 연산이 가능(여집합 제외)
  - 중복된 값이 존재하지 않음

- 담고 있는 요소를 삽입 변경, 삭제 가능 > 가변 자료형(mutable)

> 셋(set) 생성

- 중괄호({}) 혹은 set()을 통해 생성

  - 빈 set을 만들기 위해서는 set()을 반드시 활용해야 함

- 순서가 없어 별도의 값에 접근할 수 없음

#set는 중복 값 제거\
print({1, 2, 3, 1, 2}) # {1, 2, 3}\
print(type({1, 2, 3})) # <class 'set'>\
\
#빈 중괄호는 Dictionary\
blank = {}\
print(type(blank)) # <class 'dict'>\
blank_set = set()\
print(type(blank_set)) # <class 'set'>\
\
#set는 순서가 없어 인덱스 접근 등 특정 값에 접근할 수 없음\
print({1, 2, 3}[0]) # TypeError: 'set' object is not subscriptable

> 셋(set) 사용하기

- 셋을 활용하면 다른 컨테이너에서 중복된 값을 쉽게 제거할 수 있음

  - 단, 이후 순서가 무시되므로 순서가 중요한 경우 사용할 수 없음

- 아래의 리스트에서 고유한 지역의 개수는?

my_list = ['서울', '서울', '대전', '광주', '서울', '대전', '부산', '부산']\
\
print(len(set(my_list))) # 4

- 아래의 리스트에서 고유한 지역을 등장한 순서대로 출력하시오.

my_list = ['서울', '서울', '대전', '광주', '서울', '대전', '부산', '부산']\
\
#set를 사용하는 순간 순서가 사라짐(실행할 때 마다 순서가 변경됨)\
print(set(my_list)) # {'광주', '서울', '부산', '대전'}

> 셋(set) 연산자

- | : 합집합
- & : 교집합
- -: 차집합(B-A, A-B)
- ^ : 대칭차집합(합집합 - 교집합)
- 여집합은 없음.

### 딕셔너리

- 키-값(key-value) 쌍으로 이뤄진 자료형(3.7부터는 ordered, 이하 버전은 unordered)
- Dictionary의 키(key)

  - key는 변경 불가능한 데이터(immutable)만 활용 가능
    - string, integer, float, boolean, tuple, range

- 각 키의 값(values)
  - 어떠한 형태든 관계 없음

> 딕셔너리(Dictionary) 생성

- 중괄호({}) 혹은 dict()을 통해 생성
- key를 통해 value에 접근

dict_a - {}\
print(type(dict_a)) # <class 'dict'>\
\
dict_b = dict()\
print(type(dict_b) # <class 'dict'>\
\
dict_a = {'a' : 'apple', 'b' : 'banana', 'list' : [1, 2, 3]}\
print(dict_a) # {'a' : 'apple', 'b' : 'banana', 'list' : [1, 2, 3]}\
print(dict_a)['list'] # [1, 2, 3]\
\
dict_b = dict(a = 'apple', b = 'banana', list = [1, 2, 3])\
print(dict_b) # {'a' : 'apple', 'b' : 'banana', 'list' : [1, 2, 3]}

## 형변환

- 파이썬에서 데이터 형태는 서로 변환할 수 있음
- 암시적 형 변환(Implicit)

  - 사용자가 의도하지 않고, 파이썬 내부적으로 자료형을 변환하는 경우

- 명시적 형 변환(Explicit)
  - 사용자가 특정 함수를 활용하여 의도적으로 자료형을 변환하는 경우

> 암시적 형 변환

- 사용자가 의도하지 않고, 파이썬 내부적으로 자료형을 변환 하는 경우
  - bool
  - Numeric type(int, float)

print(True + 3) # 4\
print(3 + 5.0) # 8.0

> 명시적 형 변환

- int
  - str, float > int
  - 단, 형식에 맞는 문자열만 정수로 변환 가능

#문자열은 암시적 타입 변환이 되지 않음\
print('3' + 4) # TypeError: can only concatenate str(not "int") to str\
\
#명시적 타입 변환이 필요함\
print(int('3') + 4) # 7\
\
#정수 형식이 아닌 경우 타입 변환할 수 없음\
print(int('3.5') + 5) # ValueError: invalid literal for int() with base 10: '3.5'

- float
  - str(참고), int > float
  - 단, 형식에 맞는 문자열만 float로 변환 가능

print('3.5' + 3.5) # TypeError : can only concatenate str (not "float) to str\
\
#정수 형식인 경우에도 float로 타입 변환\
print(float('3')) # 3.0\
\
#float 형식이 아닌 경우 타입 변환할 수 없음\
print(float('3/4) + 5.3) # ValueError: could not convert string to float : '3/4'

- str
  - int, float, list, tuple, dict > str

print(str(1)) # 1\
print(str(1.0)) # 1.0\
print(str([1, 2, 3])) # [1, 2, 3]\
print(str((1, 2, 3))) # (1, 2, 3)\
print(str({1, 2, 3})) # {1, 2, 3}
