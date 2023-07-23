https://school.programmers.co.kr/learn/courses/30/lessons/12952

```java
class Solution {
    public static int[] board;
    public static int answer = 0;
    public int solution(int n) {
        board = new int[n];
        backtracking(0, n);
        return answer;
    }
    
    public void backtracking(int row, int n){
        if(row == n){
            answer++;
            return;
        }
        for(int i=0; i<n ;i++){
            board[row] = i;//row에 i라는 컬럼값이 들어간다. 
            if(valid(row)){
                backtracking(row+1, n);
            }
        }
    }
    
    public boolean valid(int row){
        for(int i=0;i<row ; i++){
            if(board[i] == board[row])//직선방향
                return false;
            if(Math.abs(row-i) == Math.abs(board[row]-board[i]))//대각선방향
                return false;
        }
        return true;
    }
}

```
