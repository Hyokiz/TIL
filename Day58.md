# 20220929 TIL

## 최소신장트리(MST)

> 크루스칼
  - 간선 위주로
  - 서로소 집합(Union-Find)
    - 서로소 집합 == 상호 배타 집합 == disjoint set

  - 집합의 기본 연산
    1. membership 연산(find)
    2. 합집합, 교집합, 차집합

  - 세가지 method

    1. make_set

      - 집합을 만드는 것

    2. find_set

      - 대표값으로 찾는다.

    3. union

      - find-set을 했을 때 대표값이 다르면(속해 있는 집합이 다르면) 합침(union)

```py
# 1. 반복문
# 같은 집합인지 확인
def find_set(node):
    while node != parent[node]:
        node = parent[node]
    return node


# # 2. 재귀
# def find_set(node):
#     if node != parent[node]:
#         return find_set(parent[node])
#     return node


# # 3. 재귀 - 경로 압축(부모 노드를 대표값으로 만듦)
# def find_set(node):
#     if node != parent[node]:
#         parent[node] = find_set(parent[node])
#     return parent[node]


n, m = map(int, input().split())  # 정점, 간선(Union 횟수) 개수
parent = list(range(n + 1))       # 자기 자신을 가리키는 집합들의 make-set

for _ in range(m):
    x, y = map(int, input().split())
    x_root, y_root = find_set(x), find_set(y)  # Find

    # Union
    if x_root != y_root:  # 서로소 집합인 경우만 합집합 연산
        if x_root < y_root:
            parent[y_root] = x_root
        else:
            parent[x_root] = y_root

# 출력
for i in range(1, n + 1):
    print(find_set(i), end=' ')

print()
print(parent)

# 입력값

# 6 4
# 5 6
# 4 5
# 3 4
# 1 3

# 출력값

# 1 2 1 1 1 1 
# [0, 1, 2, 1, 3, 4, 5]
```

> 최소 신장 트리

- 그래프, 모든 노드 포함, 사이클 X
- Greedy알고리즘(최소, 가장 싼거 고르기)
- 사이클이 발생하지 않으면서 가장 낮은 값만 고르기

```py
def find_set(node):
    if node != parent[node]:
        parent[node] = find_set(parent[node])  # 경로 압축(Path compression)
    return parent[node]


n, m = map(int, input().split())  # 정점, 간선 개수
edges = []
for _ in range(m):
    s, e, w = map(int, input().split())  # 시작 정점, 도착 정점, 비용
    edges.append((w, s, e))

edges.sort()  # (중요) 최소 비용의 간선부터 차례로 검사하기 위해 비용을 기준으로 오름차순 정렬

parent = list(range(n + 1))
counts = 0  # MST의 간선 개수 (정점 - 1 개가 되면 종료를 하기 위함)
cost = 0  # MST의 가중치 총합(== 최소 비용)

for dist, x, y in edges:
    x_root, y_root = find_set(x), find_set(y)  # x와 y의 각각 대표값

    if x_root != y_root:  # 사이클이 아니면
        parent[y_root] = x_root  # union
        cost += dist
        counts += 1

        if counts >= n - 1:  # 간선의 최대 개수는 정점 - 1 이므로 break
            break

print(cost)

# 입력
# 7 11
# 1 2 32
# 1 3 31
# 1 6 60
# 1 7 51
# 2 3 21
# 3 5 46
# 3 7 25
# 4 5 34
# 4 6 18
# 5 6 40
# 5 7 51

# 출력
# 175
```

- 크루스칼은 간선 위주로 본다.

> 프림

- 프림은 정점 위주로
- cut property
- 구현 방법

  1. 임의 정점 선택
  2. MST에서 갈 수 있는 모든 정점 중 가장 최고 비용 선택
  3. cost에 값 만큼 더한다.


```py
# 1) 일반적인 프림 알고리즘

def prim(start):
    visited = [False] * (n + 1)  # MST에 포함 여부 리스트
    distance = [INF] * (n + 1)  # distance[v] => 정점 v가 MST에 속한 정점과 연결된 간선의 비용
    distance[start] = 0
    cost = 0  # MST의 비용 총합(== 최소 비용)

    # 정점의 개수만큼 반복하면서 모든 정점을 이은 MST 생성
    for _ in range(n):
        # 1. MST의 정점에서 이동할 수 있는 모든 정점 중 가장 적은 비용으로 이동 가능한 정점 찾기(Greedy)
        min_dist = INF
        for i, dist in enumerate(distance):
            if not visited[i] and dist < min_dist:
                min_node = i
                min_dist = dist

        # 2. 해당 정점을 MST에 포함하고 비용을 더함
        visited[min_node] = True
        cost += min_dist

        # 3. 해당 정점과 인접한 정점에 대해 최소 비용 갱신
        for next_node, dist in graph[min_node]:
            if not visited[next_node] and dist < distance[next_node]:
                distance[next_node] = dist

    return cost


n, m = map(int, input().split())  # 정점, 간선 개수
graph = [[] for _ in range(n + 1)]
INF = 99999999  # 나올 수 없는 임의의 큰 수

for _ in range(m):
    s, e, w = map(int, input().split())  # 시작 정점, 도착 정점, 비용
    graph[s].append((e, w))
    graph[e].append((s, w))

print(prim(1))  # 1번 정점에서 시작

# 입력
# 7 11
# 1 2 32
# 1 3 31
# 1 6 60
# 1 7 51
# 2 3 21
# 3 5 46
# 3 7 25
# 4 5 34
# 4 6 18
# 5 6 40
# 5 7 51

# 출력
# 175
```

- 힙의 특징

  - 최소힙, 최대힙
  - 완전이진트리

