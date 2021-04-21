크루스칼 알고리즘-가장 적은 비용으로 모든 노드를 연결 
모든 간선을 정렬하고 가장 거리가 짧은 간선부터 집합에 포함시키되 사이클 발생시키는 간선은 포함 안 시키기 
최소신장 트리이므로 최종적으로 신장 트리에 포함되는 간선의 개수는 노드개수-1임 
```python
#프로그래머스 섬연결하기의 정답 코드 
def solution(n, costs):
    answer = 0
    costs.sort(key=lambda x:x[2]) #모든 간선을 정렬
    routes=set([costs[0][0]]) #집합
    while len(routes)!=n:
        for i, cost in enumerate(costs):
            if cost[0] in routes and cost[1] in routes:#사이클을 발생
                continue
            if cost[0] in routes or cost[1] in routes:
                routes.update([cost[0],cost[1]])#set에서 update는 []속의 여러 요소를 더할때 쓴다 
                answer+=cost[2]
                costs[i]=[-1,-1,-1]
                break
    return answer

```
