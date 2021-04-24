병합정렬-분할정복    
시간복잡도-항상 O(nlogn)   
순차적인 비교로 정렬을 진행해서 LinkedList의 정렬이 필요할때 효율적 (퀵정렬은 임의접근임) 
(LinkedList는 삽입, 삭제연산에서는 유용하고 접근 연산에서는 비효율적임 그래서 퀵소트는 오버헤드가 증가함)   
퀵소트는 우선 피벗통해서 정렬하고 영역을 쪼갬   
병합정렬은 영역을 쪼갤수 있는 만큼 쪼개고 정렬    
```java
public void mergeSort(int[] array, int left, int right){
  if(left<right){
    int mid=(left+right)/2;
    mergeSort(array, left, mid);
    mergeSort(array, mid+1, right);
    merge(array, left, mid, right);
    }
  }
  
  public static void merge(int[] array, int left, int mid, int right){
    int[] L=Arrays.copyOfRange(array, let, mid+1);
    int[] R=Arrays.copyOfRange(array, mid+1, right+1);
    
    int i=0, j=0, k=left;
    int ll=L.length, rl=R.length;
    
    while(i<ll && j<rl){
      if(L[i]<=R[j]){
        array[k]=L[i++];
       }
      else{
        array[k]=R[j++];
       }
       k++;
     }
     while(i<ll){
      array[k++]=L[i++];
     }
     while(j<rl){
      array[k++]=R[j++];
      }
   }
   
        
