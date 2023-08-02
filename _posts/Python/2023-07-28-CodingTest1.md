---
layout: single
header:
    teaser: "/assets/images/pythonteaser.PNG"
title: "[자료구조] 스택(Stack)과 큐(Queue)"
excerpt: "목표. 스택과 큐의 정의를 이해하고 관련 문제를 풀 수 있다."
categories: codingtest
tags: [CodingTest, Stack, Queue, Data Structure, Programmers, Baekjoon]
---

# 1. 스택(Stack)

<p style="text-align:center;">
    <img src="/assets/images/codingtest/stack1.PNG" width="70%">
</p>

* LiFo(Last in First out) : <u>마지막에 들어온 사람</u>이 먼저 나간다.
* Keywords
    * 삽입(Push)
    * 추출(Pop)
    * 현재 위치(Top)
    * 마지막 데이터 확인(Peek)
    * 비어있는 지 확인(Empty)

## 클래스로 이해하기

```python 
stack.py

class Stack:
    def __init__(self,n):
        self.n = n                                  # stack의 저장공간
        self.top = -1                               # 처음 위치
        self.stack = [None for _ in range(self.n)]  # stack 만들기
    
    # 원소 삽입
    def push(self, data):
        if self.top == self.n - 1:
            return '더 이상 push할 공간이 없습니다.'

        self.top += 1    
        self.stack[self.top] = data
        return self.stack

    # 원소 추출
    def pop(self):
        if self.top == -1:
            return 'pop할 원소가 없습니다.'
        
        self.stack.pop(self.top)
        self.stack.append(None)
        self.top -= 1
        return self.stack
    
    # 마지막 원소 확인
    def peek(self):
        if self.top == -1:
            print('stack이 비었습니다.')
            return None
        return self.stack[self.top]

    # 비어있는지 확인
    def empty(self):
        if self.top == -1:
            return 1
        return 0

# stack.py를 실행하면 진행
if __name__ == "__main__":
    stack = Stack(5)

    for i in range(7):
        print(f'push {i} > {stack.push(i)}')
        if i == 3:
            print(f'peek > {stack.peek()}')
    for i in range(7):
        print(f'pop > {stack.pop()}')
        if i == 2:
            print(f'peek > {stack.peek()}')
    print(f'empty > {stack.empty()}')
```

<h3>Output</h3>

```python
## push 0 > [0, None, None, None, None]
## push 1 > [0, 1, None, None, None]
## push 2 > [0, 1, 2, None, None]
## push 3 > [0, 1, 2, 3, None]
## peek > 3
## push 4 > [0, 1, 2, 3, 4]
## push 5 > 더 이상 push할 공간이 없습니다.
## push 6 > 더 이상 push할 공간이 없습니다.
## pop > [0, 1, 2, 3, None]
## pop > [0, 1, 2, None, None]
## pop > [0, 1, None, None, None]
## peek > 1
## pop > [0, None, None, None, None]
## pop > [None, None, None, None, None]
## pop > pop할 원소가 없습니다.
## pop > pop할 원소가 없습니다.
## empty > 1
```

# 2. 큐(Queue)

<p style="text-align:center;">
    <img src="/assets/images/codingtest/queue1.PNG" width="70%">
</p>

* FiFo(First in First out) : <u>먼저 온 사람</u>이 먼저 나간다.
* keywords
    * 삽입(EnQueue)
    * 추출(DeQueue)
    * 머리(Front)
    * 꼬리(Rear)

## 클래스로 이해하기
* 선형 큐의 경우, 앞 자리는 비는데 뒷 공간이 다 차서 공간 부족이 나타날 수 있다. <br>
이를 해결하기 위해 `front`는 항상 0으로 두고, dequeue가 되면 `None`을 삽입한다.

```python
class Queue:
    def __init__(self,n):
        self.n = n                                  # queue의 저장공간
        self.rear = -1                              # 마지막 위치
        self.queue = [None for _ in range(self.n)]  # queue 만들기
    
    # 원소 삽입
    def enqueue(self, data):
        if self.rear == self.n - 1:
            return '더 이상 endeque할 공간이 없습니다.'

        self.rear += 1    
        self.queue[self.rear] = data
        return self.queue

    # 원소 추출
    def dequeue(self):
        if self.rear == -1:
            return 'dequeue할 원소가 없습니다.'
        
        self.queue.pop(0)
        self.queue.append(None)
        self.rear -= 1
        return self.queue
    
    # 마지막 원소 확인
    def rearvalue(self):
        if self.rear == -1:
            print('queue이 비었습니다.')
            return None
        return self.queue[self.rear]

    # 비어있는지 확인
    def empty(self):
        if self.rear == -1:
            return 1
        return 0

if __name__ == "__main__":
    queue = Queue(5)

    for i in range(7):
        print(f'enqueue {i} > {queue.enqueue(i)}')
        if i == 3:
            print(f'rear value > {queue.rearvalue()}')
    for i in range(7):
        print(f'dequeue > {queue.dequeue()}')
        if i == 2:
            print(f'rear value > {queue.rearvalue()}')
    print(f'empty > {queue.empty()}')
```

