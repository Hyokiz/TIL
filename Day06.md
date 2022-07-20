# 0720 내용

## 제어문

> 제어문

- 파이썬은 기본적으로 위에서 아래로 명령을 수행
- 특정 상황에 따라 코드를 선택적으로 실행(분기/조건)하거나 계속하여 실행(반복)하는 제어가 필요.
- 제어문은 순서도로 표현 가능

## 조건문

> 조건문

- 조건문은 참/거짓을 판단할 수 있는 조건식과 함께 사용

> 기본 형식

- 조건에는 참/거짓에 대한 조건식
  - 조건이 참인 경우 들여쓰기 되어있는 코드 블록 실행
  - 이외의 경우 else 이후 들여쓰기 되어있는 코드 블록 실행
    - else는 선택적으로 활용 가능

> 조건문 예시

```python
a = 5
if a > 5:
	print('5 초과')
else:
	print('5 이하')
print(a)

'''
5이하
5
'''

a = 6
if a > 5:
	print('5 초과')
else:
	print('5 이하')
print(a)

'''
5초과
6
'''
```

> 조건문 실습 문제

- 조건문을 통해 변수 num의 값이 홀수, 짝수 여부를 출력하시오
  - 이때 num은 input을 통해 사용자로부터 입력을 받으시오

```python
num = int(input())
if num % 2 == 1:
	print('홀수')
else:
	print('짝수')
```

## 복수 조건문

> 복수 조건문

- 복수의 조건식을 활용할 경우 elif를 활용하여 표현함

```python
if 조건:
	# Code block
elif 조건:
	# Code block
elif 조건:
	# Code block
else:
	# Code block
```

> 복수 조건문 실습 문제

- 미세먼지 농도에 따른 위험 등급이 다음과 같을 때, dust 값에 따라 등급을 출력하는 조건식을 작성하시오. ( 단, 조건식 완료 후 미세먼지 확인 완료라는 문구를 출력)

```python
dust = 80
if dust > 150:
	print('매우 나쁨')
elif dust > 80:
	print('나쁨')
elif dust > 30:
	print('보통')
else:
	print('좋음')
print('미세먼지 확인 완료!')

'''
보통
미세먼지 확인 완료!
'''
```

## 중첩 조건문

> 중첩 조건문

- 조건문은 다른 조건문에 중첩되어 사용될 수 있음
  - 들여쓰기에 유의하여 작성할 것

```python
if 조건:
	# Code block
	if 조건:
		# Code block
else:
	# Code block
```

- 아래의 코드에서 중첩 조건문을 활용하여 미세먼지 농도가 300이 넘는 경우 ‘실외 활동을 자제하세요’를 추가로 출력하고 음수인 경우 ‘값이 잘못되었습니다’를 출력하시오.

```python
dust = 500
if dust > 150:
	print('매우 나쁨')
	if dust > 300:
		print('실외 활동을 자제하세요.')
elif dust > 80:
	print('나쁨')
elif dust > 30:
	print('보통')
elif dust >= 0:
	print('좋음')
else:
	print('값이 잘못 되었습니다.')

'''
매우 나쁨
실외 활동을 자제하세요.
'''
```

> 조건 표현식

- 조건 표현식(Conditional Expression)이란?
  - 조건 표현식을 일반적으로 조건에 따라 값을 정할 때 활용
  - 삼항 연산자(Ternary Operator)로 부르기도 함

```python
true인 경우 값 if 조건 else false인 경우 값
```

조건을 기준 true 인 경우 왼쪽, false 인 경우 오른쪽

> 조건 표현식 실습 문제

- num이 정수일 때, 아래의 코드는 무엇을 위한 코드일까요?

```python
value = num if num >= 0 else - num

# 정답 : 절대값을 저장하기 위한 코드
```

- 다음의 코드와 동일한 조건 표현식을 작성하시오.

```python
num = 2
if num % 2 :
	result = '홀수입니다.'
else:
	result = '짝수입니다.'
print(result)

# 짝수입니다.

num = 2
result = '홀수입니다.' if num % 2 else '짝수입니다'
print(result)

# 짝수입니다.
```

```python
num = -5
value = num if num >= 0 else 0
print(value) # 0

num = -5
if num >= 0:
	value = num
else:
	value = 0
print(value) # 0
```

## 반복문

> 반복문

- 특정 조건을 만족할 때 까지 같은 동작을 계속 반복하고 싶을 때 사용

> 반복문의 종류

- while 문
  - 종료 조건에 해당하는 코드를 통해 반복문을 종료시켜야 함
- for 문
  - 반복 가능한 객체를 모두 순회하면 종료 (별도의 종료 조건이 필요 없음)
- 반복 제어
  - break, continue, for-else

## While문

> While문

- while문은 조건이 참인 경우 반복적으로 코드를 실행 - 조건이 참인 경우 들여쓰기 되어 있는 코드 블럭이 실행됨 - 코드 블록이 모두 실행되고, 다시 조건식을 검사하며 반복적으로 실행됨 - while 문은 무한 루프를 하지 않도록 종료 조건이 반드시 필요

