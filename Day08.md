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
---

# 프로젝트 관련

> 딕셔너리 get 메서드

```python
a = {'key' : 'value'}

a ['key']
a.get('key')
# 둘이 같다
a.get('name', ???)
# ??? 은 key값(name)이 존재 하지 않을 경우 기본값으로 ???를 가져온다.
```

> 데이터 추출 및 생성 예시

```python
def make_dict(data):
    new_data = {
        '원제': data.get('original_title'),
        '개봉년도': data.get('release_date')[:4],
        '평점': data.get('vote_average'),
    }
    return new_data


movie = {
    'genre_ids': [18, 80],
    'id': 278,
    'original_title': 'The Shawshank Redemption',
    'release_date': '1995-01-28',
    'title': '쇼생크 탈출',
    'vote_average': 8.7,
}

print(make_dict(movie))
```

> open 및 json 모듈 사용예시

```python
import json
from pprint import pprint

movie = open('sample.json', encoding='utf-8')  # 상대경로
# 파일 이름은 문자열로 받는다. utf-8 : 인코딩 방식 중 하나
# './sample.json의 ./가 생략되어있는 것으로, 현재 폴더에서 연다.
# json = 요청과 응답 할 때 주고 받는 데이터

movie_detail = json.load(movie)  # json -> dict
# json 은 dictionary와 비슷한 것이지만, dictionary가 아니다.
# 따라서 json형식을 dict로 바꿔주는 것이다.

print(movie_detail)
pprint(movie_detail)  # 딕셔너리를 가독성 있게 출력
# pprint(pretty print) : 가독성 있게 출력해주는 방법
```

- open : 파일 입출력

> __name__ == '__main__'

- import sth : 기능을 sth에서 가져온다.
- 필요한 기능만 가져오는 기능



