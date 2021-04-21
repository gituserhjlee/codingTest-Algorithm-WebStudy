dps-깊이 우선 탐색. 모든 노드 방문하는 문제시 쓰인다
동작과정-탐색 시작노드 스택에 삽입후 방문처리-> 스택의 최상단 노드에 방문 안 한 인접 노드 있으면 그 인접노드 스택에 넣고 방문처리
->방문 안 한 인접노드 없다면 스택에서 최상단 노드 pop
->반복
```python
def dfs(graph, v, visited):
#현재 노드 방문
visited[v]=True
print(v, end='')
#인접 노드 재귀적 방문
for i in graph[v]:
   if not visited[i]:
      dfs(graph, i, visited)#방문 안 했다면 재귀적으로 방문 

```
