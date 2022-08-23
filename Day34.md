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
