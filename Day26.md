# 20220811 TIL

## 완전탐색

- 이차원 리스트의 완전탐색에서 많이 등장하는 유형인 상하좌우 탐색을 알아보자.
  - (0, 0)에서부터 이차원 리스트의 모든 원소를 순회하며 (완전탐색)
  - 각 지점에서 상하좌우에 위치한 다른 지점을 조회하거나 이동하는 방식이다.
- 이차원 리스트의 인덱스의 조작을 통해서 상하좌우 탐색을 한다.
- 이때 행과 열의 변량인 -1, +1을 델타(delta)값이라 한다.
- 행은 x, r로 주로 나타낸다.
- 열은 y, c로 주로 나타낸다.

```python
for i in range(4):
  nx = x + dx[i]
  ny = y + dy[i]

```

- 상하좌우 이동 후 범위를 벗어나지 않는지 확인 및 갱신하기

```python
for i in range(4):
  nx = x + dx[i]
  ny = y + dy[i]

  if 0 <= nx < 3 and 0 <= ny < 3:
    x = nx
    y = ny

```

```python
#1. 델타값 정의(상하좌우)
dx = [-1, 1, 0, 0]
dy = [0, 0, -1, 1]

#2. 이차원 리스트 순회
for x in range(n):
  for y in range(m):

    #3. 델타값을 이용해 상하좌우 이동
    for i in range(4):
      nx = x + dx[i]
      ny = y + dy[i]

      #4. 범위를 벗어나지 않으면 갱신
      if 0 <= nx < 3 and 0 <= ny < 3:
        x = nx
        y = ny
```

```python
# 대각선 이동 추가
dx = [-1, 1, 0, 0, -1, 1, -1, 1]
dy = [0, 0, -1, 1, -1, -1, 1, 1]
```

### 달팽이 숫자 풀이 예시

```python
# 시계방향으로 돈다.
# [0, 0]에서 시작하여 처음엔 오른쪽으로 이동
# 범위를 벗어나면 아래로 이동
# 범위를 벗어나면 왼쪽으로 이동
# 범위를 벗어나면 위쪽으로 이동
# 위에 이미 값이 있으면 다시 오른쪽 이동

# 1. 델타값 정의
dx = [0, 1, 0, -1]
dy = [1, 0, -1, 0]

for t in range(1 , int(input()) + 1):
  n = int(input())
  snail = [[0] * n for _ in range(n)]
  x, y = 0, 0 # 출발 위치
  direction = 0 # 처음 출발 방향 오른쪽

  for i in range(1, n * n + 1):
    snail[x][y] = i
    # 다음 위치 이동
    nx = x + dx[direction]
    ny = y + dy[direction]

    # 범위 안에 있는지, 이미 숫자가 있는지 확인
    if 0 <= nx < n and 0 <= ny < n and snail[nx][ny] == 0:
      x, y = nx, ny # 이동
    
    else:
      # 방향 바꿔서 이동
      direction = (direction + 1) % 4 # direction이 4가 된다면 out of index. 따라서 4로 나눈 나머지를 대입
      x += dx[direction]
      y += dy[direction]

  print(f'#{t}')
  # for i in range(n):
  #   for j in range(n):
  #     print(snail[i][j], end=' ')
  #   print()
  for line in snail:
    print(*line)
```

## 비트연산

```python
numbers = [1, 2, 3, 4]
n = len(numbers)
# 부분집합의 개수 만큼 반복 
# 1을 2진수로 바꾸고 n번만큼 왼쪽으로 민다. 빈 공간은 0으로 채운다. 
# ex. 1 << 2 == 4(100(이진수)) // 4(100(이진수)) << 2 == 16(10000(이진수))

for i in range(1 << n): # 2의 n제곱과 같은 말
  for j in range(n):
    if i & (1 << j):
      print(numbers[j], end=' ')
  print() # 다음 부분집합 출력을 위한 줄 바꿈
```

