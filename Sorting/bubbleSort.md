거품정렬- 서로 인접한 두 원소의 대소 비교하고 조건에 안 맞으면 자리 교환
1회전 끝나면 배열 마지막에 가장 큰 원소 위치함 
시간복잡도:O(n^2)
장점:구현간단, 직관적 코드, 제자리 정렬이라 다른 메모리 공간 불필요, 안정정렬
단점:시간복잡도가 비효율적. 교환연산이 많이 일어남 
```java
void bubbleSort(int[] arr){
  int temp=0;
  for(int i=0;i<arr.length;i++){
    for(int j=1;j<arr.length-i;j++){
      if(arr[j-1]>arr[j]){
        temp=arr[j-1];
        arr[j-1]=arr[j]
        arr[j]=temp;
        }
      }
     }
        
