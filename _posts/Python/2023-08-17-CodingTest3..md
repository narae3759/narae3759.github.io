---
layout: single
header:
    teaser: "/assets/images/pythonteaser.PNG"
title: "[알고리즘] 깊이 우선 탐색(Deep First Search, DFS)"
excerpt: "목표. DFS를 이용하여 그래프를 그리고 문제를 해결할 수 있다."
categories: codingtest
tags: [CodingTest, DFS, 깊이 우선 탐색, Recursive function, Stack, Programmers, Baekjoon]
---

# 1. 깊이 우선 탐색

## 1) 개념 정리
* 첫 시작을 `start`라고 했을 때, 더이상 탐색할 수 없을 때까지 계속 탐색하는 과정을 말한다. 
* 모든 경우의 수를 찾고, 그 경우의 수 중 조건을 만족하는 것을 출력한다. 
* Stack으로 푸는 방법과 Recursion Function으로 푸는 방법 2가지가 있다고 한다. 

### Stack(정리 중)

### 재귀함수(Recursive Function)
    
```python
visited = [0 for _ in range(N+1)]       # 방문했는지 안했는지의 여부
num = 1                                 # 방문 순서를 표시하기 위함
def dfs(graph, visited, start):
    global num
    visited[start] = num

    for node in graph[start]:
        if visited[node] == 0:          # 방문한 적이 없는 노드만 방문 예줭
            num += 1
            dfs(graph, visited, node)
```

* ***Note!*** 재귀함수를 사용할 때에는 `RecursionError`를 조심해야 한다. 만약 이 에러를 만났다면 다음 코드로 해결할 수 있다. 
    ```python
    sys.setrecursionlimit(int)
    ```


## 2) 그래프 개념 정리

<p style="text-align:center;">
    <img src="/assets/images/codingtest/dfs1.png" width="50%">
</p>

* 방향이 있는지의 유무, 가중치의 유무에 따라 그래프를 나눌 수 있다.
* 용어
    * 정점(vertex or node) : 동그라미
    * 간선(edge or link) : 동그라미 사이를 잇는 선
    * 인접 정점(Adjacent vertex) : 정점과 이어지는 정점
* 그래프의 연결관계를 리스트로 나타낸 것을 **인접 리스트**라고 하는데 이를 이용하여 문제를 해결한다. <br>
리스트를 만들 때 편의 상 노드번호와 맞추기 위해 0번째 요소에 빈 리스트를 포함하여 만든다. 
* EX) `N`개의 정점이 있을 때, 무방향 그래프를 그려보자.
    ```python
    # 무방향
    graph = [[] for _ in range(N+1)]

    for _ in range(M):
        node1, node2 = map(int, input().split(' '))
        graph[node1].append(node2)
        graph[node2].append(node1)
    ```
    양방향이기 때문에 그래프에 node를 바꿔서 두번 삽입한 것을 볼 수 있다. 


# 2. 실습 문제

* [알고리즘 수업 - 깊이 우선 탐색 1(무방향 그래프, 오름차순)](https://www.acmicpc.net/problem/24479)
* [알고리즘 수업 - 깊이 우선 탐색 2(무방향 그래프, 내림차순)](https://www.acmicpc.net/problem/24480)

<div class="notice" markdown="1" style="font-size:12pt;">
<h1 style='margin-top:0em'>Reference</h1>

* [[노마드 코더]개발자라면 꼭 알아야할 Hash Table의 모든 것!](https://youtu.be/HraOg7W3VAM)
* [[Wikidocs]좌충우돌, 파이썬으로 자료구조 구현하기](https://wikidocs.net/193049)

</div>