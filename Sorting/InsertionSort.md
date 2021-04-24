삽입정렬
2번째 원소부터 시작해서 왼쪽 앞 원소들이랑 비교하면서 삽입할 위치 지정하고 원소를 뒤로 옮기고 지정된 자리에 자료 삽입
최선의 경우 O(n)의 빠른 효율성
최악(역정렬) 평균의 경우 O(n^2)
장점:단순, 이미 대부분 정렬시 효율적, 제자리정렬, 안정정렬 , 선택|버블 정렬보다 빠름
단점:평균,최악의 시간복잡도가 비효율적. 배열의 길이가 길어질수록 비효율(버블, 선택도 마찬가지)
```java
void inserionSort(int[] arr){
  for(int index=1; index<arr.length; index++){
    int temp=arr[index];
    int prev=index-1;
    while( (prev>=0) && ( arr[prev]>temp)){
      arr[prev+1]=arr[prev];
      prev--;
     }
     arr[prev+1]=temp;
    }
  }
  ```
