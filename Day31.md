# 20220817 TIL

## 스택

> 스택의 특성

- 선형 구조를 갖는다.
  - 선형 구조 : 자료 간의 관계가 1대1의 관계
  - 비선형 구조 : 자료 간의 관계가 1대N의 관계(예 : 트리)
- 스택에 자료를 삽입하거나 자료를 꺼낼 수 있다.
- 마지막에 삽입한 자료를 가장 먼저 꺼낸다. 후입선출

> 스택을 프로그램에서 구현하기 위해서 필요한 자료구조와 연산

- 자료구조 : 자료를 선형으로 저장할 저장소

  - 배열을 사용할 수 있다.
  - 저장소 자체를 스택으로 부르기도 함.
  - 스택에서 마지막 삽입된 원소의 위치를 top이라 부른다.

- 연산

  - 삽입 : 저장소에 자료를 저장. 보통 push
  - 삭제 : 저장소에서 자료를 꺼낸다. 삽입한 자료의 역순. 보통 pop
  - 스택이 공백인지 아닌지를 확인하는 연산. isEmpty
  - 스택의 top에 있는 item을 반환하는 연산. peek

- 스택의 삽입 / 삭제 과정

  - 빈 스택에 원소 A, B, C를 차례로 삽입 후 한번에 삭제하는 연산과정

- 스택의 push 알고리즘
  - append 메소드를 통해 리스트의 마지막에 데이터 삽입

```python
def push(item, size):
    global top
    top += 1
    if top == size:
        print('overflow!')
    else:
        stack[top] = item

size = 10
stack = [0] * size
top = -1

push(10, size)
top += 1        # push(20)
stack[top] = 20 #
```

- 스택의 pop 알고리즘

```python
def pop():
    if len(s) == 0:
        # underflow
        return
    else:
        return s.pop(-1)
```

> 스택의 구현

```python
def pop():
    global top
    if top == -1:
        print('underflow')
        return 0
    else:
        top -= 1
        return stack[top + 1]

print(pop())

if top > -1:    # pop()
    top -= 1
    print(stack[top])
```

> 스택 연습문제

```python
stackSize = 10
stack = [0] * stackSize
top = -1

top += 1    # push(1)
stack[top] = 1

top += 1    # push(2)
stack[top] = 2

top -= 1
temp = stack[top + 1]
print(temp)

temp = stack[top]
top -= 1
print(temp)

# 2
# 1

stack2 = []
stack2.append(10)
stack2.append(20)
print(stack2.pop())
print(stack2.pop())

# 20
# 10
```

> 스택 구현 고려 사항

- 1차원 배열을 사용하여 구현할 경우 구현이 용이하다는 장점이 있지만 스택의 크기를 변경하기가 어렵다는 단점
- 해결법으로 저장솔르 동적으로 할당하여 스택 구현.

> 스택의 응용1 : 괄호검사

- 괄호의 종류 : 대괄호, 중괄호, 소괄호
- 조건

  1. 왼쪽 괄호의 개수와 오른쪽 괄호의 개수가 같아야 한다.
  2. 같은 괄호에서 왼쪽 괄호는 오른쪽 괄호보다 먼저 나와야 한다.
  3. 괄호 사이에는 포함 관계만 존재한다.

- 스택을 이용한 괄호 검사
  - 문자열 괄호 조사해서 왼쪽 괄호 만나면 스택에 삽입, 오른쪽 괄호를 만나면 top괄호 삭제하고 오른쪽 괄호와 짝이 맞는지 검사
  - 이 때, 스택이 비어 있으면 조건1 또는 2에 위배, 짝이 맞지 않으면 조건 3 위배
  - 마지막 괄호까지 조사한 후 스택에 괄호가 남아있다면 조건1에 위배

> 스택의 응용2 : function call

