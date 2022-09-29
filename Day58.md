# 20220929 TIL

## 최소신장트리(MST)

> 크루스칼

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



## 최단경로(다익스트라)