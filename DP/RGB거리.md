백준 실버1 1149 다이나믹프로그래밍   
현재 집이 빨강, 초록, 파랑인 경우를 각각 앞의 집이 가능한 색+지금 집의 색을 계산 하면 마지막 집이 빨강,초록,파랑인 경우가 계산되고 그중 최솟값을 출력   
```python
n=int(input())#집의수
house=[]
for i in range(n):
    house.append(list(map(int, input().split())))
for i in range(1, n):
    house[i][0]=min(house[i-1][1],house[i-1][2])+house[i][0]
    house[i][1]=min(house[i-1][0],house[i-1][2])+house[i][1]
    house[i][2]=min(house[i-1][0],house[i-1][1])+house[i][2]
print(min(house[n-1]))

```