> While문 예시

- 아래의 순서도를 while 반복문을 이용해서 코드로 나타내시오.

```python
a = 0
while a < 5:
	print(a)
	a += 1
print('끝')
```

> 복합 연산자(In-Place Operator)

- 복합 연산자는 연산과 할당을 합쳐 놓은 것
  - 예시) 반복문을 통해서 개수를 카운트 하는 경우

## for문

> for문

- for문은 시퀀스(string, tuple, list, range)를 포함한 순회 가능한 객체(iterable)의 요소를 모두 순회
  - 처음부터 끝까지 모두 순회하므로 별도의 종료 조건이 필요하지 않음
- Iterable

  - 순회할 수 있는 자료형(string, list, dict, tuple, range, set 등)
  - 순회형 함수(range, enumerate)

  ```python
  for 변수명 in iterable:
  	# Code block

  for fruit in ['apple', 'mango', 'banana']:
  	print(fruit)
  print('끝')

  '''
  apple
  mango
  banana
  끝
  '''
  ```

> for문을 이용한 문자열(String) 순회

- 사용자가 입력한 문자를 한 글자씩 출력하시오. (happy 입력)

```python
chars = input()

# happy

for char in chars:
				print(char)

'''
h
a
p
p
y
'''

for idx in range(len(chars)):
				print(chars[idx])

'''
h
a
p
p
y
'''
```

> 딕셔너리(Dictionary) 순회

- 딕셔너리는 기본적으로 key를 순회하며, key를 통해 값을 활용

```python
grades = {'john' : 80, 'eric' : 90}
for student in grades:
		print(student)

'''
john
eric
'''
```

> 추가 메서드를 활용한 딕셔너리(Dictionary) 순회

- 추가 메서드를 활용하여 순회할 수 있음
  - keys() : Key로 구성된 결과
  - values() : value로 구성된 결과
  - items() : (Key, value)의 튜플로 구성된 결과

```python
grades = {'john' : 80, 'eric' : 90}
print(grades.keys())
print(grades.values())
print(grades.items())

'''
dict_keys {['john', 'eric']}

```

> enumerate 순회

- enumerate()
  - 인덱스와 객체를 쌍으로 담은 열거형(enumerate) 객체 반환
    - (index, value) 형태의 tuple로 구성된 열거 객체를 반환

```python
members = ['민수', '영희', '철수']

for idx, number in enumerate(members):
```

> 파이썬 문서에서 확인하기

```python
members = ['민수', '영희', '철수']
enumerate(members) # enumerate at 0x105d3e100
print(list(enumerate(members)))
```

> List Comprehension

- 표현식과 제어문을 통해 특정한 값을 가진 리스트를 간결하게 생성하는 방법

```python
[code for 변수 in iterable]

[code for 변수 in iterable if 조건식]

# 1~3의 세제곱 리스트 만들기
cubic_list = []
for number in range(1, 4):
		cubic_list.append(number ** 3)
print(cubic_list)

# [1, 8, 27]

cubic_list = [number ** 3 for number in range(1, 4)]
print(cubic_list)

# [1, 8, 27]
```

> map 과의 차이

list comprehension은 복수의 리스트 항목을 for문과 list.append()를 사용하지 않고 한 줄의 코드로 작성하는 것입니다.

map()은 복수의 자료에 대해 map()함수의 인자로 정해진 함수에 적용시켜 새로운 값을 변환시키는데 사용합니다.

> Dictionary Comprehension 실습

- 1~3의 세제곱의 결과가 담긴 딕셔너리를 만드시오.

```python
# 1 ~ 3의 세제곱 딕셔너리 만들기

cubic_dict = {}

for number in range(1, 4):
				cubic_dict[number] = number ** 3
print(cubic_dict)

# {1: 1, 2: 8, 3: 27}

cubic_dict = {number: number ** 3 for number in range(1, 4)}
print(cubic_dict)

# {1: 1, 2: 8, 3: 27}
```

> dict 에서는 append 메서드 대신 update 메서드를 사용해서 값을 추가 할 수 있습니다.

> 반복문 제어

- break
  - 반복문을 종료
- continue
  - continue 이후의 코드 블록은 수행하지 않고, 다음 반복을 수행
- for-else
  - 끝까지 반복문을 실행한 이후에 else 문 실행
    - break를 통해 중간에 종료되는 경우 else 문은 실행되지 않음
- pass - 아무것도 하지 않음(문법ㅈ거으로 필요하지만, 할 일이 없을 때 사용)

> 반복문 제어 기본 형식

- break
  - break 를 만나면 반복문 종료
- continue
  - 해야하는 코드를 skip 하고 반복
- pass
  - 지나감.

> break

- break문을 만나면 반복문은 종료됨

```python
n = 0
while True:
		if n == 3:
				break
		print(n)
		n += 1

'''
0
1
2
'''

for i in range(10):
		if i > 1:
				print('0과 1만 필요해!')
				break
		print(i)

'''
0
1
0과 1만 필요해!
'''
```

