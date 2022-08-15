# 20220815 TIL

## 과목평가 대비

> Gravity 문제

```python
t = int(input())

for tc in range(1, t+1):
    n = int(input())
    numbers = list(map(int, input().split()))

    result = 0

    for i in range(n):
        max_height = 0

        for j in range(i+1, n):
            if numbers[i] > numbers[j]:
                max_height += 1

        if result < max_height:
            result = max_height

    print(f'#{tc} {result}')
```

> 버블정렬

```python
def BubbleSort(a, N):
    for i in range(N-1, 0, -1):
        for j in range(0, i):
            if a[j] > a[j+1]:
                a[j], a[j+1] = a[j+1], a[j]
```

> 카운팅 정렬

```python
def Counting_Sort(A, B, k):
# A [] -- 입력 배열(1 to k)
# B [] -- 정렬된 배열
# C [] -- 카운트 배열

    C = [0] * (k + 1)

    for i in range(len(A)):
        C[A[i]] += 1

    for i in range(1, len(C)):
        C[i] += C[i-1]

    for i in range(len(B)-1, -1, -1):
        C[A[i]] -= 1
        B[C[A[i]]] = A[i]
```

- ex. Baby-gin

```python
t = int(input())

for tc in range(1, t + 1):
    arr = list(map(int, input()))
    answer = 0
    # 0 ~ 9 까지의 숫자 범위이고 out of range ERROR를 피하기 위해 범위보다 많은 저장 공간을 만든다.
    count_arr = [0] * 12
    run = triple = 0

    # count_arr의 값을 채워준다.
    for i in range(6):
        count_arr[arr[i]] += 1

    # count_arr의 요소를 탐색한다.
    for i in range(12):

        # 만약 index의 값이 3이상으로 triple일 경우
        if count_arr[i] >= 3:
            triple += count_arr[i] // 3
            count_arr[i] %= 3

        # 만약 연속된 3개의 index의 값이 모두 0보다 클 경우
        if count_arr[i] > 0 and count_arr[i+1] > 0 and count_arr[i+2] > 0:
            run += 1
            count_arr[i] -= 1
            count_arr[i+1] -= 1
            count_arr[i+2] -= 1
            # 같은 연속된 수의 run일 경우 한 번 더 조건을 만족할 수 있다.
            if count_arr[i] > 0 and count_arr[i+1] > 0 and count_arr[i+2] > 0:
                run += 1
                count_arr[i] -= 1
                count_arr[i+1] -= 1
                count_arr[i+2] -= 1

    if triple + run == 2:
        answer = 1

    print(f'#{tc} {answer}')
```

```python
import sys

sys.stdin = open("input.txt")

tc = int(input())

for t in range(tc):

    number = int(input())
    a = [0] * 12
    for _ in range(6):
        a[number % 10] += 1
        number //= 10

    i = 0
    tri = run = 0
    while i < 10:
        if a[i] >= 3: # triplete 조사 후 데이터 삭제
            a[i] -= 3
            tri += 1
            continue
        if a[i] >= 1 and a[i+1] >= a[i+2] >= 1: # run 조사 후 데이터 삭제
            a[i] -= 1
            a[i+1] -= 1
            a[i+2] -= 1
            run += 1
            continue
        i += 1

    if run + tri == 2: print(f'#{t+1} {1}')
    else:
        print(f'#{t+1} {0}')
```

> 완전 검색

- 모든 경우의 수를 나열하고 확인하는 기법
- 경우의 수가 상대적으로 작을 때 유용

> 단순하게 순열을 생성하는 방법

```python
for i1 in range(1, 4):
    for i2 in range(1, 4):
        if i2 != i1:
            for i3 in range(1, 4):
                if i3 != i1 and i3 != i2:
                    print(i1, i2, i3)
```

> 탐욕 알고리즘

- 최적해를 구하는 데 사용되는 근시안적인 방법
- 결정해야할 때마다 그 순간에 최적이라고 생각되는 것을 선택

> 2차원 배열

- 1차원 List를 묶어놓은 List

> 2차원 배열의 접근

- 행 우선 순회

```python
for i in range(n):
    for j in range(m):
        Array[i][j]
```

- 열 우선 순회

```python
for j in range(m):
    for i in range(n):
        Array[i][j]:
```

- 지그재그 순회

