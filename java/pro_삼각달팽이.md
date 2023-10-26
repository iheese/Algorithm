```java
class Solution {
    public int[] solution(int n) {
        int[][] arr = new int[n][n];
        int total = n*(n+1)/2;
        int[] answer = new int[total];
        
        int x = -1;
        int y = 0;
        int num = 1;
        
        for(int i = 0;i < n; i++) {
            for(int j = i; j < n; j++) {
                if(i % 3 == 0) {
                    x++; // 세로
                } else if (i % 3 == 1) {
                    y++; // 가로
                } else {
                    // 대각선
                    x--;
                    y--;
                }
                arr[x][y] = num++; // n=n+1 에서 ++n은 첫번쨰 n값/n++는 두번쨰 n값 
            }
        }
        
        int idx = 0;
        for (int i = 0; i < arr.length; i++) {
            for(int j=0; j <= i ; j++) {
                answer[idx] = arr[i][j];
                idx++;
            }
        }
        
        return answer;
    }
}
```
