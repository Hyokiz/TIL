# 20220818 TIL

## DFS

- 취업 알고리즘 중요!!

- 스택, 재귀, 그래프 모두 DFS를 배우기 위해 배운 것.

## 자료, 자료구조, 알고리즘

### 자료

- 자료 == Data
  - 메모리에 저장되는 데이터 

- 자료구조 == Data Structure
  - 데이터 + 읽기, 쓰기, 삽입, 삭제, 탐색, 수정 등(메서드) 연산 기능 제공

- 자료구조 == 데이터 + 연산
  - 다수의 데이터를 효율적으로 저장하고 조작할 수 있으므로 알고리즘 구현의 기본 재료가 된다.
  - 재료의 특성을 알아야 요리를 할 수 있다.
  - 자료구조(list, set, dict, stack, queue) >> Algorithm

## 스택(Stack)

- 데이터를 한쪽에서만 넣고 빼는 자료구조
- LIFO(Last-in First-out, 후입선출) 방식
  - ex. 뷔페의 접시 쌓기

- 스택 자료구조의 대표 연산
  - 새로운 데이터 삽입(push), 최신 데이터 제거(pop)
  - push, pop은 같은 곳에서 일어난다.

> 스택 자료구조 쉽게 이해하기 - 1

- url에 들어가면 가장 위에 있는 데이터 == 현재 페이지
- 다른 url에 들어가면 가장 위에 있는 데이터 갱신 == 두번째 페이지
- 계속 쌓인다.
- 뒤로 가기를 누르면 제일 최신 url이 빠지고 그 전 페이지 == 현재페이지
- 다시 다른 새로운 url 이동 == stack 이 쌓인다.

- 파이썬은 List로 스택을 간편하게 사용할 수 있따!
- List를 Stack으로 사용 시, insert와 pop(-1)은 사용 안하기로 약속.
- ex. BOJ10773

```python
stack = []

for _ in range(int(input())):
    number = int(input())

    if number == 0:
        stack.pop()
    else:
        stack.append(number)

print(sum(stack))
```

## 재귀

- 재귀란 함수가 자기 자신을 계속 호출하며 문제를 해결하는 것
- 두 가지 부분으로 나누어 작성
  1. 종료 조건
     - 가장 하위 문제 도달 시 재귀 종료
     - 반드시 종료 조건 작성
  2. 점화식
     - 좁은 범위의 하위 문제 해결을 위한 재귀식(자기 자신 호출하는 부분)

- 팩토리얼 문제 점화식

```python
def factorial(n):
  if n <= 1:
    return 1 # 종료 조건(Base Case)

  return n * factorial(n-1)
```

- ex. BOJ10870. 피보나치수 5

```python
def fibo(n):
  # 1. 종료 조건 (Base Case)
  if n <= 1:
    return n

  # 2. 점화식(재귀식)
  return fibo(n - 2) + fibo(n - 1)

print(fibo(5))
# 5
```
  1. 종료 조건(Base Case)
     - 0번째 항은 0, 1번째 항은 1의 피보나치수
     - 따라서 n이 1이하이면 n을 반환하고 재귀 종료
  2. 점화식
     - 특정 항의 값은 앞 두 항의 값
     - F(n) = F(n-2) + F(n-1)

- memoization 으로 피보나치 5를 풀어보자!

```python
# 2. 피보나치 재귀 + Memoization 풀이
# 0 1 1 2 3 5 8 13 ...

def fibo(n):
    if len(memo) <= n:
        memo.append(fibo(n - 1) + fibo(n - 2))
    return memo[n]


memo = [0, 1]

print(fibo(5))
# print(fibo(40)) # 단순 재귀만 사용했을 때보다 더 빠르게 결과가 출력됨을 확인
```
  - Dynamic Programming : 동적 계획법
    - 작은 부분을 먼저 해결하고, 이것을 이용하여 큰 부분 해결
      1. 하위 문제가 중복 될 때
      2. 최적 부분 구조를 가질 때

  - Dynamic Programming 중 하나가 memoization.

- ex. 연습문제 괄호매칭

```python
for t in range(1, int(input()) + 1):
  brackets = input()
  stack = []
  result = -1 # 일단 불가능 상태로 초기화

  for bracket in brackets:
    # 1. 여는 괄호인 경우
    if bracket = '(':
      stack.append(bracket) # 스택에 넣음
    # 2. 닫는 괄호인 경우
    else:
      if not stack: # 닫는 괄호인데 스택이 비었다는 건 짝이 맞지 않음.
        break       # 그대로 종료
      stack.pop()   # 닫는 괄호가 나왔으므로 스택에 들어있는 여는 괄호 제거
  else:
    if not stack:
      result = 1 # 반복문이 정상 종료 되었을 때, 스택이 비어있다는 건 괄호의 짝이 맞는다는 것.

  print(f'#{t} {result}')
```

