해시-key-value쌍으로 데이터를 저장. 예시 프로그래머스 위장
```python
def solution(clothes):
    closet={}
    for c in clothes:
        key=c[1]
        val=c[0]
        if key in closet:
            closet[key].append(val)
        else:
            closet[key]=[val]
            
    print(closet)  
    result=1
    for i in closet.keys():
        result=result*(len(closet[i])+1)
    return result-1
  ```