```python
for i in range(n):
    for j in range(m):
        Array[i][j + (m - 1 - 2*j) * (i % 2)]
```

- 델타를 이용한 2차 배열 탐색

```python
# n x n 배열


di = [-1, 1, 0, 0]
dj = [0, 0, -1, 1] # 상하좌우
```

> 비트 연산자

- 비트연산자

  - & : and연산
  - | : or연산
  - << : 피연산자의 비트 열을 왼쪽으로 이동
  - />> : 피연산자의 비트 열을 오른쪽으로 이동

- ex.

```python
arr = [3, 6, 7, 1, 5, 4]

n = len(arr) # n : 원소의 개수

for i in range(1<<n):
    for j in range(n):
        if i & (1<<j):
            print(arr[j], end=", ")
    print()
print()
```

> 검색

- 저장되어 있는 자료 중 원하는 항목을 찾는 작업

> 순차 검색

- 일렬로 되어 있는 자료를 순서대로 검색하는 방법

  - 가장 간단하고 직관적
  - 검색 대상 수가 많은 경우 비효율적

- 2가지 경우
  - 정렬되어 있지 않은 경우
  - 정렬되어 있는 경우

> > 정렬되어 있지 않은 경우

- 검색 과정
  - 첫 번째 원소부터 비교
  - 키 값이 동일하면 그 원소의 인덱스 반환
  - 검색 대상 없으면 검색 실패

> > 정렬되어 있는 경우

- 오름차순 가정
- 원소의 키 값이 검색대상의 키 값보다 크면 검색 종료

> 이진 검색

- 자료의 가운데에 있는 항목의 키 값과 비교하여 다음 검색 위치 결정
- 자료가 정렬된 상태여야 한다.

- 검색 과정
  - 자료의 중앙에 있는 원소를 고른다.
  - 중앙 원소의 값과 목표 값 비교
  - 목표값이 중앙 원소값보다 작으면 왼쪽 반 검색, 크다면 오른쪽 반 검색
  - 반복

```python
def binarySearch(a, N, key):
    start = 0
    end = N - 1
    while start <= end:
        middle = (start + end) // 2
        if a[middle] == key:
            return True
        elif a[middle] > key:
            end = middle - 1
        else:
            start = middle + 1
    return False
```

- 재귀함수 이용

```python
def binarySearch2(a, low, high, key):
    if low > high:
        return False
    else:
        middle = (low + high) // 2
        if key == a[middle]:
            return True
        elif key < a[middle]:
            return binarySearch2(a, low, middle-1, key)
        elif a[middle] < key:
            return binarySearch2(a, middle+1, high, key)
```

> 선택 정렬

- 주어진 자료들 중 가장 작은 값의 원소부터 차례대로 위치 교환

```python
def selectionSort(a, N):
    for i in range(N-1):
        minIdx = i
        for j in range(i+1, N):
            for a[minIdx] > a[j]:
                minIdx = j
            a[i], a[minIdx] = a[minIdx], a[i]
```

> 셀렉션 알고리즘

- 저장되어 있는 자료로부터 k번째로 큰 혹은 작은 원소를 찾는 방법

```python
def select(arr, k):
    for i in range(0, k):
        minIdx = i
        for j in range(i + 1, len(arr)):
            if arr[minIdx] > arr[j]:
                minIdx = j
        arr[i], arr[minIdx] = arr[minIdx], arr[i]
    return arr[k-1]
```

> 문자

- 문자의 표현
  - 유니코드 인코딩
    - UTF-8 (in web, python)
      - min : 8bit, max : 32bit
    - UTF-16 (in windows, java)
      - min : 16bit, max : 32bit
    - UTF-32 (in unix)
      - min : 32bit, max : 32bit

> 문자열의 분류

- python에서의 문자열 처리

  - char 타입 없음
  - 문자열 기호

    - '', "", ''', """
    - +연결 : 문자열 + 문자열
    - /_반복 : 문자열 _ 수

  - 제공되는 메소드
    - replace, split, isalpha, find 등
    - 요소값을 변경할 수 없음(immutable)

> 문자열 숫자를 정수로 변환하기

- int()와 같은 atoi()함수 만들기

```python
def atoi(s):
    i = 0
    for x in s:
        i = i * 10 + ord(x) - ord('0')
    return i
```

- str() 함수를 사용하지 않고, itoa()구현하기