> continue

- continue 이후의 코드 블록은 수행하지 않고, 다음 반복을 수행

```python
for i in range(6):
		if i % 2 == 0:
				continue
		print(i)

'''
1
3
5
'''
```

> pass

- 아무것도 하지 않음.

  - 특별히 할 일이 없을 때 자리를 채우는 용도로 사용
  - 반복문이 아니어도 사용 가능

  ```python
  # i가 2일때 pass
  for i in range(4):
  		if i == 2:
  				pass
  		print(i)

  '''
  0
  1
  2
  3
  '''
  ```

> else

- 끝까지 반복문을 실행한 이후에 else문 실행

  ```python
  for char in 'apple':
  		if char == 'b':
  				print('b!')
  				break
  else:
  		print('b가 없습니다.')

  # b가 없습니다.

  for char in 'banana':
  		if char == 'b':
  				print('b!')
  				break
  else:
  		print('b가 없습니다!')

  # b!
  ```

break로 중단됨 - else 구문 실행

else 문은 break로 중단되었는지 여부에 따라 실행

> 반복문 제어 정리

- break = 중지
- continue = 지나감
- pass = 통과함

## 함수

> 함수

- 함수를 왜 사용할까
  - Decomposition(분해)
  - Abstraction(추상화)

> Decomposition(분해)

```python
numbers = [1, 2, 3]
count = 0
for i in [1, 2, 3]:
		count += 1
print(count) # 3

내용추가하기
```

```python
numbers = [1, 2, 3]

def average(numbers):
		return sum(numbers) / len(numbers)

print(average(numbers)) # 2.0
```

> Abstraction

- 사실 내부 구조를 변경할게 아니라면 몰라도 무방 - 그것이 함수의 장점이자 프로그래밍의 매력 - 스마트폰의 원리를 잘 몰라도 우리는 사용할 수 있음

> 함수의 종류

- 함수는 크게 3가지로 분류 - 내장 함수 - 파이썬에 기본적으로 포함된 함수 - 외장 함수 - import 문을 통해 사용하며, 외부 라이브러리에서 제공하는 함수 - 사용자 정의 함수 - 직접 사용자가 만드는 함수

> 함수의 정의

- 함수(Function) - 특정한 기능을 하는 코드의 조각(묶음) - 특정 코드를 매번 다시 작성하지 않고, 필요시에만 호출하여 간편히 사용

> 함수 기본 구조

- 선언과 호출(define & call)
- 입력(Input)
- 문서화(Docstring)
- 범위(Scope)
- 결과값(Output)

> 선언과 호출(define & call)

- 함수의 선언은 def 키워드를 활용함
- 들여쓰기를 통해 Funcion body(실행될 코드 블록)를 작성함
  - Docstring은 함수 body 앞에 선택적으로 작성 가능
    - 작성 시에는 반드시 첫 번째 문장에 문자열 “””
- 함수는 parameter를 넘겨줄 수 있음
- 함수는 동작 후에 return을 통해 결괏값을 전달함
- 함수는 함수명()으로 호출하여 사용
  - parameter가 있는 경우, 함수명(값1, 값2, …)로 호출

```python
def foo():
		return True

# foo()

def add(x, y):
		return x + y

# add(2, 3)
```

> 함수 실행 순서 예시

```python
num1 = 0
num2 = 1

def func1(a, b):
		return a + b

def func2(a, b):
		return a - b

def func3(a, b):
		return func1(a, 5) + func2(5, b)

result = func3(num1, num2)
print(result) # 9
```

---

## 복습내용

> 프로그래밍의 두가지

- 저장과 처리 - 변수 >> 연산자 - 컨테이너 >> 제어문(if, while, for)

> if 복습

```python
if True:
		print("여기는 참입니다.")
else:
		print("여기는 거짓입니다.")

# 여기는 참입니다.

a = 1

if 0 < a < 5:
		print("a는 0에서 5사이 입니다.")
elif a < 0:
		print("a는 0보다 작다")
elif a > 5:
		print("a는 5보다 크다")
else:
		print("a는 0 혹은 5이다.")

# a는 0에서 5사이 입니다.

a = 1

if a > 0:
		value = "a는 0보다 크다."
else:
		value = "a는 0보다 작거나 같다."

value = "a는 0보다 크다." if a > 0 else "a는 0보다 작거나 같다."

# 위의 네 줄과 아래의 한 줄이 같다.

print(value)

# a는 0보다 크다.
```

> while 복습

```python
a = 0

while a < 5:
		print(a)
		a += 1
		# a = a + 1

'''
0
1
2
3
4
'''

```

> for 복습

```python
a = 0
while a < 5:
		print(a)
		a += 1

for a in range(5): # range 자리는 반복할 수 있는 자료형이어야 한다.(iterable)
		print(a)

# 위의 네 줄과 아래의 두 줄이 같다.
# while과 다르게 for은 조건이 필요 없다.

# 컨테이너에는 시퀀스, 비시퀀스.
# 시퀀스에는 list, tuple, range, string
# 비시퀀스에는 set, dict
# 컨테이너 전부가 가지고 있는 특성이 iterable이다. 따라서 다 사용가능
```

