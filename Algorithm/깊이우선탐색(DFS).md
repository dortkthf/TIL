# 깊이우선탐색 (DFS)

# 1.그래프 탐색 알고리즘

데이터 구조는 알고리즘의 재료가 되어 문제를 해결하는데 사용된다.

그래프 자료구조는 탐색 알고리즘에 활용된다!

![image-20220820163938694](깊이우선탐색(DFS).assets/image-20220820163938694.png)

그래프 탐색 알고리즘이란?

시작 정점에서 간선을 타고 이동할 수 있는 모든 정점을 찾는 알고리즘

![image-20220820164019773](깊이우선탐색(DFS).assets/image-20220820164019773.png)

그래프 탐색 알고리즘에는 깊이우선탐색과 너비우선탐색이 있다.

이전에 학습했던 스택과 큐 자료구조의 개념을 함께 활용한다.

![image-20220820164107794](깊이우선탐색(DFS).assets/image-20220820164107794.png)

![image-20220820164118729](깊이우선탐색(DFS).assets/image-20220820164118729.png)

![image-20220820164126515](깊이우선탐색(DFS).assets/image-20220820164126515.png)

![image-20220820164228979](깊이우선탐색(DFS).assets/image-20220820164228979.png)

![image-20220820164244312](깊이우선탐색(DFS).assets/image-20220820164244312.png)

# 2. 깊이우선탐색(DFS)

시작 정점으로부터 갈 수 있는 하위 정점까지 가장 깊게 탐색하고,

더 이상 갈 곳이 없다면 마지막 갈림길로 돌아와서 다른 정점을 탐색하며 결국 모든 정점을 방문하는 순회방법

![image-20220820164359688](깊이우선탐색(DFS).assets/image-20220820164359688.png)

### 깊이우선탐색(DFS)의 특징

모든 정점을 방문할 때 유리하다. 따라서 경우의 수, 순영과 조합 문제에서 많이 사용한다.

너비우선탐색(BFS)에 비해 코드 구현이 간단하다.

단, 모든 정점을 방문할 필요가 없거나 최단 거리를 구하는 경우에는 너비우선탐색(BFS)이 유리하다.

# 3. DFS의 동작 과정

DFS를 하기 전에, 일단 탐색을 진행할 그래프가 필요하다.

그래프는 인접 행렬 혹은 인접 리스트 방식으로 표현할 수 있다.

![image-20220820164547035](깊이우선탐색(DFS).assets/image-20220820164547035.png)

각 정점을 방문했는지 여부를 판별할  방문 체크 리스트가 필요하다.

사람과 달리 컴퓨터는 각 정점에 방문했는지 여부를 알 수 없다.

따라서 visited 리스트를 따로 선언하여 각 정점을 방문했는지 체크한다.

![image-20220820164717273](깊이우선탐색(DFS).assets/image-20220820164717273.png)

![image-20220820164732646](깊이우선탐색(DFS).assets/image-20220820164732646.png)

![image-20220820164753770](깊이우선탐색(DFS).assets/image-20220820164753770.png)

![image-20220820164801433](깊이우선탐색(DFS).assets/image-20220820164801433.png)

![image-20220820164808858](깊이우선탐색(DFS).assets/image-20220820164808858.png)

![image-20220820164818091](깊이우선탐색(DFS).assets/image-20220820164818091.png)

![image-20220820164828776](깊이우선탐색(DFS).assets/image-20220820164828776.png)

![image-20220820164835440](깊이우선탐색(DFS).assets/image-20220820164835440.png)

![image-20220820164844543](깊이우선탐색(DFS).assets/image-20220820164844543.png)

![image-20220820164911002](깊이우선탐색(DFS).assets/image-20220820164911002.png)

![image-20220820164918107](깊이우선탐색(DFS).assets/image-20220820164918107.png)

![image-20220820164923863](깊이우선탐색(DFS).assets/image-20220820164923863.png)

![image-20220820164933286](깊이우선탐색(DFS).assets/image-20220820164933286.png)

![image-20220820164941040](깊이우선탐색(DFS).assets/image-20220820164941040.png)

![image-20220820164948759](깊이우선탐색(DFS).assets/image-20220820164948759.png)

![image-20220820164955058](깊이우선탐색(DFS).assets/image-20220820164955058.png)

![image-20220820165002909](깊이우선탐색(DFS).assets/image-20220820165002909.png)

![image-20220820165010880](깊이우선탐색(DFS).assets/image-20220820165010880.png)

![image-20220820165019881](깊이우선탐색(DFS).assets/image-20220820165019881.png)

![image-20220820165039866](깊이우선탐색(DFS).assets/image-20220820165039866.png)

![image-20220820165048353](깊이우선탐색(DFS).assets/image-20220820165048353.png)

![image-20220820165054951](깊이우선탐색(DFS).assets/image-20220820165054951.png)

![image-20220820165103396](깊이우선탐색(DFS).assets/image-20220820165103396.png)

![image-20220820165116381](깊이우선탐색(DFS).assets/image-20220820165116381.png)

![image-20220820165125491](깊이우선탐색(DFS).assets/image-20220820165125491.png)

# 4. DFS의 구현 방식

지금까지 살펴본 DFS를 코드로 구현해보자.

여기에서는 인접 리스트로 표현한 그래프를 가준으로 설명한다.

![image-20220820165316078](깊이우선탐색(DFS).assets/image-20220820165316078.png)

반복문을 이용한 DFS

DFS는 직전에 방문한 정점으로 차례로 돌아가야 하므로, 후입선출(LIFO)구조의 스택을 사용한다.

```python
graph = [
    [1,2],
    [0,3,4],
    [0,4,5],
    [1],
    [1,2,6],
    [2],
    [4]
]

visited = [False]*n   방문 처리 리스트 만들기

def dfs(start):
    stack = [start] 돌아갈 곳을 기록
    visited[start] = True 시작 정점 방문 처리
    
    while stack: 스택이 빌 때까지(돌아갈 곳이 없을때까지) 반복
        cur = stack.pop() 현재 방문 정점(후입선출)
        
        for adj in graph[cur]: 인접한 모든 정점에 대해
    		if not visited[adj]: 아직 방문하지 않았다면
                visited[adj] = True 방문처리
                stack.append(adj) 스택에 넣기
                
dfs(0) 0번 정점에서 시작
```



# 5. DFS 문제 풀이

![image-20220821233435542](깊이우선탐색(DFS).assets/image-20220821233435542.png)

```python
n = int(input()) 정점 개수
m = int(input()) 간선 개수
graph = [[] for _ in range(n+1)]
visited = [Fasle]*(n+1)
total = 0

인접 리스트 만들기
for _ in range(m)
	v1,v2 = map(int,input().split())
    graph[v1].append(v2)
    graph[v2].append(v1)
    
def dfs(start):
    stack = [start]
    visited[start] = True
    
    while stack:
        cur = stack.pop()
        
        for adj in graph[cur]:
            if not visited[adj]:
                visited[adj] = True
                stack.append(adj)
                
dfs(1) 1번 정점에서 시작
```

