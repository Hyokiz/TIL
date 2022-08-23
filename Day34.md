# 20220823 TIL

## 계산기

- 컴퓨터는 왼쪽부터 계산하므로 중위 표기식이 아닌 후위 표기식을 사용한다.

```python
for t in range(1, int(input()) + 1):
  word = input() # 중위표기법
  result = '' # 후위표기법 변환 결과
  stack = []

  for token in word:
    # 토큰이 연산자 혹은 괄호라면
    if token in '*/-+()':
      # 1. 스택이 비어있는 상태이거나 토큰이 여는 괄호라면 push
      if not stack or token == '(':
        stack.append(token)

      # 2. 토큰이 연산자라면 스택 top과 비교하여 우선순위가 높으면 push,
      # 낮으면 더 우선순위가 낮은 연산자를 만날 때 까지 pop하고 결과값에 담음
      elif token in '*/':
        while stack and stack[-1] in '*/':
          result += stack.pop()
        stack.append(token) # 이후 스택에 연산자 push
      elif token in '+-':
        while stack and stack[-1] != '(':
          result += stack.pop()
        stack.append(token) # 이후 스택에 연산자 push

      # 3. 토큰이 닫는 괄호라면 여는 괄호를 만날 때 까지 모두 pop하고 결과 값에 담음
      elif token == ')':
        while stack and stack[-1] != '(':
          result += stack.pop()
          stack.pop() # 남아있는 여는 괄호 버림
    # 토큰이 피연산자라면 그대로 결과 값에 담음
    else:
      result += token
```

- 괄호의 우선순위가 제일 높다.

> 계산기

- 위의 코드에서 후위 표기법으로 바꾼 목적 : 계산하기 위해서

```python
for t in range(1, int(input()) + 1):
  word = input()
  stack = []

  for char in word:
    # 1. 피연산자를 만나면 스택에 push
    if char not in '*/+-':
      stack.append(int(char))
    # 2. 연산자를 만나면 필요한 만큼의 피연산자를 스택에서 pop하여 연산하고,
    # 연산 결과를 다시 스택에 push 한다.
    else:
      x = stack.pop()
      y = stack.pop()
      if char == '+':
        stack.append(y + x)
      elif char == '-':
        stack.append(y - x)
      elif char == '*':
        stack.append(y * x)
      elif char == '/':
        stack.append(y / x)

  # 3. 수식이 끝나면 마지막으로 스택을 pop하여 출력한다.
  print(f'#{t} {stack[-1]}')
```

## 순열과 조합

- 순열(permutation): 순서 상관있음
- 조합(combination): 순서 상관없음

> 순열

```python
def permutations(arr):
  # 뽑고 싶은 만큼 뽑았다면 출력 및 종료
  if len(arr) == length:
    print(arr)
    return

  for i in range(len(numbers)):
    if not visited[i]:
      # 1. i번째 원소를 뽑는다.
      visited[i] = True
      arr.append(numbers[i])

      # 2. 재귀함수 진행
      permuatations(arr)

      # 3. 재귀함수 종료 후, 뽑았던 i번째 원소 삭제
      visited[i] = False
      arr.pop()

numbers = [1, 2, 3, 4]
visited = [False] * len(numbers)
length = 3 # 뽑고 싶은 원소의 개수

permutations([])
```

> 조합

```python
def combinations(arr, start):
  # 뽑고 싶은 만큼 뽑았따면 출력 및 종료
  if len(arr) == length:
    print(arr)
    return

  for i in range(start, len(numbers)):
    # 1. i번째 원소를 뽑는다.
    arr.append(numbers[i])

    # 2. 재귀함수 진행
    combinations(arr, i + 1)

    # 3. 재귀함수 종료 후, 뽑았던 i번째 원소 삭제
    arr.pop()

numbers = [1, 2, 3, 4]
length = 3 # 뽑고 싶은 원소의 개수

combinations([], 0)
```

- 다른 방법 (이거로도 부분집합을 구할 수 있다.)

```python
def combinations(arr, depth):
  # 전체 원소의 개수만큼 재귀가 진행됐다면 종료
  if depth == len(numbers):
    # 뽑고 싶은만큼 뽑았다면 출력
    if len(arr) == length:
      print(arr)
    return
  
  # 1. 현재 원소를 뽑고 다음 재귀로 진행하는 경우
  combinations(arr + [numbers[depth]], depth + 1)

  # 2. 현재 원소를 뽑지 않고 다음 재귀로 진행하는 경우
  combinations(arr, depth + 1)

numbers = [1, 2, 3, 4]
length = 3 # 뽑고 싶은 원소의 개수

combinations([], 0)
```

> 부분집합 문제

```python
def powerset(arr, depth, total):
  # 가지치기(pruning) - 합이 10 초과면 더 진행할 필요가 없다.
  if total > 10:
    return

  # 전체 원소의 개수만큼 재귀가 진행됐다면 종료
  if depth == len(numbers):
    # 원소의 합이 10이라면 해당 부분집합 출력
    if total == 10:
      print(arr)
    return

  # 1. 현재 원소를 뽑고 다음 재귀로 진행하는 경우
  powerset(arr, [numbers[depth]], depth + 1, total + numbers[depth])

  # 2. 현재 원소를 뽑지 않고 다음 재귀로 진행하는 경우
  powerset(arr, depth + 1, total)

numbers = list(range(1, 11))
powerset([], 0, 0)
```

> 내장함수로 순열, 조합 쉽게하기

```python
from itertools import permutations, combinations

numbers = [1, 2, 3, 4]
length = 3 # 뽑고 싶은 원소의 개수

# 순열
for case in permutations(numbers, length):
  print(case)

# 조합
for case in combinations(numbers, length):
  print(case)