- 프로그램에서의 함수 호출과 복귀에 따른 수행 순서 관리
  - 후입 선출 구조이므로, 스택을 이용하여 수행순서 관리
  - 함수 호출이 발생하면 정보들을 스택 프레임에 저장하여 시스템 스택에 삽입
  - 함수의 실행이 끝나면 top원소(스택 프레임)를 삭제(pop)하면서 프레임에 저장되어 있던 복귀주소 확인 후 복귀
  - 이 과정 반복하여 전체 프로그램 수행이 종료되면 시스템 스택은 공백 스택이 된다.

> 재귀호출

- 자기 자신을 호출하여 순환 수행되는 것
- 재귀로 함수를 만들면 프로그램의 크기를 줄이고 간단하게 작성

- 0과 1로 시작하고 이전의 두 수 합을 다음 항으로 하는 수열을 피보나치라 한다.

  - 0, 1, 1, 2, 3, 5, 8, 13, ...

- 피보나치 수열의 i 번째 값을 계산하는 함수 F를 정의하면 다음과 같다.

  - F0 = 0, F1 = 1
  - Fi = F(i-1) + F(i-2) for i >= 2

- 위의 정의로부터 피보나치 수열의 i번째 항을 반환하는 함수를 재귀함수로 구현할 수 있다.

```python

def f(i, N):
    if i == N:
        print(i)
        return
    else:
        print(i)
        f(i+1, N)

f(0, 3)
```

- 재귀 2

```python
def f(i, N):
    if i == N:
        return
    else:
        print(A[i])
        f(i+1, N)

N = 3
A = [1, 2, 3]
B = [0] * N
f(0, N)
```

> Memoization

- 앞의 예에서 피보나치 수를 구하는 함수를 재귀함수로 구현한 알고리즘은 문제점이 있다.
- 엄청난 중복 호출 존재
- 컴퓨터 프로그램을 실행할 때 이전에 계산한 값을 메모리에 저장하여 매번 다시 계산하지 않도록 실행속도를 빠르게 하는 기술. 동적 계획법의 핵심이 되는 기술
- 앞의 예에서 피보나치 수를 구하는 알고리즘에서 fibo(n)의 값을 계산하자마자 저장하면 실행시간을 O(n)으로 줄일 수 있다.

```python
# memo를 위한 배열을 할당하고, 모두 0으로 초기화한다.
# memo[0]을 0으로 memo[1]은 1로 초기화한다.

def fibo1(n):
    global memo
    if n >= 2 and len(memo) <= n:
        memo.append(fibo1(n-1) + fibo1(n-2))
    return memo[n]

memo = [0, 1]
```

- 팩토리얼

```python
def f(n): # 팩토리얼 n! 1! = 1
    if n <= 1: # 1 이하로 하지 않는다면 0이 들어가므로 에러
        return 1
    else:
        return n * f(n-1)

for i in range(21):
    print(i, f(i))
```

- 피보나치

```python
def fibo(n):
    if n < 2:
        return n
    else:
        return fibo(n-1) + fibo(n-2)

for i in range(21):
    print(i, fibo(i))
```

```python
def fibo(n):
    if memo[n] == -1:
        memo[n] = fibo(n-1) + fibo(n-2)
    return memo[n]

memo = [-1] * 101
memo[0] = 0
memo[1] = 1
for i in range(101):
    print(i, fibo(i)) # 위의 식보다 더 빠름
```

> DP(Dynamic Programming)

- 동적 계획 알고리즘은 그리디 알고리즘과 같이 최적화 문제를 해결하는 알고리즘
- 입력 크기가 작은 부분 문제들을 모두 해결하고 그 해들을 이용하여 보다 큰 크기의 부분 문제들 해결. 최종적으로 원래 주어진 입력의 문제를 해결하는 알고리즘

- 피보나치 수 DP 적용 알고리즘

```python
def fibo_dp(n):
    table[0] = 0
    table[1] = 1
    for i in range(2, n+1):
        table [i] = table[i-1] + table[i-2]
    return

table = [0] * 101
fibo_dp(100)

t = int(input())
for tc in range(1, t+1):
    n = int(input())
    print(f'#{tc} {table[n]}')
```

