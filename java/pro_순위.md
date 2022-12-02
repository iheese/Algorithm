```java
class Solution {
		public int solution(int n, int[][] results) {
			int answer = 0;
			int[][] graph = new int[n+1][n+1];

			for (int i = 0; i < results.length; i++) {
				graph[results[i][0]][results[i][1]] = 1; //이긴 경우 1 넣기
			}
			
			// a -> b, b -> c 이면 a -> c인 경우를 간접적으로 찾는 것, 1인 것은 결과 확정인 것을 의미
			for (int i = 0; i <= n; i++) {
				for (int j = 0; j <= n ; j++) {
					for (int k = 0; k <= n; k++) {
						if(graph[j][i]==1 && graph[i][k]==1){
							graph[j][k]=1;
						}
					}
				}
			}
			//2차원 행렬을  돌면서 1인 경우를 더하여 확정된 것을 다 더하면 n-1인 것 갯수를 구한다. 
			for (int i = 1; i <= n ; i++) {
				int game = 0;
				for (int j = 1; j <= n ; j++) {
					if(graph[i][j]==1 || graph[j][i] == 1){
						game++;
					}
				}
				if (game == n-1){
					answer++;
				}
			}
			return answer;
		}
	}
	```
