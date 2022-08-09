# 20220809 TIL

## 버블 정렬

```python
sample = [55, 7, 78, 12, 42]

def buble_sort(a): # 정렬할 List
  for i in range(len(a) -1, 0, -1):
    for j in range(0, i):
      if a[j] > a[j + 1]:
        a[j], a[j + 1] = a[j + 1], a[j] # swap

  return a

print(bubble_sort(sample)) # [7, 12, 42, 55, 78]
```

- 심화

```python
sample = [("철수", 55), ("영희",7), ("민수", 78), ("기영", 12), ("유라", 42)]

def buble_sort(a): # 정렬할 List
  for i in range(len(a) -1, 0, -1):
    for j in range(0, i):
      if a[j][1] > a[j + 1][1]:
        a[j], a[j + 1] = a[j + 1], a[j] # swap

  return a

print(buble_sort(sample)) # [("영희",7), ("기영", 12), ("유라", 42), ("철수", 55), ("민수", 78)]
```

## 카운팅 정렬

```python
def counting_sort(original, k): # k에 최댓값을 적음으로 효율성 증가
  counter = [0] * (k + 1)

  # 1. counter에 original 원소의 빈도수 담기
  for i in original:
    counter[i] += 1

  # 2. 누적(counter 업데이트)
  for i in range(1, len(counter)):
    counter[i] += counter[i - 1]

  # 3. result 생성
  result = [-1] * len(original)

  # 4. result에 정렬하기(counter를 참조)
  for i in range(len(original) -1, -1, -1):
    counter[original[i]] -= 1
    result[counter[original[i]]] = original[i]
    # 거꾸로 하는 이유? 안정정렬(stable) - 같은 숫자여도 값이 다르다.
    # counter에 정리 된 숫자는 맨 뒤에 위치하기 때문.

  return result

a = [0, 4, 1, 3, 1, 2, 4, 1]
print(counting_sort(a, 5)) # [0, 1, 1, 1, 2, 3, 4, 4]
```