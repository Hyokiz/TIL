# 20220725

## 월말평가 리뷰

- 재귀함수(recursion)
  1.  종료 조건 (base-case)
  2.  점화식

```python
def dec_to_bin(n):
    # 1. 종료 조건
    if n < 2:
        return str(n)
    # 2. 점화식
    else:
        return dec_to_bin(n // 2) + str(n % 2)

print(dec_to_bin(23))
```

- 아스키코드

  - A = 65, z = 90 인 경우
    - -65를 해서 0~25로 만들고 26일 경우에 나누기 26해서 0으로 돌아가게 만든다.

- 이차원 리스트
  - 변량 델타이동

```python
a = [
    [0, 0, 0],
    [0, 1, 0],
    [0, 0, 0]
]

now = [1, 1]

# 상하좌우
dx = [-1, 1, 0, 0]
dy = [0, 0, -1, 1]

# 상
now[0] += dx[0]
now[1] += dy[0]

# 하
now[0] += dx[1]
now[1] += dy[1]

# 좌
now[0] += dx[2]
now[1] += dy[2]

# 우
now[0] += dx[3]
now[1] += dy[3]

# for문

for i in range(4):
    now[0] += dx[i]
    now[1] += dy[i]

#한칸이동
n = 3 # 행렬의 크기
m = 0 # 상하좌우 중 어디로 갈지에 대한 인덱스
now[0] += dx[m]
now[1] += dy[m]0

if now[0] < 0 or now[0] >= n or now[1] < 0 or now[1] >= n:
    print("범위 벗어남")
else:
    print("정상범위")
```

---

# 오후 강의

## 데이터구조

> 데이터 구조 활용

- 데이터 구조를 활용하기 위해서는 메서드(method)를 활용
  - 메서드는 크래스 내부에 정의한 함수, 사실상 함수 동일
  - 쉽게 설명하자면 객체의 기능(추후 객체 지향 프로그래밍에서 학습)
  - 데이터구조.메서드()형태로 활용
  - 어렵게 느껴진다면 주어.동사()

> 데이터 구조 활용 예시

- 메서드(method)
- List.append(10)
- String.split()

> 파이썬 공식 문서의 표기법

- python 구문이 아니며, 문법을 표현하기 위한 것임
- 아래 예시에서 str.replace(old, new[,count])
  - old, new는 필수 / [,count]는 선택적 인자를 의미함

## 문자열

> 문자열(String Type)

```python
word = 'ssafy'
print(id(word)) # 메모리 주소 확인
word = 'test'
print(id(word)) # 메모리 주소 확인
```

- 문자들의 나열(sequence of characters)
  - 모든 문자는 str 타입(변경 불가능한 immutable)
- 문자열은 작은 따옴표나 큰 따옴표를 활용하여 표기
  - 문자열을 묶을 때 동일한 문장부호를 활용
  - PEP8에서는 소스코드를 묶어서

> 문자열 조회/탐색 및 검증 메서드

- s.find(x) : x의 첫 번째 위치를 반환. 없으면, -1을 반환
- s.index(x) : x의 첫 번째 위치를 반환. 없으면 오류 발생
- s.isalpha() : 알파벳 문자 여부(단순 알파벳이 아닌 유니코드 상 Letter)(한국어도 포함)
- s.isupper() : 대문자 여부
- s.islower() : 소문자 여부
- s.istitle() : 타이틀 형식 여부

> 문자열 조회/탐색

- .find(x)
- x의 첫 번째 위치를 반환. 없으면, -1을 반환함.(오류가 나지 않음)

```python
print('apple'.find('p')) # 1
print('apple'.find('k')) # -1
```

- .index(x)
- x의 첫번째 위치를 반환. 없으면 오류

```

```

> 문자열 관련 검증 메서드 사용 예시

```python
print('abc'.isalpha()) # True
print('ㄱㄴㄷ'.isalpha()) # True
print('Ab'.isupper()) # False
print('ab'.islower()) # True
print('Title Title!'.istitle()) # True
```

