```java
class Solution {
		boolean[] visited;
		public int solution(int n, int[][] computers) {
			visited = new boolean[n];
			int answer = 0;
			for (int i = 0; i < computers.length; i++) {
				if(!visited[i]){ //방문하지 않은 노드 나오면 +1
					answer++; 
					dfs(i, computers);
				}
			}
			return answer;
		}
		private void dfs(int start, int[][] computers){
			visited[start]=true; //방문처리
			for(int i =0; i<computers.length; i++){
				if(!visited[i] && computers[start][i]==1){ //방문하지 않았고, 연결되어 있을 때
					dfs(i, computers); //재귀로 네트워크를 연결, 재귀가 끝나면 다시 돌아간다.
				}
			}
		}
	}
	```

```java
class Solution {

    public int solution(int n, int[][] computers) {
        int answer = 0;
        boolean[] visited = new boolean[n];
        
        for(int i = 0; i< n ; i++) {
            if(!visited[i]) {
                dfs(computers, i, visited);
                answer++;
            }
        }
        
        return answer;
    }
    
    private void dfs(int[][] computers, int i, boolean[] visited){
        visited[i] = true;
        
        for (int j = 0; j<computers.length; j++) {
            if(computers[i][j] == 1 && !visited[j]) {
                dfs(computers, j , visited);
            }
        }
    }
}

```
