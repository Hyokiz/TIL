# 20221003 TIL

## 순열과 조합

- 순열을 구하는 코드

```py
# visited를 이용한 순열 뽑기

def permutations(arr):
    # 뽑고 싶은 만큼 뽑았으면 출력 및 종료
    if len(arr) == length:
        print(arr)
        return

    for i in range(len(numbers)):
        if not visited[i]:
            # 1. i번째 원소 뽑기
            visited[i] = True
            arr.append(numbers[i])

            # 2. 재귀함수 진행
            permutations(arr)

            # 3. 재귀함수 종료 후 뽑았던 i번째 원소 삭제
            visited[i] = False
            arr.pop()

numbers = [1, 2, 3, 4]
visited = [False] * len(numbers)
length = 2

permutations([])

# [출력]

# [1, 2]
# [1, 3]
# [1, 4]
# [2, 1]
# [2, 3]
# [2, 4]
# [3, 1]
# [3, 2]
# [3, 4]
# [4, 1]
# [4, 2]
# [4, 3]
```

```py
# 자기 길이만큼 뽑는 순열

def permutations(depth):
    if depth == len(numbers):
        print(numbers)
        return

    for i in range(depth, len(numbers)):
        numbers[depth], numbers[i] = numbers[i], numbers[depth]
        permutations(depth + 1)
        numbers[depth], numbers[i] = numbers[i], numbers[depth]


numbers = [1, 2, 3, 4]

permutations(0)
```

```py
def permutations(i, k):
    if i == k:  # 인덱스 i == 원소의 개수
        print(p)
        return

    for j in range(i, k):
        p[i], p[j] = p[j], p[i]
        permutations(i + 1, k)
        p[i], p[j] = p[j], p[i]


p = [1, 2, 3]
permutations(0, 3)
```

- 조합을 구하는 코드

```py
# 비트연산자를 이용한 부분집합

numbers = [1, 2, 3, 4]
n = len(numbers)

for i in range(1 << n):  # 부분집합의 개수 만큼 반복
    for j in range(n):
        if i & (1 << j):
            print(numbers[j], end=' ')
    print()  # 다음 부분집합 출력을 위한 줄 바꿈

```

```py
# 재귀 조합 1
def combinations(arr, depth):
    # 전체 원소의 개수만큼 재귀가 진행됐다면 종료
    if depth == len(numbers):
        # 뽑고 싶은 만큼 뽑았다면 출력
        if len(arr) == length:
            print(arr)
        return

    # 1) 현재 원소를 뽑고 다음 재귀로 진행하는 경우
    combinations(arr + [numbers[depth]], depth + 1)

    # 2) 현재 원소를 뽑지 않고 다음 재귀로 진행하는 경우
    combinations(arr, depth + 1)


numbers = [1, 2, 3, 4]
length = 3  # 뽑고 싶은 원소의 개수

combinations([], 0)
```

```py
# 재귀 조합 2

def combinations(arr, start):
    # 뽑고 싶은 만큼 뽑았다면 출력 및 종료
    if len(arr) == length:
        print(arr)
        return

    for i in range(start, len(numbers)):
        # 1) i번째 원소를 뽑는다.
        arr.append(numbers[i])

        # 2) 재귀함수 진행
        combinations(arr, i + 1)

        # 3) 재귀함수 종료 후, 뽑았던 i번째 원소 삭제
        arr.pop()


numbers = [1, 2, 3, 4]
length = 3  # 뽑고 싶은 원소의 개수

combinations([], 0)
```