> 문자열 검증 메서드

- isdecimal() < .isdigit() < .isnumeric()
  - 숫자, 수, 숫자로 볼 수 있는 것 같은 개념?

> 문자열 변경 메서드(S는 문자열)

- s.replace(old, new[, count]) : 바꿀 대상 글자를 새로운 글자로 바꿔서 반환
- s.strip([chars]) >> 구분자 : 공백이나 특정 문자를 제거
- s.split(sep=None, maxsplit= -1) : 공백이나 특정 문자를 기준으로 분리
- 'separator'.join([iterable]) : 구분자로 iterable을 합침
- s.capitalize() : 가장 첫 번째 글자를 대문자로 변경
- s.title() : 문자열 내 띄어쓰기 기준으로 각 단어의 첫글자는 대문자로, 나머지는 소문자로 변환
- s.upper() : 모두 대문자로 변경
- s.lower() : 모두 소문자로 변경
- s.swapcase() : 대문자와 소문자를 서로 변경

> 문자열은 immutable(불변형)인데, 문자열 변경이 되는 이유?

- 기존의 문자열을 변경하는게 아니라, 변경된 문자열을 새롭게 만들어서 반환
  - ex) replace, strip, title 등

```python
word = 'python'
print(word) # python
print(id(word)) # 2006262763184
print(word.upper()) # PYTHON
print(id(word.upper)) # 2006262763120
```

> 문자열 변경

- .replace(old, new[, count])
  - 바꿀 대상 글자를 새로운 글자로 바꿔서 반환
  - count를 지정하면 해당 개수만큼만 시행

```python
print('coone'.replace('o', 'a')) # caane

print('woooowoo'.replace('o', '!', 2)) # w!!ooowoo
```

- .strip([chars])
  - 특정한 문자들을 지정하면
    - 양쪽을 제거하거나(strip), 왼쪽을 제거하거나(lstrip), 오른쪽을 제거(rstrip)
- 문자열을 지정하지 않으면 공백을 제거함

```python
print('    와우!\n'.strip()) # '와우!'
print('    와우!\n'.lstrip()) # '와우!'
print('    와우!\n'.rstrip()) # '   와우!'
print('안녕하세요????'.rstrip('?')) # '안녕하세요'
```

- .split
  - 문자열을 특정한 단위로 나눠 리스트로 변환
    - sep이 None이거나 지정되지 않으면 연속된 공백문자를 단일한 공백문자로 간주하고, 선행/후행 공백은 빈 문자열에 포함시키지 않음
    - maxsplit이 -1인 경우에는 제한이 없음.

```python
print('a,b,c'.split('_')) # ['a,b,c']

print('a b c'.split()) # ['a', 'b', 'c']
```

- 'seperator'.join([iterable])
  - 반복가능한(iterable) 컨테이너 요소들을 separator(구분자)로 합쳐 문자열 반환
    - iterable에 문자열이 아닌 값이 있으면 TypeError 발생

```python
print('!'.join('ssafy')) # 's!s!a!f!y'

print(' '.join(['3', '5'])) # '3 5'
```

> 문자열 변경 예시

```python
msg = 'hI! Everyone, I\'m ssafy'

print(msg) # hI! Everyone, I'm ssafy
print(msg.capitalize()) # Hi! everyone, i'm ssafy
print(msg.title()) # Hi! Everyone, I'M Ssafy
print(msg.upper()) # HI! EVERYONE, I'M SSAFY
print(msg.lower()) # hi! everyone, i'm ssafy
print(msg.swapcase()) # Hi! eVERYONE, i'M SSAFY
```

---

## 리스트

> 리스트의 생성과 접근

- 리스트는 대괄호 혹은 list()를 통해 생성

> 리스트 메서드

