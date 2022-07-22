# 0722 TIL

## 0721 워크샵 문제 풀이

1. 간단한 N의 약수

```python
n = int(input())

# 1. 반복문과 end 옵션
for i in range(1, n+1)
  if n % i == 0:
    print(i, end=' ') # 1 2 5 10

# 2. 리스트 컴프리헨션과 언패킹
numbers = [i for i in range(1, n + 1) if n % i == 0]
print(*numbers) # 1 2 5 10

# 3. 더간단하게

print(*[i for i in range(1, n + 1) if n % i == 0])
```

2. List의 합 구하기

```python
def list_sum(numbers):
  sum_value = 0

  for number in numbers:
    sum_value += number

    return sum_value

print(list_sum([1, 2, 3, 4, 5]))

# return을 쓰지 않고 print를 사용하면 값은 출력되나, return은 자동으로 None
```

3. Dictionary로 이루어진 List의 합 구하기

```python

def dict_list_sum(infos):
  age_sum = 0

  for info in infos:
    age_sum += info['age']

  return age_sum

# dictionary라는 집합 안의 'age'값을 뽑기 위해 ['age'] 한다.

print(dict_list_sum([{'name' : 'kim', 'age' : 12}, {'name' : 'lee', 'age' : 4}]))
```

4. 2차원 List의 전체 합 구하기

> 개념

> 이차원 리스트

- 이차원 리스트는 리스트를 원소로 가지는 리스트일 뿐이다.
- 이차원 리스트는 행렬이다.

> 이차원 리스트 순회

- 이중 for문을 이용한 행 우선 순회
- 이중 for문을 이용한 열 우선 순회

> 순회 

- 행 우선 순회를 이용해 이차원 리스트의 총합 구하기

- Pythonic한 방법으로 이차원 리스트의 총합 구하기

```python
matrix = [
  [1, 1, 1, 1],
  [1, 1, 1, 1],
  [1, 1, 1, 1]
]

total = sum(map(sum, matrix))
# map : 원소에 각각 앞의 함수를 적용하는 것

print(total)
>>> 12
```

- 행 우선 순회를 이용해 이차원 리스트의 최대값, 최소값 구하기

> 2차원 List의 전체 합 구하기

```python
def all_list_sum(num_lists):
  lists_sum = 0

  for num_list in num_lists:
    for num in num_list:
      lists_num += num

  return lists_sum

print(all_list_sum([[1], [2, 3], [4, 5, 6], [7, 8, 9, 10]]))

# Pythonic

print(sum(map(sum, [[1], [2, 3], [4, 5, 6], [7, 8, 9, 10]])))

```

5. 숫자의 의미

> 아스키 코드

- 컴퓨터는 숫자만 이해할 수 있다!
- ord : 문자 > 아스키코드로 변환하는 내장 함수
- chr : 아스키코드 > 문자로 변환하는 내장 함수

```python
def get_secret_word(numbers):
  word = ''

  for number in numbers:
    word += chr(number)

  return word

print(get_secret_word([83, 115, 65, 102, 89]))
```

6. 내 이름은 몇일까?

```python
def get_secret_number(word):
  total = 0

  for char in word:
    total += ord(char)

  return total

print(get_secret_number('happy'))
```

7. 강한 이름

```python
def get_strong_word(word1, word2):
  word1_total = 0
  word2_total = 0

  for char in word1:
    word_total += ord(char)

  for char in word2:
    word2_total += ord(char)

  if word1_total > word2_total:
    return word1
  elif word1_total < word2_total:
    return word2
  else:
    return word1, word2

print(get_strong_word('z', 'a'))
print(get_strong_word('delilah', 'dixon'))
print(get_strong_word('a', 'a'))
```
