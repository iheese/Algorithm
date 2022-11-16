```java
class Solution {
		boolean[] visited;
		int max=0;
		public int solution(int k, int[][] dungeons) {
			visited = new boolean[dungeons.length];
			dfs(k, dungeons, 0);
			return max;
		}
		private void dfs(int tired, int[][] dungeons, int depth){
			//던전을 순회
			for (int i = 0; i < dungeons.length; i++) {
				//방문하지 않았고, 현재 피로도보다 최소필요피로도가 작을 때
				if(!visited[i] && dungeons[i][0] <= tired){
					visited[i] = true; //방문 체크
					dfs(tired-dungeons[i][1], dungeons, depth+1); //함수 재호출, depth 늘려줌
					visited[i]= false; //초기화
				}
			}
			max=Math.max(depth,max);
	}
	}
	```
