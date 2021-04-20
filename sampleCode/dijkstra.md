다익스트라 코드- 한 지점에서 다른 특정 지점까지의 최단 경로 구할때 사용 
```python
import heapq

#초기에 노드정보 담는 리스트
graph=[[] for i in range(n+1)]
#최단거리 테이블 무한으로 초기화
distance=[INF]*(n+1)

#간선정보 입력
for _ in range(m):
  a,b,c=map(int, input().split())
  graph[a].append((b,c)) #튜플로 
  
def dijkstra(start):
q=[]
heapq.heappush(q,(0, start))
distance[start]=0
while q:
  dist, now=heapq.heappop(q) #최단경로, 위치
  if distance[now]<dist:
    continue
  for i in graph[now]:
    cost=dist+i[1]
    if cost<distance[i[0]]:
      distance[i[0]]=cost
      heapq.heappush(q, (cost, i[0])