- L.append(x) : 리스트 마지막에 항목 x를 추가
- L.insert(i, x) : 리스트 인덱스 i에 항목 x를 삽입
- L.remove(x) : 리스트 가장 왼쪽에 있는 항목(첫 번째) x를 제거. 항목이 없으면 ValueError
- L.pop() : 리스트의 가장 오른쪽에 있는 항목을 반환 후 제거
- L.extend(m) : 순회형 m의 모든 항목들의 리스트 끝에 추가(+=와 같은 기능)
- L.index(x, start, end) : 리스트에 있는 항목 중 가장 왼쪽에 있는 항목 x의 인덱스를 반환
- L.reverse() : 리스트를 거꾸로 정렬
- L.sort() : 리스트를 정렬(매개변수 이용가능)
- L.count(x) : 리스트에서 항목 x가 몇 개 존재하는지 갯수를 반환

> 값 추가 및 삭제

- .append(x)
  - 리스트에 값을 추가함 > 마지막에

```python
cafe = ['starbucks', 'tomntoms', 'hollys']
print(cafe) # ['starbucks', 'tomntoms', 'hollys']
cafe.append('banapresso')
print(cafe) # ['starbucks', 'tomntoms', 'hollys', 'banapresso']
```

- .insert(i, x)
  - 정해진 위치 i에 x값을 추가함

```python
cafe = ['starbucks', 'tomntoms', 'hollys']
print(cafe)
cafe.insert(0, 'start')
print(cafe)
# ['start', 'starbucks', 'tomntoms', 'hollys']
cafe.insert(10000, 'end')
print(cafe) # ['starbucks', 'tomntoms', 'hollys', 'end'] << 리스트 길이보다 큰 경우 맨뒤
```

- .extend(iterable)

  - 리스트에 iterable의 항목을 추가함
  - list값으로 추가 가능
  - 문자열로 추가 시 한 글자씩만 추가됨.

- .remove(x)

  - 리스트에서 값이 x인 것 삭제

- .pop(i)
  - 정해진 위치 i에 있는 값을 삭제하고, 그 항목을 반환함
  - i가 지정되지 않으면, 마지막 항목을 삭제하고 반환함

```python
numbers = ['hi', 1, 2, 3]
numbers.pop()
print(numbers) # ['hi', 1, 2]
numbers.pop(0)
print(numbers) # [1, 2, 3]
```

- .clear()
  - 모든 항목을 삭제함

> 탐색 및 정렬

- .count(x)
  - 원하는 값의 개수를 반환함

```python
numbers = [1, 2, 3, 1, 1]

print(numbers.count(1)) # 3
print(numbers.couint(100)) # 0
```

- .sort()
  - 원본 리스트를 정렬함. None 반환
  - sorted 함수와 비교할 것

```python
numbers = [3, 2, 5, 1]
result = numbers.sort()
print(numbers, result) # [1, 2, 3, 5] None << 원본 변경

result = sorted(numbers)
print(numbers, result) # [3, 2, 5, 1] [1, 2, 3, 5] << 정렬된 리스트를 반환. 원본 변경 없음
```

- .reverse()
  - 순서를 반대로 뒤집음(정렬 X)

```python
numbers = [3, 2, 5, 1]
result = numbers.reverse()
print(numbers, result) # [1, 5, 2, 3] None
```

---

## 튜플

> 튜플의 정의

- 여러 개의 값을 순서가 있는 구조로 젖아하고 싶을 때 사용
  - 리스트와의 차이점은 생성 후, 담고 있는 값 변경 불가(불변 자료형)
- 항상 소괄호 형태로 사용

```python
print((1, 2, 3, 1)) # (1, 2, 3, 1)

print(tuple((1, 2, 3, 1))) # (1, 2, 3, 1)

print(type((1, 2, 3, 1))) # <class 'tuple'>

a = (1, 2, 3, 1)
a[0] = 5 # Error
```

> 튜플 관련 메서드

