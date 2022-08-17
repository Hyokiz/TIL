# 20220817 TIL

## 스택

> 스택의 특성

- 선형 구조를 갖는다.
  - 선형 구조 : 자료 간의 관계가 1대1의 관계
  - 비선형 구조 : 자료 간의 관계가 1대N의 관계(예 : 트리)
- 스택에 자료를 삽입하거나 자료를 꺼낼 수 있다.
- 마지막에 삽입한 자료를 가장 먼저 꺼낸다. 후입선출

> 스택을 프로그램에서 구현하기 위해서 필요한 자료구조와 연산

- 자료구조 : 자료를 선형으로 저장할 저장소

  - 배열을 사용할 수 있다.
  - 저장소 자체를 스택으로 부르기도 함.
  - 스택에서 마지막 삽입된 원소의 위치를 top이라 부른다.

- 연산

  - 삽입 : 저장소에 자료를 저장. 보통 push
  - 삭제 : 저장소에서 자료를 꺼낸다. 삽입한 자료의 역순. 보통 pop
  - 스택이 공백인지 아닌지를 확인하는 연산. isEmpty
  - 스택의 top에 있는 item을 반환하는 연산. peek

- 스택의 삽입 / 삭제 과정

  - 빈 스택에 원소 A, B, C를 차례로 삽입 후 한번에 삭제하는 연산과정

- 스택의 push 알고리즘
  - append 메소드를 통해 리스트의 마지막에 데이터 삽입

```python
def push(item, size):
    global top
    top += 1
    if top == size:
        print('overflow!')
    else:
        stack[top] = item

size = 10
stack = [0] * size
top = -1

push(10, size)
top += 1        # push(20)
stack[top] = 20 #
```

- 스택의 pop 알고리즘

```python
def pop():
    if len(s) == 0:
        # underflow
        return
    else:
        return s.pop(-1)
```

> 스택의 구현

```python
def pop():
    global top
    if top == -1:
        print('underflow')
        return 0
    else:
        top -= 1
        return stack[top + 1]

print(pop())

if top > -1:    # pop()
    top -= 1
    print(stack[top])
```

> 스택 연습문제

```python
stackSize = 10
stack [0] * stackSize
top = -1

top += 1    # push(1)
stack[top] = 1

top += 1    # push(2)
stack[top] = 2

top -= 1
temp = stack[top + 1]
print(temp)

temp = stack[top]
top -= 1
print(temp)

# 2
# 1

stack2 = []
stack2.append(10)
stack2.append(20)
print(stack2.pop())
print(stack2.pop())

# 20
# 10
```

> 스택 구현 고려 사항

- 1차원 배열을 사용하여 구현할 경우 구현이 용이하다는 장점이 있지만 스택의 크기를 변경하기가 어렵다는 단점
- 해결법으로 저장솔르 동적으로 할당하여 스택 구현.

> 스택의 응용1 : 괄호검사

- 괄호의 종류 : 대괄호, 중괄호, 소괄호
- 조건

  1. 왼쪽 괄호의 개수와 오른쪽 괄호의 개수가 같아야 한다.
  2. 같은 괄호에서 왼쪽 괄호는 오른쪽 괄호보다 먼저 나와야 한다.
  3. 괄호 사이에는 포함 관계만 존재한다.

- 스택을 이용한 괄호 검사
  - 문자열 괄호 조사해서 왼쪽 괄호 만나면 스택에 삽입, 오른쪽 괄호를 만나면 top괄호 삭제하고 오른쪽 괄호와 짝이 맞는지 검사
  - 이 때, 스택이 비어 있으면 조건1 또는 2에 위배, 짝이 맞지 않으면 조건 3 위배
  - 마지막 괄호까지 조사한 후 스택에 괄호가 남아있다면 조건1에 위배

> 스택의 응용2 : function call

- 프로그램에서의 함수 호출과 복귀에 따른 수행 순서 관리
  - 후입 선출 구조이므로, 스택을 이용하여 수행순서 관리
  - 함수 호출이 발생하면 정보들을 스택 프레임에 저장하여 시스템 스택에 삽입
  - 함수의 실행이 끝나면 top원소(스택 프레임)를 삭제(pop)하면서 프레임에 저장되어 있던 복귀주소 확인 후 복귀
  - 이 과정 반복하여 전체 프로그램 수행이 종료되면 시스템 스택은 공백 스택이 된다.

> 재귀호출

- 자기 자신을 호출하여 순환 수행되는 것
- 재귀로 함수를 만들면 프로그램의 크기를 줄이고 간단하게 작성

- 0과 1로 시작하고 이전의 두 수 합을 다음 항으로 하는 수열을 피보나치라 한다.

  - 0, 1, 1, 2, 3, 5, 8, 13, ...

- 피보나치 수열의 i 번째 값을 계산하는 함수 F를 정의하면 다음과 같다.

  - F0 = 0, F1 = 1
  - Fi = F(i-1) + F(i-2) for i >= 2

- 위의 정의로부터 피보나치 수열의 i번째 항을 반환하는 함수를 재귀함수로 구현할 수 있다.

```python

def f(i, N):
    if i == N:
        print(i)
        return
    else:
        print(i)
        f(i+1, N)

f(0, 3)
```

- 재귀 2

```python
def f(i, N):
    if i == N:
        return
    else:
        print(A[i])
        f(i+1, N)

N = 3
A = [1, 2, 3]
B = [0] * N
f(0, N)
```

> Memoization

- 앞의 예에서 피보나치 수를 구하는 함수를 재귀함수로 구현한 알고리즘은 문제점이 있다.
- 엄청난 중복 호출 존재
- 컴퓨터 프로그램을 실행할 때 이전에 계산한 값을 메모리에 저장하여 매번 다시 계산하지 않도록 실행속도를 빠르게 하는 기술. 동적 계획법의 핵심이 되는 기술
- 앞의 예에서 피보나치 수를 구하는 알고리즘에서 fibo(n)의 값을 계산하자마자 저장하면 실행시간을 O(n)으로 줄일 수 있다.

```python
# memo를 위한 배열을 할당하고, 모두 0으로 초기화한다.
# memo[0]을 0으로 memo[1]은 1로 초기화한다.

def fibo1(n):
    global memo
    if n >= 2 and len(memo) <= n:
        memo.append(fibo1(n-1) + fibo1(n-2))
    return memo[n]

memo = [0, 1]
```