## 그래프

- 정점(Vertex)과 이를 연결하는 간선(Edge)들의 집합으로 이루어진 비선형 자료구조
  - 선형 자료구조 : 일자로 되어있는 형태
  - 비선형 자료구조 : 순서가 없는?? 

> 그래프 관련용어

- 정점(Vertex) : 간선으로 연결되는 객체, 노드(Node)라고도 한다.
- 간선(Edge) : 정점 관의 관계(연결)를 표현하는 선
- 경로(Path) : 시작 정점부터 도착 정점까지 거치는 정점을 나열한 것
- 인접(Adjacency) : 두 개의 정점이 하나의 간선으로 직접 연결된 상태

> 그래프의 종류

1. 무방향 그래프
   - 간선의 방향이 없는 가장 일반적인 그래프
   - 간선을 통해 양방향의 정점 이동가능

2. 유방향 그래프
   - 간선의 방향이 있는 그래프
   - 방향이 가리키는 정점으로 이동 가능

> 그래프의 표현

1. 인접 행렬
   - 두 정점을 연결하는 간선이 없으면 0, 있으면 1을 가지는 행렬로 표현하는 방식
  ```python
  # 입력
  # 7 7
  # 0 1
  # 0 2
  # 1 3
  # 1 4
  # 2 4
  # 2 5
  # 4 6

  n, m = map(int, input().split()) # 정점, 간선 개수
  graph = [[0] * n for _ in range(n)] # n x n 의 인접 행렬 초기화

  # 간선의 개수만큼 반복하면서 인접 행렬에 표시
  for _ in range(m):
    v1, v2 = map(int, input().split()) # 인접한 정점 2개
    graph[v1][v2] = 1
    graph[v2][v1] = 1

  # 인접 행렬 출력
  for line in graph:
    print(*line)
  ```

2. 인접 리스트

- 리스트를 통해 각 정점에 대한 인접 정점들을 순차적으로 표현하는 방식

```python
# 입력
# 7 7
# 0 1
# 0 2
# 1 3
# 1 4
# 2 4
# 2 5
# 4 6

n, m = map(int, input().split()) # 정점, 간선 개수
graph = [[0] * n for _ in range(n)] # n x n 의 인접 행렬 초기화

# 간선의 개수만큼 반복하면서 인접 리스트에 표시
for _ in range(m):
  v1, v2 = map(int, input().split()) # 인접한 정점 2개
  graph[v1].append(v2) = 1
  graph[v2].append(v1) = 1

# 인접 리스트 출력
for line in graph:
  print(*line)
```

> 인접 행렬 vs 인접 리스트

- 인접 행렬 : 직관적이고 만들기 편하지만, 불필요하게 공간이 낭비된다.
- 인접 리스트 : 연결된 정점만 저장하여 효율적이므로 자주 사용된다.

## 깊이우선탐색(DFS)

- 그래프 탐색 알고리즘에는 깊이우선탐색과 너비우선탐색이 있다.
  - 스택 + 그래프 + 큐
    - 스택 + 그래프 : 깊이우선탐색(DFS)
    - 그래프 + 큐 : 너비우선탐색(BFS)

> 깊이우선탐색

- 모든 정점을 방문할 때 유리. 경우의 수, 순열과 조합에서 많이 사용
- 너비우선탐색에 비해 코드 구현 간단.

> DFS 동작 과정

- 조건이 있다.
  1. 그래프가 있어야 한다.
     - 그래프는 인접 행렬, 인접 리스트 방식으로 표현할 수 있다.
  2. 방문 처리할 리스트가 있어야 한다.
     - 각 정점을 방문했는지 여부를 판별할 방문 체크 리스트가 필요하다.
       - 정점의 개수 만큼 False를 만들어 줌. 방문하면 True, 방문하지 않은 정점을 False 
  3. DFS 탐색
     1. 현재 정점 방문 처리
     2. 인접한 모든 정점 확인
     3. 방문하지 않은 인접 정점 이동

> 재귀(Recursion)를 이용한 DFS

- 스택과 재귀의 원리가 같기 때문에 거의 재귀로 많이 푼다.
- 함수 호출 시 메모리의 스택 영역에 호출이 쌓인다. 따라서 반복문 대신 재귀 함수를 사용해도 풀 수 있다.

```python
def dfs(v):
  visited[v] = True # 방문 처리

  for next_v in graph[v]: # 인접한 모든 정점에 대해
    if not visited[next_v]:
      dfs(next_v) # 방문하지 않았다면 인접 정점으로 이동

visited = [False] * n # 방문 처리 초기화
dfs(0) # 0번 정점에서 시작
```