- 튜플은 변경할 수 없기 때문에 값에 영향을 미치지 않는 메서드만을 지원
- 리스트 메서드 중 항목을 변경하는 메서드들을 제외하고 대부분 동일

```python
day_name = ('월', '화', '수', '목', '금')

# 인덱스로 접근
print(day_name[-2]) #  목

# 반복결합 연산자
print(day_name * 2)
# ('월', '화', '수', '목', '금', '월', '화', '수', '목', '금')

# 확장연산자 : 값을 병합해서 재할당 (같은 자료형)
# 그러나 extend는 값을 변경하기 때문에 지원하지 않음
day_name += False, True
print(day_name)
# ('월', '화', '수', '목', '금', False, True)
```

---

## 연산자

> 멤버십 연산자

- 포함 여부 확인
  - in
  - not in

> 시퀀스형 연산자

- 반복연산자
  - 시퀀스를 반복

---

## 셋

> 셋

- set이란 중복 요소가 없이, 순서에 상관없는 데이터들의 묶음
  - 중복 원소 있으면 하나만 저장
  - 순서가 없기 때문에 인덱스 접근 X

> 셋 메서드(s는 셋)

- s.copy() : 셋의 얕은 복사본을 반환
- s.add(x) : 항목 x가 셋 s에 없다면 추가
- s.pop() : 셋 s에서 랜덤하게 항목을 반환하고, 해당 항목을 제거. set이 비어 있을 경우 KeyError
- s.remove(s) : 항목 x를 셋s에서 삭제. 항목이 존재하지 않을 경우, KeyError
- s.discard(x) : 항목 x가 셋 s에 있는 경우, 항목 x를 셋 s에서 ㅅ ㅏㄱ제
- s.update(t) : 셋 t에 있는 모든 항목 중 셋 s에 없는 항목을 추가
- s.clear() : 모든 항목을 제거
- s.isdisjoint(t) : 셋 s가 셋 t의 서로 같은 항목을 하나라도 갖고 있지 않은 경우, True반환(서로소)
- s.issubset(t) : 셋 s가 셋 t의 하위 셋인 경우, True반환
- s.issuperset(t) : 셋 s가 셋 t의 상위 셋인 경우, True반환

> 추가 및 변경

- .add(elem)
  - 셋에 값을 추가

```python
a = {'사과', '바나나', '수박'}
a.add('딸기')
print(a) # {'사과', '딸기', '바나나', '수박'}
```

- .update(\*others)
  - 여러 값을 추가

```python
a = {'사과', '바나나', '수박'}
a.update(['딸기', '바나나', '참외'])
print(a) # {'참외', '바나나', '딸기', '수박', '사과'}
```

- .remove(elem)
  - set에서 삭제하고, 없으면 KeyError

```python
a = {'사과', '바나나', '수박'}
a.remove('사과')
print(a) # {'바나나', '수박'}
a.remove('애플')
print(a) # KeyError: '애플'
```

- .discard(elem)
  - 셋에서 삭제하고 없어도 에러가 발생하지 않음

```python
a = {'사과', '바나나', '수박'}
a.discard('사과')
print(a) # {'바나나', '수박'}
a.discard('애플')
print(a) # {'바나나', '수박'}
```

- .pop()
  - 임의의 원소를 제거해 반환

```python
a = {'사과', '바나나', '수박'}
a.pop()
print(a) # {'사과', '수박'}
```

> 삭제

- .clear
  - 모두 삭제

> 집합 관련 함수

- s.isdisjoint(t)
  - 셋 s가 셋 t의 서로 같은 항목을 하나라도 갖고 있지 않은 경우, True반환(서로소)
- s.issubset(t)
  - 셋 s가 셋 t의 하위 셋인 경우, True 반환
- s.issuperset(t)
  - 셋 s가 셋 t의 상위 셋인 경우, True 반환

