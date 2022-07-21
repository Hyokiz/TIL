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