```python
a = 0
b = 1
n = 20
for _ in range(n-1):
    a, b = b, a + b
```

- 피보나치 수 DP 적용 알고리즘

```python
def fibo2(n) :
    f = [0, 1]

    for i in range(2, n+1):
        f.append(f[i-1] + f[i-2])

    return f[n]
```

- DP의 구현 방식

  - recursive 방식 : fib1()
  - iterative 방식 : fib2()

- memoization을 재귀적 구조에 사용하는 것보다 반복적 구조로 DP를 구현한 것이 성능 면에서 보다 효율적
- 재귀적 구조는 내부에 시스템 호출 스택을 사용하는 오버헤드가 발생하기 때문

> DPS(깊이우선탐색)

- 비선형구조인 그래프 구조는 그래프로 표현된 모든 자료를 빠짐없이 검색하는 것이 중요
- 두가지 방법

  - 깊이 우선 탐색(Depth First Search, DFS)
  - 너비 우선 탐색(Breadth First Search, BFS)

- 시작 정점의 한 방향으로 깊이 탐색해 가다가 갈 곳이 없으면 가장 마지막 정점으로 되돌아와서 탐색 반복. 결국 모든 정점 방문.
- 가장 마지막 정점으로 되돌아가서 탐색을 반복해야 하므로 후입선출 구조의 스택 사용

> DFS 알고리즘

1. 시작 정점 v를 결정하여 방문한다.
2. 정점 v에 인접한 정점 중
   1. 방문하지 않은 정점 w가 있으면, 정점v를 스택에 push 정점 w를 방문. 그리고 w를 v로하여 다시 2 반복
   2. 방문하지 않은 정점이 없으면, 탐색의 방향을 바꾸기 위해서 스택을 pop하여 받은 가장 마지막 방문 정점을 v로하여 다시 2 반복
3. 스택이 공백이 될 때 까지 2 반복

> DFS 예

```python
# A~G -> 0~6
adjList = [
    [1, 2],     # 0
    [0, 3, 4],  # 1
    [0, 4],     # 2
    [1, 5],     # 3
    [1, 2, 5],  # 4
    [3, 4, 6],  # 5
    [5]]        # 6

def dfs(v, N):
    visited = [0] * N   # visited 생성
    stack = [0] * N     # stack 생성
    top = -1
    print(v)            # 방문
    visited[v] = 1      # 시작점 방문 표시
    while True:
        for w in adjList[v]:    # if (v의 인접 정점 중 방문 안 한 정점 w가 있으면)
            if visited[w] == 0: # push(v);
                top += 1
                stack[top] = v  # v <- w; (w에 방문)
                v = w           # visited[w] <- true;
                print(v)        # 방문
                visited[w] = 1

                break
        else:                   # w가 없으면
            if top != -1:       # 스택이 비어있지 않은 경우
                v = stack[top]  # pop
                top -= 1
            else:               # 스택이 비어 있으면
                break
N = 7
visited = [0] * N # visited 생성 visited : [1, 1, 1, 1, 1, 1, 1]
stack = [0] * N   # stack 생성 stack : [1, 0, 2, 4, 5, 0, 0]
dfs(1, N)
print()
```

```python
# 0번부터 V번까지, E개의 간선
7 8
0 1
0 2
1 3
1 4
2 4
3 5
4 5
5 6

def dfs(v):
    print(v)        # v 방문
    visited[v] = 1
    for w in adjList[v]:
        if visited[w] == 0: # 방문하지 않은 w
            dfs(w)

V, E = map(int, input().split())
N = V + 1
adjList = [[] for _ in range(N)]
for _ in range(E):
    a, b = map(int, input().split())
    adjList[a].append(b)
    adjList[b].append(a)

visited = [0] * N       # visited 생성
stack = [0] * N         # stack 생성
dfs(0)

```
