```python
from collections import deque
def dfs(v,visited,graph):
    
    visited[v]=1
    print(v, end=' ')
    for i in graph[v]:
        if visited[i]==0:
            dfs(i,visited,graph)
    
    
def bfs(v,visited,graph):
    q=deque([v])
    visited[v]=1
    while q:
        v=q.popleft()
        print(v, end=' ')
        for i in graph[v]:
            if visited[i]==0:
                q.append(i)
                visited[i]=1
                
n, m,v=map(int, input().split())
graph=[[] for _ in range(n+1)]
for i in range(m):
    a, b=map(int, input().split())
    graph[a].append(b)
    graph[b].append(a)
for i in graph:
    i.sort()
visited=[0]*(n+1)
dfs(v,visited,graph)
print()
visited=[0]*(n+1)
bfs(v,visited,graph)
```
