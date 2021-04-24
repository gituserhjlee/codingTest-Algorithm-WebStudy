퀵 정렬-분할정복
불안정 정렬. 비교정렬. 배열을 비균등하게 분할
평균적으로 가장 빠르고 자바 Array.sort()도 내부적으로 퀵소트임 

동작:
배열중 피벗을 고름. 
피벗앞은 피벗보다 작은 값, 피벗뒤는 피벗보다 큰 값 오도록 둘로 나눔(분할)+부분배열을 정렬하는 (정복).
분할 끝나면 피벗은 더이상 안움직임
분할된 두 배열에 대해 재귀적으로 반복
재귀 한번 진행될때마다 최소 한 원소는 최종적으로 위치 정해짐 

배열이 오름,내림차순 정렬 돼있으면 시간복잡도 O(n^2)
최선의 경우 O(nlog2n)
장점: 시간복잡도가 빠르다. 제자리정렬
단점:불안정정렬. 정렬된 배열에 대해서는 불균형 분할이라 오히려 수행시간 많이걸림 

정복
```java
public void quickSort(int[] array, int left, int right){
  if(left>=right) return;
  
  //분할
  int pivot=partition(array, left, right);
  
  //피벗제외 2개 부분 배열대상 순환 호출
  quickSort(array, left, pivot-1);//정복
  quickSort(array, pivot+1, right);//정복
 }
 ```
 분할
 ```java
 public int partition(int [] array, int left, int right){
  int pivot=array[left]; //가장 왼쪽값을 피벗으로
  int i=left, j =right;
  while(i<j){
    while(pivot<array[i]){
      j--;
     }
     while(i<j && pivot>=array[i]{
      i++;
      }
      swap(array, i, j);
     }
  array[left]=array[i];
  array[i]=pivot;
  
  return i;
  }
  ```
 
 
 
 
 
 
 
 
 
