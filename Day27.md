# 20220812 TIL

## String

> python 에서의 문자열 처리

- 문자열 : 컨테이너 > 시퀀스 > 변경불가능 > iterable
- 인덱싱, 슬라이싱 가능

> 문자열 뒤집기

- palindrome : 회문

```python

string = 'Hello Algorithm'

string_list = list(string)
string_list.reverse()
print(string_list)

reversed_string = ''.join(string_list)

print(reversed_sting)

# 슬라이싱 활용

string = 'Hello Algorithm'
reversed_string = string[::-1]

print(reversed_string)
```

> 문자열 숫자를 정수로 변환하기

- int()와 같은 atoi()함수 만들기

```python
def atoi(number):
    int_number = 0

    for char in number:
        int_number *= 10
        int_number += ord(char) - ord('0')

    return int_number

result = atoi('123')
print(type(result))
print(result)
# <class 'int'>
# 123
```