```py
# 2) 힙을 이용한 프림 알고리즘

from heapq import heappush, heappop


def prim(start):
    visited = [False] * (n + 1)  # MST에 포함 여부 리스트
    heap = [(0, start)]  # 힙 선언 [(비용, 정점)]
    cost = 0  # MST의 가중치 총합(== 최소 비용)

    while heap:
        # 1. 가장 적은 비용으로 이동 가능한 정점 찾기(Greedy)
        min_dist, min_node = heappop(heap)  # 최소힙이므로 튜플의 첫 번째 원소를 기준으로 최소값 pop
        if visited[min_node]:
            continue  # 이미 MST에 포함된 정점이라면 무시

        # 2. 해당 정점을 MST에 포함하고 비용 총합을 더함
        visited[min_node] = True
        cost += min_dist

        # 3. 해당 정점과 인접한 정점에 대해 heappush
        for next_node, dist in graph[min_node]:
            if not visited[next_node]:
                heappush(heap, (dist, next_node))

    return cost


n, m = map(int, input().split())  # 정점, 간선 개수
graph = [[] for _ in range(n + 1)]

for _ in range(m):
    s, e, w = map(int, input().split())  # 시작 정점, 도착 정점, 비용
    graph[s].append((e, w))
    graph[e].append((s, w))

print(prim(1))  # 1번 정점에서 시작

# 입력
# 7 11
# 1 2 32
# 1 3 31
# 1 6 60
# 1 7 51
# 2 3 21
# 3 5 46
# 3 7 25
# 4 5 34
# 4 6 18
# 5 6 40
# 5 7 51

# 출력
# 175
```

> 크루스칼, 프림은 언제 사용해야 하나

- 크루스칼은 간선, 프림은 정점을 기준
- 간선이 많으면 프림(힙으로)사용, 정점이 많으면 크루스칼 사용


## 최단경로(다익스트라)

- 특정 정점에서 다른 모든 정점으로 가는 최단거리
- 음의 간선이 없어야 한다.
- Greedy 알고리즘

- 구현

  1. 출발지점 k 정하기
  2. distance k > v 비용
  3. 갱신

```py
# 1) 일반적인 다익스트라 알고리즘

def dijkstra(start):
    visited = [False] * (n + 1)  # 방문 처리 리스트(최단 거리가 확정된 정점)
    visited[start] = True
    distance[start] = 0

    # 시작 정점과 인접한 정점에 대해 최단 거리 초기화
    for e, w in graph[start]:
        distance[e] = w

    # 시작 정점을 제외한 나머지 정점에 대해서만 반복하므로 n - 1 번 반복함
    for _ in range(n - 1):
        # 1. 최단 거리가 확정되지 않은 정점들 중 최단 거리가 가장 짧은 정점을 선택
        min_dist = INF
        for i in range(1, n + 1):
            if not visited[i] and min_dist > distance[i]:
                min_node = i
                min_dist = distance[i]

        # 2. 해당 정점 최단 거리 확정
        visited[min_node] = True

        # 3. 해당 정점에 인접한 정점에 대해 최단 거리 갱신
        for next_node, dist in graph[min_node]:
            new_dist = distance[min_node] + dist
            if new_dist < distance[next_node]:
                distance[next_node] = new_dist


n, m = map(int, input().split())  # 정점, 간선 개수
graph = [[] for _ in range(n + 1)]
INF = 99999999  # 나올 수 없는 임의의 큰 수
distance = [INF] * (n + 1)  # 출발 정점에서 다른 정점들까지의 최단 거리(무한으로 초기화)

for _ in range(m):
    s, e, w = map(int, input().split())
    graph[s].append((e, w))

dijkstra(1)  # 1번 정점에서 시작
print(distance)

# 입력
# 6 11
# 1 2 3
# 1 3 5
# 2 3 2
# 2 4 6
# 3 2 1
# 3 4 4
# 3 5 6
# 4 5 2
# 4 6 3
# 5 1 3
# 5 6 6

# 출력
# [99999999, 0, 3, 5, 9, 11, 12]
```

- 힙

```py
# 2) 힙을 이용한 다익스트라 알고리즘

from heapq import heappush, heappop


def dijkstra(start):
    distance[start] = 0
    heap = [(0, start)]  # 힙 선언 [(비용, 정점)]

    while heap:
        # 1. 최단 거리가 가장 짧은 정점을 선택
        min_dist, min_node = heappop(heap)

        # 2. 이미 최단 거리로 기록되어 있는 값보다 높은 경우 무시
        if min_dist > distance[min_node]:
            continue

        # 3. 해당 정점에 인접한 정점에 대해 최단 거리 갱신
        for next_node, dist in graph[min_node]:
            new_dist = min_dist + dist
            if new_dist < distance[next_node]:
                distance[next_node] = new_dist
                heappush(heap, (new_dist, next_node))


n, m = map(int, input().split())  # 정점, 간선 개수
graph = [[] for _ in range(n + 1)]
INF = 99999999  # 나올 수 없는 임의의 큰 수
distance = [INF] * (n + 1)  # 출발 정점에서 다른 정점들까지의 최단 거리(무한으로 초기화)

for _ in range(m):
    s, e, w = map(int, input().split())
    graph[s].append((e, w))

dijkstra(1)  # 1번 정점에서 시작
print(distance)

# 입력
# 6 11
# 1 2 3
# 1 3 5
# 2 3 2
# 2 4 6
# 3 2 1
# 3 4 4
# 3 5 6
# 4 5 2
# 4 6 3
# 5 1 3
# 5 6 6

# 출력
# [99999999, 0, 3, 5, 9, 11, 12]
```