<h3>Output</h3>

```python
## enqueue 0 > [0, None, None, None, None]
## enqueue 1 > [0, 1, None, None, None]
## enqueue 2 > [0, 1, 2, None, None]
## enqueue 3 > [0, 1, 2, 3, None]
## rear value > 3
## enqueue 4 > [0, 1, 2, 3, 4]
## enqueue 5 > 더 이상 endeque할 공간이 없습니다.
## enqueue 6 > 더 이상 endeque할 공간이 없습니다.
## dequeue > [1, 2, 3, 4, None]
## dequeue > [2, 3, 4, None, None]
## dequeue > [3, 4, None, None, None]
## rear value > 4
## dequeue > [4, None, None, None, None]
## dequeue > [None, None, None, None, None]
## dequeue > dequeue할 원소가 없습니다.
## dequeue > dequeue할 원소가 없습니다.
## empty > 1
```

# 3. deque() 이용하기
위에서는 리스트를 이용하여 스택과 큐를 설명했다. 하지만, 실제 코딩테스트를 하다보면 시간복잡도에서 pass하지 못하는 경우가 많이 발생한다. 이 경우 `from collections import deque`를 이용하여 빠르고 쉽게 코딩할 수 있다. `deque()`를 사용해서 만들어진 형태를 **덱(deque)**이라고 한다. 가장 많이 쓰이는 함수만 소개한다. 

<table>
<tr><th>code</th><th>description</th></tr>
<tr><td>append(data)</td><td>오른쪽에 원소 data(하나)를 추가한다.</td></tr>
<tr><td>appendleft(data)</td><td>왼쪽에 원소 data(하나)를 추가한다.</td></tr>
<tr><td>extend(data)</td><td>오른쪽에 원소 data(여러 개|문자열, 리스트 등)를 추가한다.</td></tr>
<tr><td>extendleft(data)</td><td>왼쪽에 원소 data(여러 개|문자열, 리스트 등)를 추가한다.</td></tr>
<tr><td>pop()</td><td>가장 오른쪽 원소를 제거한다. 제거값을 반환함.</td></tr>
<tr><td>popleft()</td><td>가장 왼쪽 원소를 제거한다. 제거값을 반환함.</td></tr>
<tr><td>index(data)</td><td>data의 위치를 반환한다.</td></tr>
<tr><td>insert(i,data)</td><td>i 위치에 data를 삽입한다.</td></tr>
<tr><td>clear()</td><td>모든 data를 제거하고, 길이를 0으로 만든다.</td></tr>
<tr><td>reverse()</td><td>data의 순서를 뒤집는다.</td></tr>
<tr><td>rotate(n)</td><td>뒤에서 n번째부터 순환한다.</td></tr>
</table>

## Examples

```python
## deque                > []
## append 0             > [0]
## appendleft 1         > [1, 0]
## extend abc           > [1, 0, 'a', 'b', 'c']
## extendleft [5,6,7]   > [7, 6, 5, 1, 0, 'a', 'b', 'c']
## pop                  > [7, 6, 5, 1, 0, 'a', 'b']
## popleft              > [6, 5, 1, 0, 'a', 'b']
## reverse              > ['b', 'a', 0, 1, 5, 6]
## rotate 1             > [6, 'b', 'a', 0, 1, 5]
## clear                > []
```

# 4. 실전 문제 풀어보기(난이도 순)
시간 복잡도를 고려하여 `deque()`를 이용해야만 풀 수 있는 문제들을 난이도별로 나열하였다. 각 문제의 옆을 드래그하면 Hint를 볼 수 있다.

## 스택(stack)
* [Bronze II, 백준 17608. 막대기](https://www.acmicpc.net/problem/17608) Hint. <font color="white">new보다 큰 친구들만 <b>남길 때까지</b> pop을 해야 한다.</font>
* [Silver IV, 백준 3986. 좋은 단어](https://www.acmicpc.net/problem/17608) Hint. <font color="white">괄호 쌍 찾기 문제와 같다.</font>

## 큐(queue)
* [Silver V, 백준 2161. 카드1](https://www.acmicpc.net/problem/2161) Hint. <font color="white">rotate 함수를 이용하면 빠르다.</font>

<div class="notice" markdown="1" style="font-size:12pt;">
<h1 style='margin-top:0em'>Reference</h1>

* [[노마드 코더]개발자라면 무조건 알아야하는 자료구조! 5분컷](https://youtu.be/Nk_dGScimz8)
* [[Wikidocs]좌충우돌, 파이썬으로 자료구조 구현하기](https://wikidocs.net/192069)
* [[Python Documentation] collections - deque](https://docs.python.org/ko/3/library/collections.html#deque-objects)

</div>