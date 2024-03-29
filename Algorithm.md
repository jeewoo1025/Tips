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
<br>

## sorted 우선순위
- 우선순위가 높은 순서대로 정렬 예시
```python
# 아기상어 16236번

....
  tmp.append((nx,ny,distance[nx][ny]))   # 거리 
....

# 우선순위: 거리가 가까운 물고기 > 가장 위에 있는 물고기 > 가장 왼쪽에 있는 물고기
tmp = sorted(tmp, key=lambda x:(-x[2], -x[0], -x[1]))
```
<br>

## 마이너스를 % 계산하면?
- 양수임
- 백준 23290번 마법사 상어와 복제 문제에서 방향 움직일때 사용하
```python
cnt = -2
cnt %= 8
cnt = 2

# 방향 8가지 이어져 있음
for i in range(d, d-8, -1):
  i %= 8
```
<br>

### 시계방향으로 90도 / 180도 / 270도 회전
```python
def rotate_90():
    global arr, N
    ret = [[0]*N for _ in range(N)]
    for r in range(N):
        for c in range(N):
            ret[c][N-1-r] = arr[r][c]
    return ret

def rotate_180():
    global arr, N
    ret = [[0]*N for _ in range(N)]
    for r in range(N):
        for c in range(N):
            ret[N-1-r][N-1-c] = arr[r][c]
    return ret

def rotate_270():   # -90도랑 동일함
    global arr, N
    ret = [[0]*N for _ in range(N)]
    for r in range(N):
        for c in range(N):
            ret[N-1-c][r] = arr[r][c]
    return ret
```
<br>

### 다익스트라
- 특징: 최단 경로를 구하는 과정에서 '각 노드에 대한 현재까지의 최단거리' 정보를 항상 1차원 리스트에 저장하며 리스트를 계속 갱신한다는 특징이 있음
- 현재 가장 가까운 노드를 저장하기 위해 우선순위 큐를 사용함
```python
1. 출발노드를 설정
2. 최단거리 테이블 초기화
3. 방문하지 않은 노드 중 최단 거리가 가장 짧은 노드를 선택함
4. 해당 노드를 거쳐 다른 노드로 가는 비용을 계산하여 최단거리 테이블을 갱신함
5. 3~4번 반복
```
<br>

```python
import heapq
INF = int(1e9)
distance = [INF]*(N+1)    # 최단거리 테이블

# 모든 간선 정보 입력받기
for _ in range(m):
  a, b, c = map(int, input().split())
  # a번 노드에서 b번 노드로 가는 비용이 c라는 의미
  graph[a].append((b,c))


def dijkstra(start):
  q = []

  # 시작 노드로 가기 위한 최단경로는 0으로 설정하여 큐에 삽입
  heapq.heappush(q, (0, start))   # (거리, 노드) 삽입
  distance[start] = 0
  while q:
    # 가장 최단거리가 짧은 노드에 대한 정보 꺼내기
    dist, now = heapq.heappop(q)

    # 현재 노드가 이미 처리된 적이 있는 노드라면 무시
    if distance[now] < dist:
      continue
    # 현재 노드와 연결된 다른 입접한 노드들을 확인
    for i in graph[now]:
      cost = dist + i[1]
      if cost < distance[i[0]]:
        distance[i[0]] = cost
        heapq.heappush(q, (cost, i[0]))
```
