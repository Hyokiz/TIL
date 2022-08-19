# 20220819 TIL

## 이차원 격자에서의 DFS

```python
visited = [[False] * m for _ in range(n)]
# 2차원 배열로 선언한다.
```
- 인접 정점은 델타값을 이용한 상하좌우 이동으로 갈 수 있다.

```python
def dfs(x, y):
  visited[x][y] = True

  for i in range(4):
    nx = x + dx[i]
    ny = y + dy[i]

    if 0 <= nx < n and 0 <= ny < m and not visited[nx][ny] and maze[nx][ny] = 0:
      road.append((nx, ny)) # 경로에 포함

      if nx == n - 1 and ny == m - 1:
        print(road)
        break

        dfs(nx, ny) # 다음 칸 이동

        road.pop() # 되돌아가면서 이전 경로 삭제

n, m = map(int, input().split())
maze = [list(map(int, input().split())) for _ in range(n)]
visited = [[False] * m for _ in range(n)]

dx, dy = [-1, 1, 0, 0], [0, 0, -1, 1] # 상하좌우
road = [(0, 0)] # 출구까지의 경로

dfs(0, 0) # (0, 0) 정점에서 시작
```

- 파이썬에서는 재귀가 1000번까지만 제한이 있어서 임의로 늘릴 수 있다.
  
```python
import sys
sys.setrecursionlimit(100000)
```