> break, continue 복습

```python
# break : 반복 중간에 탈출
# continue : 처음으로 돌아감

# break

a = 0
while a < 5:
		print(a)
		a += 1
		if a == 3:
				break

'''
0
1
2
'''

for a in range(5)
		if a == 3:
				break
		print(a)

'''
0
1
2
'''

# continue

a = 0
while a < 5:
		if a == 3:
				a += 1
				continue
		print(a)
		a += 1

for a in range(5):
		if a == 3:
				continue
		print(a)
```

- for-else 복습

  ```python
  for a in range(5):
  		print(a)
  else:
  		print("모두 다 돌았습니다.")

  # for의 반복이 정상적으로 끝나면 else가 작동

  for a in range(5):
  		print(a)
  		if a == 3:
  				break
  else:
  		print("모두 다 돌았습니다")

  # for의 반복이 정상적으로 끝나지 않으면 else가 작동하지 않음

  # 알고리즘 풀때 좋음(else문이 있을 때 편하다.)
  ```

  > enumerate 복습

  ```python
  a = [1, 2, 3, 4, 5]

  for i in a:
  		print(i)

  '''
  1
  2
  3
  4
  5
  '''

  # 순서와 값을 같이 출력하고 싶을 때

  a = [1, 2, 3, 4 ,5]

  for i in range(len(a)):
  		print(i)

  '''
  0
  1
  2
  3
  4
  '''

  # f.string사용

  a = [1, 2, 3, 4, 5]

  for i in range(len(a)):
  		print(f"현재 {i}번째 데이터는 {a[i]}")

  '''
  현재 0번째 데이터는 1
  .
  .
  .
  .
  '''

  #enumerate 사용(좀더 pythonic한 방법)

  a = [1, 2, 3, 4, 5]

  for i, v in enumerate(a):
  		print(f"현재 {i}번째 데이터는 {v}")

  '''
  위의 결과와 같음
  '''

  # append

  a = []

  for i in range(5)
  		a.append(i) # a.append(i) == i의 값을 a에 넣으세요.

  print(a)

  # 한줄로 줄이기(마법의 복사 붙여넣기)
  # list comprehension
  # 왼쪽에 값 for 범위

  a = [i for i in range(5)]

  # 홀수만 넣을 경우

  a = []

  for i in range(5):
  		if i % 2 == 1:
  				a.append(i)

  a = [i for i in range(5) if i % 2 == 1]

  print(a)

  # 0719 항구 문제의 다른 풀이

  odd_ports = []

  for i, v in enumerate(ports):
  		if (i + 1) % 2 == 1:
  				odd_ports.append(v)

  odd_ports = [v for i, v in enumerate(ports) if (i + 1) % 2 == 1]

  print(odd_ports)
  ```

> 함수 복습

- 함수
  - 저장 + 처리
- 파이썬의 경우 input : input() > output : print()
- 함수의 경우 input : 파라미터 > output : return

```python
numbers = [1, 2, 3]
count = 0

for i in numbers:
		count += 1

print(count) # 3

# len을 쓰지 않고 길이를 측정하는 방법

 def length(x):
		count = 0
		for i in x:
				count += 1
		return count

numbers = [1, 2, 3]
print(length(numbers))

# numbers = Argument(함수를 호출할 때 넣는 실제 입력값)
# x = Parameter(함수 안에서 입력으로 받는 임의의 값)

# numbers가 여러 개일 경우 def로 만든 함수를 재사용 가능
```

---

## 함수의 결과값(Output)

> 값에 따른 함수의 종류

- Void function
  - 명시적인 return 값이 없는 경우, None을 반환하고 종료
- Value returning function - 함수 실행 후, return문을 통해 값 반환 - return을 하게 되면, 값 반환 후 함수가 바로 종료 - print는 값을 출력하지만, 반환하지는 않는다.

> print vs return

- print 함수와 return의 차이점
  - print를 사용하면 호출될 때마다 값이 출력됨(주로 테스트를 위해 사용)
  - 데이터 처리를 위해서는 return 사용

```python
# Void function 예시
def void_product(x, y):
		print(f'{x} x {y} = {x * y}')

void_product(4, 5) # 4 x 5 = 20
ans = void_product(4, 5) # 4 x 5 = 20
print(ans) # None

# Value returning function 예시
def value_returning_product(x, y):
		return x * y

value_returning_product(4, 5)
ans = value_returning_product(4, 5)
print(ans) # 20
```

- REPL(Read-Eval-Print Loop) 환경에서는 마지막으로 작성된 코드의 리턴 값을 보여주므로 같은 동작을 하는 것으로 착각할 수 있음 ex) Jupyter Notebook

> 두 개 이상의 값 반환

- 아래 코드의 문제점은?

