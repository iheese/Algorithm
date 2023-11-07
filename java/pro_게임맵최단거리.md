```java
// 최단거리는 bfs로 품 > 거리 1, 거리 2, 거리 3 처럼 짧은 순서대로 탐색함
import java.util.*;

class Solution {
    // 4방 탐색
    int[] dx = {0,0,1,-1};
    int[] dy = {-1,1,0,0};
    
    public int solution(int[][] maps) {
        int answer = 0;
	// 방문맵
        int[][] visited = new int[maps.length][maps[0].length];
        visited[0][0] = 1;
        
        bfs(maps, visited);
	// 맵의 구석에 가면 끝
        answer = visited[maps.length-1][maps[0].length - 1];
        
	// 해당 값이 0이면 어차피 못감..ㅠ
        if(answer == 0) {
            answer = -1;
        }
        
        return answer;
    }
    
    // bfs
    private void bfs(int[][] maps, int[][] visited) {
        // 큐 생성
	Queue<int[]> q = new LinkedList<>();
        // 첫번째 노트 삽입
	q.add(new int[]{0,0});
        
	// 비어있을 때까지 반복
        while(!q.isEmpty()) {
            int[] now = q.poll();
            int x = now[0];
            int y = now[1];
            
		// 4방 탐색
            for(int i = 0; i<4; i++) {
                int nx = x + dx[i];
                int ny = y + dy[i];
                
		// 범위를 넘지 않게 범위 검사, 방문하지 않은 값만 탐색, 벽 확인
                if(nx >= 0 && ny >= 0 && nx < maps.length && ny < maps[0].length
                  && visited[nx][ny] == 0 && maps[nx][ny] == 1) {
                    // 방문하하면 전 값에 1 더해서 등록
		    visited[nx][ny] = visited[x][y] + 1;
		    // 큐 삽입
                    q.add(new int[]{nx, ny});
                }
            }
        }
    }
}

```
