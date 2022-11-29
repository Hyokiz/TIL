# 20221129 TIL

# 알고리즘 특강

# 목차

> 자료구조

- Tree
- Sagment Tree
- Fenwick Tree

# Tree

> Tree란

- 노드 간 계층과 1:N 관계를 갖는 자료구조

> Tree - Degree(차수)

- 노드에 연결된 자식 노드의 개수

> Tree - Level, Height, Depth(레벨, 높이, 깊이)

- 일반적으로 루트 노드부터 가장 높은 레벨

> Binary Tree

- 모든 노드가 최대 2개의 자식 노드를 가질 수 있는 트리

> Binary Tree -  노드의 개수 구하기

- 레벨/높이 H 일때 => 최소 H + 1개, 최대 2^H+1 - 1개

> Binary Tree - Complete Binary Tree (완전이진트리)

- 높이가 H이고 노드의 개수가 N일때, 빈 자리 없이 채워지는 트리
- 단 노드의 개수 <= N < 2^(H + 1) - 1

> Binary Tree - Skewed Binary Tree (편향 이진 트리)

- 높이가 H일때, 최소 노드 개수를 가지면서 한쪽 방향으로 노드는 가지는 트리

> Binary Tree - Traversal(순회)

- Traversal(순회) 란 트리의 각 노드를 중복되지 않게 전부 방문하는 것.
- 비 선형 구조로 선형 구조처럼 선후 연결 관계를 알 수 없다.

# Tree - 순회

> Binary Tree - Traversal(순회)

- 트리의 순회 방법

  - 전위 순회 : 부모 노드 방문 후, 좌/우 순서로 방문
  - 중위 순회 : 왼쪽 자식 노드 방문 후 부모 노드/오른쪽 자식 노드 방문
  - 후위 순회 : 좌/우 자식노드 방문 후 부모노드 방문

> Binary Tree - 전위 순회

- 전위 순회 방법

  - 현재 노드 n 을 방문하여 처리한다 > V
  - 현재 노드 n의 왼쪽 서브 트리로 이동한다 > L
  - 현재 노드 n의 오른쪽 서브 트리로 이동한다 > R

    ```java
    preorder_traverse(T) {
        if (T is not null) {
            visit(T)
            preorder_traverse(T.left)
            perorder_traverse(T.right)
        }
    }
    ```

# Sagment Tree

> Segment Tree 란?

- 어떤 데이터가 존재할 때 특정 구간의 결과값을 구하는데 사용하는 자료구조

- 배열의 크기가 커지면?

  - 구간별 합을 구해 저장해두면 빠르게 찾을 수 있다.

- Sagment Tree는 Binary Tree(이진 트리) 구조를 가지고 있다.

# Fenwick Tree

> Fenwick Tree란?

- Segment Tree처럼 구간에 대한 연산을 저장하는 트리
- Segment Tree 보다 적은 메모리로 사용 가능하다.
- 비트를 이용한 구간 연산을 진행