```python
def minus_and_product(x, y):
		return x - y
		return x * y

y = minus_and_product(4, 5)
print(y) # -1

# return은 항상 하나의 값 만을 반환
# 두 개 이상의 값을 반환하는 방법은?
```

> 튜플을 활용하여 두 개 이상의 값 반환

- 반환 값으로 튜플 사용

```python
def minus_and_product(x, y):
		return x - y, x * y

y = minus_and_product(4, 5)
print(y) # (-1, 20)
```

> 함수 반환 정리

- return X >> None (Void)
- return O >> 하나를 반환
- 여러 개를 원하면 Tuple 활용(혹은 리스트와 같은 컨테이너 활용)

```python
# 똑바로 읽어도 거꾸로 읽어도 같은 단어를 찾는 함수
word_list = ['우영우', '기러기', '별똥별', '파이썬']
def is_palindrom(word_list):
		palindrom_list = []
		for word in word_list:
				if word == word[::-1]:
						palindrom_list.append(word)
		return palindrom_list
print(is_palindrom(word_list))
# ['우영우', '기러기', '별똥별']
```

> Parameter와 Argument

- Parameter : 함수를 정의할 때, 함수 내부에서 사용되는 변수
- Argument : 함수를 호출할 때, 넣어주는 값

```python
def function(ham) : # parameter : ham
		return ham

function('spam') # argument : 'spam'
# 함수 리턴값 : spam

# 선언 : 파라미터 // 호출 : 아규먼트
```

> Argument

- Argument란? - 함수 호출 시 함수의 parameter를 통해 전달되는 값 - Argument는 소괄호 안에 할당 func_name(argument) - 필수 Argument : 반드시 전달되어야 하는 argument(없으면 에러) - 선택 Argument : 값을 전달하지 않아도 되는 경우는 기본값이 전달

> Positional Arguments

- 기본적으로 함수 호출 시 Argument는 위치에 따라 함수 내에 전달됨

```python
def add(x, y):
		return x + y

add(2, 3)

def add(x, y):
		x = 2, y = 3
		return x + y
```

> Keyword Arguments

- 직접 변수의 이름으로 특정 Argument를 전달할 수 있음
- Keyword Argument 다음에 Positional Argument를 활용할 수 없음

```python
def add(x, y):
		return x + y

add(x=2, y=5)
add(2, y=5)
add(x=2, 5) >> Error 발생!
```

> Default Arguments Values

- 기본값을 지정하여 함수 호출 시 argument 값을 설정하지 않도록 함
  - 정의된 것 보다 더 적은 개수의 argument 들로 호출될 수 있음

```python
def add(x, y=0):
		return x + y

add

def add (x, y=0):
		x = 2
		return x + y
```

> 정해지지 않은 여러 개의 Arguments 처리

- print 함수의 Arguments개수가 변해도 잘 동작하는 이유는? - 애스터리스크(Asterisk) 혹은 언패킹 연산자라고 불리는 \* 덕분

> 가변 인자(\*args)

- 가변인자란?
  - 여러 개의 Positional Argument를 하나의 필수 parameter로 받아서 사용
- 가변 인자는 언제 사용하는가? - 몇 개의 Positional Argument를 받을지 모르는 함수를 정의할 때 유용

> 패킹 / 언패킹

- 가변 인자를 이해하기 위해서는 패킹, 언패킹을 이해해야 함
- 패킹
  - 여러 개의 데이터를 묶어서 변수에 할당하는 것
  ```python
  numbers = (1, 2, 3, 4, 5) # 패킹
  print(numbers) # (1, 2, 3, 4, 5)
  ```
- 언패킹
  - 시퀀스 속의 요소들을 여러 개의 변수에 나누어 할당하는 것
  ```python
  numbers = (1, 2, 3, 4, 5)
  a, b, c, d, e = numbers # 언패킹
  print(a, b, c, d, e) # 1 2 3 4 5
  ```
- 언패킹시 변수의 개수와 할당하고자 하는 요소의 갯수가 동일해야 함

```python
numbers = (1, 2, 3, 4, 5) # 패킹
a, b, c, d, e, f = numbers # 언패킹
# ValueError : not enough values to unpack (expected 6, got 5)
```

- 언패킹시 왼쪽의 변수에 asterisk(\*)를 붙이면, 할당하고 남은 요소를 리스트에 담을 수 있음

```python
numbers = (1, 2, 3, 4, 5) # 패킹

a, b, *rest = numbers # 1, 2를 제외한 나머지를 rest에 대입
print(a, b, rest) # 1 2 [3, 4, 5]

a, *rest, e = numbers # 1, 5를 제외한 나머지를 rest에 대입
print(rest) # [2, 3, 4]
```

> Asterisk (\*)와 가변 인자

- \*은 스퀀스 언패킹 연산자라고도 불리며, 말 그래도 시퀀스를 풀어 헤치는 연산자 - 주로 튜플이나 리스트를 언패킹하는데 사용 - \*를 활용하여 가변 인자를 만들 수 있음