```python
a = {'사과', '바나나', '수박'}
b = {'포도', '망고'}
c = {'사과', '포도', '망고', '수박', '바나나'}

print(a.isdisjoint(b)) # True A와 B는 서로소인가?
print(b.issubset(c)) # True # b가 C의 하위셋인가?
print(a.issuperset(c)) # False A가 C의 상위셋인가?
```

---

## 딕셔너리

> 딕셔너리 메서드(d는 딕셔너리)

- d.clear() : 모든 항목 제거
- d.copy() : 딕셔너리 d의 얕은 복사본을 반환
- d.keys() : 딕셔너리 d의 모든 키를 담은 뷰를 반환
- d.values() : 딕셔너리 d의 모든 값을 담은 뷰를 반환
- d.items() : 딕셔너리 d의 모든 키-값의 쌍을 담은 뷰를 반환
- d.get(k) : 키 k의 값을 반환하는데, 키 k가 딕셔너리 d에 없을 경우 None을 반환
- d.get(k, v) : 키 k의 값을 반환하는데, 키 k가 딕셔너리 d에 없을 경우 v를 반환
- d.pop(k) : 키 k의 값을 반환하고 키 k인 항목을 딕셔너리 d에서 삭제하는데, 키 k가 딕셔너리 d에 없을 경우 KeyError 발생
- d.pop(k, v) : 키 k의 값을 반환하고 키 k인 항목을 딕셔너리 d에서 삭제하는데, 키 k가 딕셔너리 d에 없을 경우 v를 반환
- d.update([other]) : 딕셔너리 d의 값을 매핑하여 업데이트

> 조회

- .get(key[, default])
  - key를 통해 value를 가져옴
  - KeyError가 발생하지 않으며, default 값을 설정할 수 있음(기본 : None)

> 추가 및 삭제

- .pop(key[, default])
  - key가 딕셔너리에 있으면 제거하고 해당 값을 반환
  - 그렇지 않으면 default를 반환
  - default 값이 없으면 KeyError

```python
my_dict = {'apple' : '사과', 'banana' : '바나나'}
data = my_dict.pop('apple')
print(data, my_dict) # 사과 {'banana' : '바나나'}
```

- .update()
  - 값을 제공하는 key, value로 덮어씁니다.

```python
my_dict = {'apple' : '사', 'banana' : '바나나'}
my_dict.update(apple = '사과')
print(my_dict) # {'apple' : '사과', 'banana' : '바나나'}
```

---

## 얕은 복사와 깊은 복사

> 복사 방법

- 할당
- 얕은 복사
- 깊은 복사

> 할당(assignment)

- 대입 연산자 (=)
  - 리스트 복사 확인하기

```python
original_list = [1, 2, 3]
copy_list = original_list
print(original_list, copy_list) # [1, 2, 3] [1, 2, 3]

copy_list[0] = 'hello'
print(original_list, copy_list) # ['hello', 2, 3] ['hello', 2, 3]
```

> 얕은 복사(shallow copy)

- Slice 연산자를 활용하여 같은 원소를 가진 리스트지만 연산된 결과를 복사(다른 주소)

```python
a = [1, 2, 3]
b = a[:]
print(a, b) # [1, 2, 3] [1, 2, 3]
b[0] = 5
print(a, b) # [1, 2, 3] [5, 2, 3]
```

> 얕은 복사 주의사항

- 복사하는 리스트의 원소가 주소를 참조하는 경우

```python
a = [1, 2, ['a', 'b']]
b = a[:]
print(a, b) # [1, 2, ['a', 'b']] [1, 2, ['a', 'b']]
b[2][0] = 0
print(a, b) # [1, 2, [0, 'b']] [1, 2, [0, 'b']]
```

> 깊은 복사

- 리스트 복사 확인하기

```python
import copy
a = [1, 2, ['a', 'b']]
b = copy.deepcopy(a)
print(a, b) # [1, 2, ['a', 'b']] [1, 2, ['a', 'b']]
b[2][0] = 0
print(a, b) # [1, 2, ['a', 'b']] [1, 2, [0, 'b']]
```
