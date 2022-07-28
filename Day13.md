# 20220728 TIL

## 객체지향 프로그래밍 복습

### 개념

- 기술 == 문제해결
- 문제해결을 위한 프로그래밍 == 객체지향 프로그래밍
- 절차지향 프로그래밍 == 호출 순서에 따라 진행이 된다.
- 프로그래밍은 저장과 처리로 나뉜다.
- 저장과 처리를 한번에 >> 함수
- 프로그램은 확장성이 고려되어야 한다. >> Style Guide
- 절차지향 프로그래밍의 단점 : 확장성이 떨어진다.
- 객체지향 프로그래밍 : 구조에 초점을 맞춤. 구조를 기준으로 프로그램이 실행된다.
- 클래스는 단지 도구일 뿐
- 객체의 세 가지 특징 : 역할, 책임, 협력
- 현실세계로 예를 들면
- 내 역할 : 교육생, 책임 : 교육받기, 협력 : 교수님과 협력하여 교육을 받음.
- 객체지향 프로그래밍은 객체끼리 요청과 응답을 통해 이루어짐

### 객체지향 프로그래밍의 구성 요소

- 추상화
- 상속
- 다형성
- 캡슐화
- 위 4가지가 사실 하나이다.

> 추상화

- 추상화 : 정확한 원리는 몰라도 사용은 가능함. ex 핸드폰, 컴퓨터를 사용해도 작동 원리는 모른다.
- 추상화 : 객체끼리 서로 소통할 때 역할과 책임에 맞는 주제를 협력할 때 원리는 상관 없이 요청만 하고 응답만 받으면 된다.

> 캡슐화

- 캡슐화 : 객체는 다른 객체의 내부에 간섭할 수 없다. 객체에게 자율성을 부여하기 때문
- 접근제어자 : public, protected, private
- getter : 

> 다형성

- 다른 객체이더라도 요청했을 시 동일한 응답이 오면 괜찮다.

> 상속

- 상위 개념에 하위 개념에 상속되어있다.

---

### OOP

> 클래스와 객체

- 개별 객체를 하나의 타입으로 보는 것 == 추상화

> 기본 문법

- 클래스 정의, 인스턴스 생성, 메서드 호출, 속성

> 속성

- 타입/클래스의 객체들이 가지게 될 상태/데이터

> 클래스변수

- 클래스변수
  - 한 클래스의 모든 인스턴스가 공유하는 값

> 인스턴스와 클래스 간의 이름 공간


```python
class Person:
  counts = 0

  def __init__(self, name):
    self.name = name

p1 = Person("k")
p1.name
p1.counts
```
### 인스턴스메서드

- 변수를 함수 안에서 찾고 없으면 함수 밖에서 변수를 가지고 온다.

> 메서드

- 특정 데이터 타입/클래스의 객체에 공통적으로 적용 가능한 행위(함수)

> 생성자 메서드

- 인스턴스 객체가 생성될 때 자동으로 호출되는 메서드

> 매직 메서드

```python
class Person:
  def __init__(self, name):
    self.name = name

  def __str__(self): # 매직메서드
    return self.name # 매직메서드가 없을 시 Person object at id값이 나온다.

person1 = Person("sth")
print(person1) # sth

class Person:
  def __init__(self, name):
    self.name = name

  def __str__(self): # 매직메서드
    return self.name

  def __add__(self, other):
    return self.name + other.name

person1 = Person("sth")
person2 = Person("sone")
print(person1 + person2) # sthsone
```

> 소멸자

```python
class Person:
  counts = 0

  def __init__(self, name, age):
    self.name = name
    self.age = age

  def __str__(self): # 매직메서드
    return self.name + " " + str(self.age)

  def __del__(self):
    print("삭제되었습니다.")

person1 = Person("sth", 25)
person2 = person1
del person1
print(person2.name) 
# sth
# 삭제되었습니다.
# del == 변수가 객체를 가르키는 참조값을 없애는 것.
# 왜 삭제되었습니다가 두번째에 나오나?
# person1의 참조값만 삭제한 것이기 때문에 person2의 값이 나오고 프로그램이 끝났기 때문에 "삭제되었습니다"가 출력된다.
```

### 클래스 메서드

- @classmethod 데코레이터를 사용하여 정의
- 호출 시, 첫번째 인자로 클래스(cls)가 전달됨
- 인스턴스 메서드는 클래스 변수 조회만 가능.

### 스태틱 메서드

- 유틸리티 함수
- 속성을 다루지 않고 단지 기능(행동)만을 하는 메서드를 사용할 때 사용
- 클래스 변수나 인스턴스 변수(self)를 사용하지 않을 때 @staticmethod 사용
- 고정된 값을 여러 번 출력할 때 사용

```python
class Person():
  counts = 0

  def __init__(self, name, age):
    self.name = name
    self.age = age

  def call_name(self):
    return f'대전 2반 {self.name} 입니다!'

  @staticmethod
  def hello():
    return '안녕하세요!'

person1 = Person("sth", 25)
print(person.call_name())
print(person1.hello())
```