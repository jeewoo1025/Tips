## BFS
```python
1. Queue에서 꺼내기
2. 목적지인가?
  2-1. 목적지이면 return
3. 연결 노드 순회
  3-1. 갈 수 있는가?
    3-1-1. 방문 체크 O
    3-1-2. Queue에 넣기
```

실제 구현
```python
from collections import deque

def bfs(x,y):
  queue = deque([(x,y)])

  while queue:
    cur_node = queue.popleft()

    if 목적지:
      return

    # 주변 탐색
    for dir in directions:
      # 갈 수 있는가?
      if 갈 수 있는 조건:
        visited[노드] = True
        queue.append(노드)
```

## DFS
```python
1. 목적지인가?
  1-1. 목적지라면 return
2. 연결 노드 순회
  2-1. 갈 수 있는가?
    2-1-1. dfs() 호출
```

실제 구현
```python
# 재귀 함수
def dfs(graph, v, visited):
  visited[v] = True
  for i in graph[v]:
    if not visited[i]:
      dfs(graph,i,visited)

# 스택 구현
def dfs(graph, v, visited):
  stack = [v]
  visited[v]=True

  while stack:
    cur_node = stack.pop()

    for i in graph[v]:
      if not visited[i]:
        visited[cur_node] = True
        stack.append(i)
```

## 백트래킹
- 해를 찾는 도중 막히면 되돌아가서 다시 해를 찾는 기법
- 특징
    - 어떤 노드에서 출발하는 경로가 그 해결책으로 이어질 것 같지 않으면 더이상 경로를 탐색하지 않음으로써 시도 횟수 감소
    - 불필요한 경로의 조기 차단
```python
def 백트래킹(n):
  if 정답이면:
    출력 or 저장
  else:
    for 모든 자식 노드에 대해
      if promising(m):   # 유망한지 확인
        자식노드로 이동
        백트래킹(n+1)
        부모 노드로 이동

def promising(m):
  if 조건에 안 맞으면:
    return False
  return True
```
