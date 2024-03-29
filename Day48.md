# 20220915 TIL

- 트리와 힙
1. CT
2. start
3. 그리디
4. 퀵정렬, 병합정렬

- 이것들을 배우는 이유 = 가중치 그래프인 다익스트라, 벨만포드, 플로이드워셜를 풀기 위함
- MST의 크루스칼, 프림을 풀기 위함.

## 트리

- 자료구조에는 선형 알고리즘, 비선형 알고리즘이 있다.
  - 선형 : 앞과 뒤가 1대1로 매치 되어있을 때 ex. 리스트
  - 비선형 : 무작위로 퍼져 있는 구조 ex. 그래프, 트리

- 나무를 뒤집어 놓은 것 같다고 해서 트리.
  - 가장 위쪽이 root(뿌리), 가장 밑이 leaf(나뭇잎)

> 트리 용어

- 서브 트리 : 부모 노드와 연결된 간선을 끊었을 때 생성되는 트리
- 자손 노드 : 서브 트리에 있는 하위 레벨의 노드들
- 단말 노드(리프 노드) : 차수가 0인 노드

> 트리 vs 그래프

- 트리 : 트리는 그래프의 한 종류이다. 그래프의 부분집합
  1. 유방향
     - 위에서 아래로. 부모에서 자식으로만 간다.
  2. 비순환
     - 일방통행. 부모에서 자식으로만
  3. 부모가 1개
     - 그래프는 여러개 일 수 있다.

> 트리를 배우는 이유?

1. 코테에 나온다.
2. 효율적.

> 완전이진트리

- 메모리 낭보 X

## 이진트리의 표현 - 배열

- 노드 번호의 성질
  - 노드 번호가 i인 부모 노드 번호 = floor(3/2)
  - 노드 번호가 i인 노드의 왼쪽 자식 노드 번호 = 2 * i
  - 노드 번호가 i인 노드의 오른쪽 자식 노드 번호 = 2 * i + 1
  - 레벨 n인 노드 번호 시작 번호 = 2 ** n

- 번외
  - int(-3/2) == -1
  - -3 // 2 == -2
  - int는 뒤에 소수점을 버림. floor는 낮은 수를 기준?

```py
# 루트 노드 찾기
def find_root(n):
    for node in range(1, n + 1):
        if tree[node][2] == 0:  # 부모 노드가 없으면 루트 노드
            return node


# 전위 순회 (V -> L -> R)
def pre_order(node):
    if node != 0:
        print(node, end=' ')
        pre_order(tree[node][0])
        pre_order(tree[node][1])


# 중위 순회 (L -> V -> R)
def in_order(node):
    if node != 0:
        in_order(tree[node][0])
        print(node, end=' ')
        in_order(tree[node][1])


# 후위 순회 (L -> R -> V)
def post_order(node):
    if node != 0:
        post_order(tree[node][0])
        post_order(tree[node][1])
        print(node, end=' ')


v = int(input())  # 정점 개수
tree = [[0] * 3 for _ in range(v + 1)]  # [왼쪽자식, 오른쪽자식, 부모]
edges = list(map(int, input().split()))

# 이진 트리 구현
for i in range(0, len(edges), 2):
    parent, child = edges[i], edges[i + 1]

    if tree[parent][0] == 0:
        tree[parent][0] = child  # 왼쪽 자식 노드 삽입
    else:
        tree[parent][1] = child  # 오른쪽 자식 노드 삽입

    tree[child][2] = parent  # 부모 노드 삽입

root = find_root(v)  # 루트 노드 찾기

print(tree)
print('-------------')

print('전위 순회 : ', end='')
pre_order(root)
print()

print('중위 순회 : ', end='')
in_order(root)
print()

print('후위 순회 : ', end='')
post_order(root)
print()


"""
이진 트리 구현 방법은 아래와 같습니다.

                1          2          3      ...
[[0, 0, 0], [2, 3, 0], [4, 0, 1], [5, 6, 1], ...]

1번 노드
- 왼쪽: 2번
- 오른쪽: 3번
- 부모: 없음

2번 노드
- 왼쪽: 4번
- 오른쪽: 없음
- 부모: 1번

3번 노드
- 왼쪽: 5번
- 오른쪽: 6번
- 부모: 1번
"""
```

## 이진탐색트리

- 리스트의 이진 탐색
  - 반드시 리스트는 정렬된 상태여야 한다.

- 이진 탐색 트리
  - 반드시 왼쪽 < 중간 < 오른쪽 
  - 왼쪽 서브트리의 값보단 루트가 커야하고, 루트보단 오른쪽 서브트리의 값이 더 커야한다.
  - 중위 순회하면 오름차순으로 정렬된 값을 얻을 수 있다.

- 이진탐색트리의 삽입, 삭제는 나중에 필요하면 공부할 것

## 힙(heap)

- 다익스트라, 프림알고리즘에서 나옴
- 완전 이진 트리에 있는 노드 중에서 키값이 가장 큰 노드나 키값이 가장 작은 노드를 찾기 위해서 만든 자료구조
- 완전 이진 트리 사용 이유
  - 메모리
  - 편리함

- 최대 힙(max heap)
  - 키값이 가장 큰 노드를 찾기 위한 완전 이진 트리

- 최소 힙(min heap)
  - 키값이 가장 작은 노드를 찾기 위한 완전 이진 트리

> 힙 삽입, 삭제 잘 보기

1. 마지막 위치에 새 노드 삽입
2. 최소 / 최대 힙 만족할때까지 swap

- 파이썬은 heapq로 쉽게 구현할 수 있다.

```py
from heapq import heappush, heappop

heap = []

heappush(heap, 2)
heappush(heap, 5)
heappush(heap, 7)
heappush(heap, 3)
heappush(heap, 4)
heappush(heap, 6)
print(heap)

while heap:
  print(heappop(heap))

```

