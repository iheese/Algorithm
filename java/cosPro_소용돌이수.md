```java
 public int solution(int n) {
      int[][] arr = new int[n][n];	
			int i = 0;
			int j = 0;
			int num = 1;
			int col = n;
			int row = n -1;
			
			while(num <= n*n) {
				for(int k = 0; k < col; k++) {
					arr[i][j] = num;
					j++;
					num++;
				}
				col--;
				i++;
				j--; // 인덱스 맞춰주기
				
				for(int k = 0 ; k < row ; k++) {
					arr[i][j] = num;
					i++;
					num++;
				}
				row--;
				i--;
				j--;
				
				for(int k = 0; k < col ; k++) {
					arr[i][j] = num;
					j--;
					num++;
				}
				col--;
				i--;
				j++;
				
				for(int k = 0; k< row; k++) {
					arr[i][j] = num;
					i--;
					num++;
				}
				
				row--;
				i++;
				j++;
			}	
							
      int answer = 0;
			for(int k = 0 ; k < n ; k++) {
				answer+=arr[k][k];
			}

      return answer;
    }
```
