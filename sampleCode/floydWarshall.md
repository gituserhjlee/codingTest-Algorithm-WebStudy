플로이드 워셜-모든 지점에서 다른 모든 지점까지의 최단 경로를 모두 구해야 하는 경우
```python
#2차원 리스트 무한으로 초기화
graph=[[INF]*(n+1) for _ in range(n+1)]

#자기 자신으로 가는 비용은 0
for a in range(1, n+1):
   for b in range(1, n+1):
     if a==b:
      graph[a][b]=0
      
#각 간선 정보 초기화
for _ in range(m):
  a, b , c=map(int, input().split())
  graph[a][b]=c
  
#플로이드 워셜
for k in range(1, n+1):
   for a in range(1, n+1):
    for b in range(1, n+1):
      graph[a][b]=min(graph[a][b], graph[a][k]+graph[k][b])


```
