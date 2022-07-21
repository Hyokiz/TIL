# 0721 TIL

## 1. 표준 입출력 (input)

> 표준 입력 예제

input()은 사용자의 입력 한 줄을 문자열로 받는 함수

```python
word = input()
>>> happyhacking
```

input()과 map함수를 이용해 원하는 대로 입력 받기

```python
# 문자열 입력 받기
a = input()

# 한 개 숫자 입력 받기
b = int(input())
c = float(input())

# 여러 개 숫자 입력 받기
```

> 파이썬의 내장 함수 map(function, iterable)

- map(int, ["1", "2", "3"]) >> 정수 1, 2, 3을 반환
(각 원소에 int를 적용)

- map(int, "123") >> 리스트 뿐만 아니라 문자열에도 적용 가능. 정수 1, 2, 3을 반환

> map으로 입력 받는 과정 -1

```python
a, b = map(int,(input().split()))
a, b = map(int, "1 2".split())
a, b = map(int,["1", "2"])
a, b = 1, 2
```

> Quiz 1. 다음 코드의 결과는?

```python
a, b, c = map(int, input())
>>> 123 # 문자열에도 적용 가능. 공백이 없으므로 input

print(a + b + c)
>>> 6
```

> Quiz 2. 물음표에 들어갈 코드는?

```python
a, b, c = map(int, input().split())
>>> 1 2 3 # 공백이 있으면 split

print(a + b + c)
>>> 6
```

## 2. 표준 출력 예제 (print)

- print()는 데이터를 출력할 수 있는 함수이며, 자동적으로 줄 바꿈 발생
- 콤마(,)를 이용해 여러 인자를 넣으면 공백을 기준으로 출력
- end, sep 옵션을 사용하여 출력 조작하ㅣ

```python
a = "happy"
b = "hacking"

print(a, end="@") # print의 본질을 바꿈 #end의 값은 제일 뒤에
print(b)
>>> happy@hacking

print(a, b, sep="\n") # seperation 구분자 # sep를 지정하면 다른 문자를 기준으로 출력
>>>happy 
>>>hacking
```

> Quiz 1. 다음 코드의 결과는?

```python
a, b, c = map(int, input().split())
>>> 1 2 3

print(a, b, c)
>>> 1 2 3 
```

> Quiz 2. 다음 코드의 결과는?

```python
a, b, c = map(int, input().split())
>>> 1 2 3

print(a, b, c, end = "&")
>>> 1 2 3&

print(a, b, c, sep = "&")
>>> 1&2&3

print(a, b, c, end = "&", sep = "&")
>>> 1&2&3&
```
---
# 추가

```python
# lambda 함수 (== 익명함수, 한 줄로 간단하게 함수를 표현)
minus_two = lambda x: x - 2
result = minus_two(5)
print(result) # 3

# map과 같이 사용 가능
minus_numbers = list(map(lambda x: x - 2, [5, 6]))
prnt(minus_numbers) # [3, 4]
```

> 재귀함수

1. 재귀에 대한 이해

- 재귀(Recursion)란 함수가 자기 자신을 계속 호출하며 문제를 해결하는 것을 말한다.
  - 재귀의 깊이가 깊어질 때 마다 범위가 작아짐
  - base-case(재귀탈출조건)과 점화식으로 이루어짐
- 팩토리얼 문제를 통해 재귀 이해하기
  - 상위 문제를 해결하기 위해, 그 보다 좁은 범위의 하위 문제를 먼저 해결
```python
4! = 4 * 3 * 2 * 1
3! = 3 * 2 * 1
2! = 2 * 1
1! = 1

n! = n x (n-1)!
(n-1)! = (n-1) x (n-2)!
```
2. 반복문 vs 재귀

```python
def factorial(n):
  if n <= 1:
    return 1

  return n * factorial(n - 1) # 자기 자신 호출

print(factorial(4))
>>> 24

n = 4
result = 1

for i in range(1, n + 1)
  result *= i

print(result)
>>> 24
```

3. 재귀 함수의 구조

- 재귀 함수는 두 가지 부분으로 나누어 정리한다.
  1. 종료 조건
    - 가장 하위 문제에 도달 시 재귀를 종료할 수 있는 조건문

  2. 점화식
    - 재귀함수를 호출 하는 식
    - 좁은 범위의 하위 문제 정의

  3. 종료 조건을 작성하지 않으면
    - RecursionError : maximum recursion depth exceeded