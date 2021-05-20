2단계   
capitalize는 앞글자만 대문자로 바꾼다.   
.upper(), .lower() 함수도 있다. 
```python
def solution(s):
    arr=s.split(' ')
    answer=' '
    for i in range(len(arr)):
        arr[i]=arr[i].capitalize()
        
      
    return answer.join(arr)
 ```
 
 or
 
 ```python
 def solution(s):
    arr=s.split(' ')
    answer=''
    for i in arr:
        i=i.capitalize()
        answer+=str(i)+str(' ')
      
    return answer[:-1]
 ```
