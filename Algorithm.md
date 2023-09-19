## BFS
- 최단거리 구하는 문제면 BFS 수행
- 이유: BFS는 현재 노드에서 가까운 곳부터 찾기 때문에 경로를 탐색 시 먼저 찾아지는 해답이 곧 최단거리임.
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
<br>

## zip으로 행렬 뒤지기
```python
def rotate(M, dir='left'):
  if dir=='left': # left 90 degree rotate
    out = list(reversed(list(map(list, zip(*M)))))
  elif dir=='right':   # right 90 degree rorate
    out = list(map(list, zip(*reversed(M))))
  elif dir=='transpose':
    out = list(map(list, zip(*M)))
  return out

M = [[1,2,3,4],[5,6,7,8]]

print(rotate(M,dir='left'))  # [[4,8],[3,7],[2,6],[1,5]]
print(rotate(M,dir='right')) # [[5,1],[6,2],[7,3],[8,4]]
print(rotate(M,dir='transpose'))  # [[1,5],[2,6],[3,7],[4,8]]
```
<br>

## 2차원 => 1차원 리스트 변환
1. sum()
```python
list1 = [[1, 10], [2, 22], [3, 19], [4, 7]]
list2 = sum(list1, [])
print(list2)  # [1, 10, 2, 22, 3, 19, 4, 7]
```

2. itertools
```python
import itertools

list1 = [[1, 10], [2, 22], [3, 19], [4, 7]]
list2 = list(itertools.chain(*list1))
print(list2)  # [1, 10, 2, 22, 3, 19, 4, 7]
```

