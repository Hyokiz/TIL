# 20220825 TIL

## Queue

- 한쪽에서만 넣고 다른 한쪽에서만 뺀다.
- FIFO(First-in First-Out, 선입선출 방식)

- enqueue : 데이터 삽입
- dequeue : 데이터 가져오기

> 선형큐

- front : 머리
- rear : 꼬리
- front, rear == -1 로 초기화

- enqueue : rear + 1
- dequeue : front + 1
- is_empty : front == rear
- is_full : rear + 1 == size
- 선형 큐의 단점
  - 잘못된 포화상태 인식

> 리스트를 이용한 큐 자료구조의 단점

- 데이터가 많은 경우 비효율적.
- 맨 앞 데이터가 빠지면서 리스트 인덱스가 하나씩 당겨지기 때문.

- 덱(Deque, Double-Ended Queue) 자료구조 == 양방향으로 삽입과 삭제가 자유로운 큐
  - 큐보다 훨씬 빠르다.