````python
  def func(\*args):
  print(args)
  print(type(args))

      func(1, 2, 3, 'a', 'b')

      '''
      (1, 2, 3, 'a', 'b')
      <class 'tuple'>
      '''
      ```
````

> 가변 인자 예시

- packing을 통해 받은 모든 숫자들의 합을 구하는 함수 만들기

```python
def sum_all(*numbers):
		result = 0
		for number in numbers:
					result += number
		return result

print(sum_all(1, 2, 3)) # 6
print(sum_all(1, 2, 3, 4, 5, 6)) # 21
```

- 반드시 받아야 하는 인자와, 추가적인 인자를 구분해서 사용할 수 있음

```python
def print_family_name(father, mother, *pets):
		print(f'아버지 : {father}')
		print(f'어머니 : {mother}')
		print('반려동물들..')
		for name in pets:
				print(f'반려동물 : {name}')

print_family_name('아부지', '어무니', '멍멍이', '냥냥이')
```

> 가변 키워드 인자(\*\*kwargs)

- 몇 개의 키워드 인자를 받을지 모르는 함수를 정의할 때 유용
- **kwargs는 딕셔너리로 묶여 처리되며, parameter에 **를 붙여 표현

```python
def family(**kwargs):
		for key, value in kwargs.items():
				print(key, ":", value)
family(father = '아부지', mother = '어무니', baby = '아기')

'''
father : 아부지
mother : 어무니
baby : 아기
'''
```

> 가변 키워드 인자(\*\*kwargs) 예시

- 반드시 받아야하는 키워드 인자와, 추가적인 키워드 인자를 구분해서 사용할 수 있ㅇ므

```python
def print_family_name(father, mother, **pets):
		print("아버지 :", father)
		print("어머니 :", mother)
		if pets:
				print("반려동물들..")
				for species, name in pets.items():
						print(f'{species} : {name}')

print_family_name('아부지', '어무이', dog = '멍멍이', cat = '냥냥이')

'''
아버지 : 아부지
어머니 : 어무이
반려동물들..
dog : 멍멍이
cat : 냥냥이
'''
```

> 가변 인자(\*args)와 가변 키워드 인자(\*\*kwargs) 동시 사용 예시

- 가변 인자와 가변 키워드 인자를 함께 사용할 수 있음

```python
def print_family_name(*parents, **pets):
			print("아버지 :", parents[0])
			print("어머니 :", parents[1])
			if pets:
					print("반려동물들..")
					for title, name in pets.items():
							print('{} : {}'.format(title, name))

print_family_name('아부지', '어무이', dog = '멍멍이', cat = '냥냥이')

'''
아버지 : 아부지
어머니 : 어무이
반려동물들..
dog : 멍멍이
cat : 냥냥이
'''
```

## Python의 범위(Scope)

> Python의 범위(Scope)

- 함수는 코드 내부에 local scope를 생성하며, 그 외의 공간인 global scope로 구분
- scope
- global scope : 코드 어디에서든 참조할 수 있는 공간
- local scope : 함수가 만든 scope. 함수 내부에서만 참조 가능
- variable - global variable : global scope에 정의된 변수 - local variable : local scope에 정의된 변수

> 변수 수명주기(lifecycle)

- 변수는 각자의 수명주기(lifecycle)가 존재 - built-in scope - 파이썬이 실행된 이후부터 영원히 유지 - global scope - 모듈이 호출된 시점 이후 혹은 인터프리터가 끝날 때까지 유지 - local scope - 함수가 호출될 때 생성되고, 함수가 종료될 때까지 유지

> 예시

```python
def func():
		a = 20
		print('local', a) # local 20

func()
print('global', a) # NameError: name 'a' is not defined
```

> 이름 검색 규칙(Name Resolution)

- 파이썬에서 사용되는 이름(식별자)등른 이름공간(namespace)에 저장되어 있음
- 아래와 같은 순서로 이름을 찾아나가며, LEGB Rule이라고 부름
- Local scope : 지역 범위(현재 작업 중인 범위)
- Enclosed scope : 지역 범위 한 단계 위 범위
- Global scope : 최상단에 위치한 범위
- Built-in scope : 모든 것을 담고 있는 범위(정의하지 않고 사용할 수 있는 모든 것)
  - ex) print()
- 함수 내에서는 바깥 Scope의 변수에 접근 가능하나 수정은 할 수 없음

> LEGB 예시1

```python
print(sum) # <bulit-in function sum>
print(sum(range(2))) # 1

sum = 5
print(sum) # 5
print(sum(range(2))) # TypeError: 'int' object is not callable
```

> LEGB 예시2

```python
a = 0
b = 1
def enclosed():
		a = 10
		c = 3
		def local(c):
				print(a, b, c) # 10 1 300
		local(300)
		print(a, b, c) # 10 1 3
enclosed()
print(a, b) # 0 1

