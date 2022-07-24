# 0724 TIL

1. 간단한 N의 약수

```python
N = int(input())

for i in range(1, N+1):
    if N % i == 0:

print(i,end=" ")
```

2. List의 합 구하기

```python
def list_sum(_):
    result = 0
    for i in _:
        result += i
    return result

print(list_sum([1, 2, 3, 4, 5]))
```

3. Dictionary로 이루어진 List의 합 구하기

```python
def dict*list_sum(*):
    result = 0
    for i in (_):
        result += i['age']
    return result

print(dict_list_sum([{'name': 'kim', 'age': 12}, {'name': 'lee', 'age': 4}]))
```

4. 2차원 List의 전체 합 구하기

```python
def all_list_sum(num_lists):
    lists_sum = 0
    for num_list in num_lists:
        for num in num_list:
            lists_sum += num
    return lists_sum
```

5. 숫자의 의미

```python
def get_secret_word(numbers):
    word = ''
    for i in numbers:
        word += chr(i)
    return word

print(get_secret_word([83, 115, 65, 102, 89]))
```

# 6. 내 이름은 몇일까?

```python
def get_secret_number(word):
    numbers = 0
    for i in word:
        numbers += ord(i)
    return numbers

print(get_secret_number('happy'))
```

# 7. 강한 이름

```python
def get_strong_word(word1, word2):
    result1 = 0
    result2 = 0
    for i in word1:
        result1 += ord(i)
        for j in word2:
            result2 += ord(j)
        if result1 > result2:
            return word1
        elif result1 < result2:
            return word2
        else:
            return word1, word2

print(get_strong_word('z', 'a'))
```
