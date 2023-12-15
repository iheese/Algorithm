```java
import java.util.*;
class Solution {
    int[] dx = {1,-1,0,0};
    int[] dy = {0,0,1,-1};
    int xSize, ySize;
        
    public class Moving {
        int x, y, depth;
        
        public Moving(int x, int y, int depth) {
            this.x = x;
            this.y = y;
            this.depth = depth;
        }
    }

    public int solution(String[] board) {
        int answer = 0;
        // 가로를 x축으로, y를 세로축으로 생각하였다.
        xSize = board[0].length();
        ySize = board.length;
        Moving start = null;
        Moving goal = null;
        for(int i = 0; i < xSize ; i++) {
            for(int j = 0 ; j < ySize ; j++) {
                char c = board[j].charAt(i);
                if(c == 'R') {
                    start = new Moving(i, j, 0);
                } else if(c == 'G') {
                    goal = new Moving(i, j, 0);
                }
            }
        }
        answer = bfs(board, start, goal);
        return answer;
    }

    private int bfs(String[] board, Moving start, Moving goal) {
        // bfs 를 위한 큐
        Queue<Moving> q = new LinkedList<>();
        q.add(start);
        // 방문처리도 가로는 x축, y는 세로축
        boolean[][] visited = new boolean[xSize][ySize];
        visited[start.x][start.y] = true;
        
        
        while(!q.isEmpty()) {
            Moving now = q.poll();
            
            if(now.x == goal.x && now.y == goal.y) return now.depth;
            
            for(int i = 0; i < 4 ; i++) {
                int nx = now.x;
                int ny = now.y;
                
                // 범위를 안에 속한 상태에서 벽까지 방향으로 쭉 간다
                while(inRange(nx, ny) && board[ny].charAt(nx) != 'D') {
                    nx += dx[i];
                    ny += dy[i];
                }
                // 하나 빼줘야 범위 벗어나기 전, D 전으로 간다, 이미 D나 범위를 벗어난 상태에서 나오게 됨
                nx -=dx[i];
                ny -=dy[i];
                
                // 방문했거나, 같은 위치일 경우 패스
                if(visited[nx][ny] || (now.x == nx && now.y == ny)) continue;
                // 방문 처리
                visited[nx][ny] = true;
                // 큐에 값을 넣어준다. 
                q.add(new Moving(nx, ny, now.depth+1));
            }
        }
        return -1;
    }

    private boolean inRange(int x, int y) {
        return x >= 0 && y >=0 && x < xSize && y < ySize;
    }
}
```


- bfs, dfs 는 언제나 어렵다.₩
