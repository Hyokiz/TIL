# 20220929 TIL

## 최소신장트리(MST)

1. 크루스칼

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



2. 프림




## 최단경로(다익스트라)