# Scope를 살펴보면 알 수 있다.
```

> global 문

- 현재 코드 블록 전체에 적용되며, 나열된 식별자(이름)이 global variable임을 나타냄 - global에 나열된 이름은 같은 코드 블록에서 global 앞에 등장할 수 없음 - global에 나열된 이름은 parameter, for 루프 대상, 클래스/함수 정의 등으로 정의되지 않아야 함.

> global 예시

```python
# 함수 내부에서 글로벌 변수 변경하기
a = 10
def func1():
		global a
		a = 3

print(a) # 10
func1()
print(a) # 3
```

> global 관련 에러

```python
# global 주의 사항
a = 10
def func1():
		print(a) # global a 선언 전에 사용
		global a
		a = 3

print(3)
func1()
print(a)

# SyntaxError: name 'a' is used prior to global declaration

# global 주의 사항
a = 10
def func1(a):
		global a # parameter에 global 사용 불가
		a = 3

print(a)
func1(3)
print(a)

# SyntaxError: name 'a' is parameter and global
```

> nonlocal

- global을 제외하고 가장 가까운(둘러싸고 있는) scope의 변수를 연결하도록 함
- nonlocal에 나열된 이름은 같은 코드 블록에서 nonlocal 앞에 등장할 수 없음
- nonlocal에 나열된 이름은 parameter, for 루프 대상, 클래스/함수 정의 등으로 정의되지 않아야 함
- global과는 달리 이미 존재하는 이름과의 연결만 가능함

> nonlocal 예시

```python
# nonlocal 예시
x = 0
def func1():
		x = 1
		def func2():
				nonlocal x
				x = 2
		func2()
		print(x) # 2

func1()
print(x) # 0

# enclosed scope(func1)의 변수 x의 변경
```

> nonlocal, global 비교

```python
# 선언된 적 없는 변수의 활용
def func1():
		global out
		out = 3

func1()
print(out) # 3

def func1():
		def func2():
				nonlocal y
				y = 2
		func2()
		print(y)

func1()

# SyntaxError: no binding for nonlocal 'y' found
```

- nonlocal은 이름공간상에 존재하는 변수만 가능

> 함수의 범위 주의

- 기본적으로 함수에서 선언된 변수는 Local scope에 생성되며, 함수 종료 시 사라짐
- 해당 scope에 변수가 없는 경우 LEGB rule에 의해 이름을 검색함
- 변수에 접근은 가능하나, 수정 불가
- 단, 함수 내에서 필요한 상위 scope 변수는 argument로 넘겨서 활용할 것
- 상위 scope에 있는 변수를 수정하고 싶다면 global, nonlocal 키워드를 활용 가능
- 단, 코드가 복잡해지면서 변수의 변경을 추적하기 어렵고, 예기치 못한 오류 발생
- 가급적 사용하지 않는 것을 권장, 함수로 값을 바꾸고자 한다면 항상 argument로 넘기고 리턴 값을 사용하는 것을 추천

## 함수 응용

> 내장 함수(Built-in Functions)

- 파이썬 인터프리터에는 항상 사용할 수 있는 많은 함수와 형(type)이 내장되어 있음

> map

- 순회 가능한 데이터구조(iterable)의 모든 요소에 함수(function)적용하고, 그 결과를 map object로 반환

```python
numbers = [1, 2, 3]
result = map(str, numbers)
print(result, type(result)) # <map object at __> <class 'map'>
print(list(result)) # ['1', '2', '3']
```

> map 활용 사례

- 알고리즘 문제 풀이시 input 값들을 숫자로 바로 활용하고 싶을 때

```python
n, m = map(int, input().split()) # 3, 5를 입력하면
print(n, m) # 3, 5
print(type(n), type(m)) # <class 'int'> <class 'int'>
```

> filter

- 순회 가능한 데이터구조(iterable)의 모든 요소에 함수(function)적용하고, 그 결과가 True인 것들을 filter object로 반환

```python
def odd(n):
		return n % 2
numbers = [1, 2, 3]
result = filter(odd, numbers)
print(result, type(result)) # <filter object at __> <class 'filter'>
print(list(result)) # [1, 3]
```

> zip

- 복수의 iterable을 모아 튜플을 원소로 하는 zip object를 반환

```python
girls = ['Jane', 'Ashley']
boys = ['Justin', 'Eric']
pair = zip(girls, boys)
print(pair, type(pair)) # <zip obect at _> <class 'zip'>
print(list(pair)) # [('jane', 'justin'), ('Ashley', 'Eric')]

# list 형변환을 통해 결과 직접 확인
# 세로로 묶는다
```

> lambda 함수

```python
# 삼각형의 넓이를 구하는 공식 - def
def triangle_area(b, h):
		return 0.5 * b * h
print(triangle_area(5, 6)) # 15.0

