# 20220725

## 월말평가 리뷰

- 재귀함수(recursion)
  1.  종료 조건 (base-case)
  2.  점화식

```python
def dec_to_bin(n):
    # 1. 종료 조건
    if n < 2:
        return str(n)
    # 2. 점화식
    else:
        return dec_to_bin(n // 2) + str(n % 2)

print(dec_to_bin(23))
```

- 아스키코드

  - A = 65, z = 90 인 경우
    - -65를 해서 0~25로 만들고 26일 경우에 나누기 26해서 0으로 돌아가게 만든다.

- 이차원 리스트
  - 변량 델타이동

```python
a = [
    [0, 0, 0],
    [0, 1, 0],
    [0, 0, 0]
]

now = [1, 1]

# 상하좌우
dx = [-1, 1, 0, 0]
dy = [0, 0, -1, 1]

# 상
now[0] += dx[0]
now[1] += dy[0]

# 하
now[0] += dx[1]
now[1] += dy[1]

# 좌
now[0] += dx[2]
now[1] += dy[2]

# 우
now[0] += dx[3]
now[1] += dy[3]

# for문

for i in range(4):
    now[0] += dx[i]
    now[1] += dy[i]

#한칸이동
n = 3 # 행렬의 크기
m = 0 # 상하좌우 중 어디로 갈지에 대한 인덱스
now[0] += dx[m]
now[1] += dy[m]0

if now[0] < 0 or now[0] >= n or now[1] < 0 or now[1] >= n:
    print("범위 벗어남")
else:
    print("정상범위")
```
