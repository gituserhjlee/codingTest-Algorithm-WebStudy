이진탐색-배열 내부 데이터가 정렬돼 있을때 탐색범위를 절반씩 좁혀가며 데이터 탐색
재귀 이용 or 반복문 이용

재귀 코드
```python 
def binary_search(array, target, start, end):
  if start>end:
    return None
  mid=(start+end)//2
  if array[mid]==target:
    return mid
  elif array[mid]>target:
    return binary_search(array, target, start, mid-1)
  else:
    return binary_search(array, target, mid+1, end)

```

반복문코드(내가 선호하는 방식)
```python 
def binary_search(array, target, start, end):
  while start<=end:
    mid=(start+end)//2
    if array[mid]==target:
      return mid
    elif array[mid]>target:
      end=mid-1
    else:
      start=mid+1
  return None
```