# 삼각형의 넓이를 구하는 공식 - 람다
triangle_area = lambda b, h : 0.5 * b * h
print(triangle_area(5, 6)) # 15.0
```

> 재귀 함수(recursive function)

- 자기 자신을 호출하는 함수
- 무한한 호출을 목표로 하는 것이 아니며, 알고리즘 설계 및 구현에서 유용하게 활용
- 알고리즘 중 재귀 함수로 로직을 표현하기 쉬운 경우가 있음(예 - 점화식)
- 변수의 사용이 줄어들며, 코드의 가독성이 높아짐
- 1개 이상의 base case(종료되는 상황)가 존재하고, 수렴하도록 작성

> 예시

- factorial : n!

```python
4! = 4 * 3! = 4 * 3 * 2! = 4 * 3 * 2 * 1 # f(4) = 4 * f(3)
.
.
1! = 1 # f(1) = 1

# 재귀 함수

# 팩토리얼을 코드로 구현해본다면?

def factorial(n):
		if n == 0 or n == 1:
				return 1
		else:
				return n * factorial(n-1)
print(factorial(4)) # 24
```

> 재귀 함수 주의 사항

- 재귀 함수는 base case에 도달할 때까지 함수를 호출함
- 메모리 스택이 넘치게 되면 (stack overflow) 프로그램이 동작하지 않게 됨
- 파이썬에서는 최대 재귀 깊이(maximum recursion depth)가 1,000번으로, 호출 횟수가 이를 넘어가게 되면 Recursion Error 발생
  > 재귀 함수를 반복문으로 표현
- 팩토리얼 코드를 반복문으로 작성한다면?

```python
def fact(n):
		result = 1
		while n > 1:
				result =
```

> 반복문과 재귀 함수 비교

- 알고리즘 자체가 재귀적인 표현이 자연스러운 경우 재귀함수를 사용함.
  ex) 바이러스가 주변으로 퍼지는 문제 등
- 재귀 호출은 변수 사용을 줄여줄 수 있음
- 재귀 호출은 입력 값이 커질 수록 연산 속도가 오래 걸림

## 모듈과 패키지

> 모듈과 패키지

- 합, 평균, 표준편차, …
- 자주 쓰는 기능들
- 다양한 기능을 하나의 파일로(모듈, module)
- 다양한 파일을 하나의 폴더로(패키지, package)
- 다양한 패키지를 하나의 묶음으로(라이브러리, library)
- 이것을 관리하는 관리자(pip)
- 패키지의 활용 공간(가상환경)

> 모듈과 패키지

- 모듈
- 특정 기능을 하는 코드를 파이썬 파일(.py)단위로 작성한 것
- 패키지 - 특정 기능과 관련된 여러 모듈의 집합 - 패키지 안에는 또 다른 서브 패키지를 포함

> 모듈과 패키지 불러오기

- import module
- from module import var, function, Class
- from module import \*

- from package import module
- from package.module import var, function, Class

## 파이썬 표준 라이브러리

> 파이썬에 기본적으로 설치된 모듈과 내장 함수

- 파이썬에 기본적으로 설치 되어 있음 - 예시 - random.py

> 파이썬 패키지 관리자(pip)

- PyPl

> 파이썬 패키지 관리자(pip) 명령어

- 패키지 설치
- 최신 버전 / 특정 버전 / 최소 버전을 명시하여 설치할 수 있음
- 패키지 삭제
- 패키지 목록 및 특정 패키지 정보
- 패키지 관리하기
- 다양한 파이썬 프로젝트에서 사용됨

## 사용자 모듈과 패키지

> 패키지

- 패키지는 여러 모듈 / 하위

> 패키지 만들기

- 계산 기능이 들어간 calculator 패키지를 아래와 같이 구성
  - check.py에서 calculator의 tools.py의 기능을 사용

## 가상환경

> 가상환경

- 파이썬 표준 라이브러리가 아닌 외부 패키지와 모듈을 사용하는 경우 모두 pip를 통해 설치를 해야함
- 복수의 프로젝트를 하는 경우 버전이 상이할 수 있음
  - 과거 외주 프로젝트 - django 버전 2.x
  - 신규 회사 프로젝트 - django 버전 3.x
- 이러한 경우 가상환경을 만들어 프로젝트 별로 독립적인 패키지를 관리할 수 있음
- 가상 환경을 만들고 관리하는데 사용되는 모듈(Python 버전 3.5부터)
- 특정 디렉토리에 가상환경을 만들고, 고유한 파이썬 패키지 집합을 가질 수 있음
  - 특정 폴더에 가상 환경이(패키지 집합 폴더 등) 있고
  - 실행환경(예 - bash)에서 가상환경을 활성화 시켜
  - 해당 폴더에 있는 패키지를 관리/사용함

> 가상환경 생성

- 가상환경을 생성하면, 해당 디렉토리에 별도의 파이썬 패키지가 설치됨
- $ python -m venv <폴더명>

> 가상환경 활성화/비활성화

- 여러 명령어를 통해 가상환경 활성화
  - <venv>는 가상환경을 포함하는 디렉토리의 경로
- 가상환경 비활성화는 $ deactivate 명령어를 사용
- cmd와 bash 환경
- $ source venv/Scripts/activate

> 가상환경 예시

- 동일 컴퓨터에서 별도의 가상환경
