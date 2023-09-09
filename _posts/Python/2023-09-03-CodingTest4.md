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

<p style="text-align:center;">
    <img src="/assets/images/codingtest/dfs1.png" width="40%">
</p>

* 첫 시작을 `start`라고 했을 때, 더 이상 탐색할 수 없을 때까지 계속 탐색하는 과정을 말한다. <br>
트리라고 생각했을 때, 부모 노드에서 자식 노드로 계속해서 탐색하는 과정이다.
* 스택(Stack)으로 푸는 방법과 재귀함수(Recursion Function)으로 푸는 방법 2가지가 있다고 한다. 

## 2) 탐색 과정
준비물 : `visited` 변수

가장 끝에 있는 원소를 추출하면서 그와 동시에 `stack`에 후보가 될 수 있는 정점을 계속해서 추가한다.

<p style="text-align:center;">
    <img src="/assets/images/codingtest/dfs_gif.gif" width="70%">
</p>


## 3) 코드 구현
위의 그림을 예시로 코드를 구현해보았다.

### Stack으로 풀기
```python
# 스택으로 DFS 구현
def dfs_stack(graph,start):
    stack = [start]
    visited = []

    while stack:
        node = stack.pop()
        if node not in visited:
            visited.append(node)
            stack.extend(graph[node])
            print(f'stack {stack}')
            print(f'visited {visited}')
    
    return visited
```

### 재귀함수(Recursive Function)
    
```python
# 재귀함수로 DFS 구현
def dfs_recursive(graph,start):
    visited = []

    def dfs(node):
        if node not in visited:
            visited.append(node)
            print(f'visited {visited}')
            for n in graph[node][::-1]:
                dfs(n)
            
    dfs(start)

    return visited
```

* ***Note!*** 재귀함수를 사용할 때에는 `RecursionError`를 조심해야 한다. 만약 이 에러를 만났다면 다음 코드로 해결할 수 있다. 
    ```python
    sys.setrecursionlimit(int)
    ```

# 2. 실습 문제

* [알고리즘 수업 - 깊이 우선 탐색 1(무방향 그래프, 오름차순)](https://www.acmicpc.net/problem/24479)
* [알고리즘 수업 - 깊이 우선 탐색 2(무방향 그래프, 내림차순)](https://www.acmicpc.net/problem/24480)

<div class="notice" markdown="1" style="font-size:12pt;">
<h1 style='margin-top:0em'>Reference</h1>

* [[노마드 코더]개발자라면 꼭 알아야할 Hash Table의 모든 것!](https://youtu.be/HraOg7W3VAM)
* [[Wikidocs]좌충우돌, 파이썬으로 자료구조 구현하기](https://wikidocs.net/193049)

</div>