bfs-너비우선 탐색. 간선 가중치 모두 1인 그래프에서 최단경로 찾기, 임의의경로, 정점과 간선 개수 적을때.dfs보다 빠름
동작방식-탐색 시작노드 큐에 삽입하고 방문처리 ->큐에서 노드 꺼내서 해당 노드의 인접 노드중 방문 안한 노드 모두 큐에 삽입후 방문처리
->반복
```python
from collections import deque

def bfs(graph, start, visited):
  queue=deque([start])
  visited[start]=True #시작노드 방문처리
  while queue:
    v=queue.popleft()
    print(v, end='')
    for i in graph[v]:
      if not visited[i]:
        queue.append(i)
        visited[i]=True

```
