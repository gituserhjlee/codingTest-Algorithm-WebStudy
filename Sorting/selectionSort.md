배열중 최소값을 맨앞 위치한 값과 교체- 처음위치 뺴고 반복
맨처음위치에 정렬된 값이 쌓이게됨 
시간복잡도:O(n^2)
장점:단순, 버블소트에 비해서 실제 교환횟수는 적음 . 제자리정렬(정렬하려는 배열안에서 교환)이라 다른 메모리 공간 불필요
단점:시간복잡도 비효율적, 불안정정렬
(안정정렬-동일한 값에 대해 기존의 순서가 유지. 불안정정렬은 기존의 순서가 뒤바뀔수있음)


```java
  void selectionSort(int[] arr){
    int indexMin, temp;
    for(int i=0;i<arr.length-1;i++){
      indexMin=i;
      for(int j=i+1;j<arr.length;j++){
        if(arr[j]<arr[indexMin]){
          indexMin=j;
          }
         }
         temp=arr[indexMin];
         arr[indexMin]=arr[i];
         arr[i]=temp;
     } 
   }
