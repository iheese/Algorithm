```java
import java.util.*;
class Solution {
    int[] dx = {1, -1, 0, 0};
    int[] dy = {0, 0, 1, -1};
    
    public int solution(String[] maps) {
        int answer = 0;
        // 가로는 x축, 세로는 y축이라 생각했다.
        int[][] visited = new int[maps[0].length()][maps.length];
        
        int[] start = new int[2];
        int[] lever = new int[2];
        int[] exit = new int[2];
        // 시작점, 레버, 도착점 찾아주기
        for(int i = 0 ; i < maps[0].length(); i++) {
            for(int j = 0 ; j < maps.length; j++) {
                if(maps[j].charAt(i) == 'S') {
                    start[0] = i;
                    start[1] = j;
                }
                if(maps[j].charAt(i) == 'L') {
                    lever[0] = i;
                    lever[1] = j;
                }
                if(maps[j].charAt(i) == 'E') {
                    exit[0] = i;
                    exit[1] = j;
                }
            }
        }
        
        // bfs, 시작점에서 레버까지 빠른 길
        int toLevel = bfs(start, lever, maps, visited);
        // 다시 초기화
        visited = new int[maps[0].length()][maps.length];
        // 레버에서 도착점까지 빠른 길
        int toExit = bfs(lever, exit, maps, visited);
        
        // 하나라도 불가능하면 불가능
        return toLevel == -1 || toExit == -1 ? -1 : toLevel + toExit;
    }
    
    // bfs
    private int bfs(int[] start, int[] goal, String[] maps, int[][] visited) {
        Queue<int[]> q = new LinkedList<>();
        q.add(start);
        
        while(!q.isEmpty()) {
            int[] now = q.poll();
                       
            int x = now[0];
            int y = now[1];
            
            if(x == goal[0] && y == goal[1]) {
                return visited[x][y];
            }
            
            for(int i = 0 ; i < 4; i++) {
                int nx = x + dx[i];
                int ny = y + dy[i];
                
                if(nx >= 0 && nx < maps[0].length() && ny >= 0 && ny < maps.length
                  && visited[nx][ny] == 0 && (maps[ny].charAt(nx) != 'X')) {
                    visited[nx][ny] = visited[x][y] + 1;
                    q.add(new int[]{nx, ny});
                }
            }
        }
        return -1;
    }
}

```

- 이걸 풀어내다니.. 뿌듯..!

```java
import java.util.LinkedList;
import java.util.Queue;

class Solution {
    static String[][] MIRO;
    static int[] dx = {-1, 1, 0, 0};
    static int[] dy = {0, 0 , -1, 1};
    
    public int solution(String[] maps) {
        MIRO = new String[maps.length][maps[0].length()];
        int[] start = new int[2];
        int[] labor = new int[2];
        
        for(int i = 0; i<maps.length; i++) {
            String[] tmp = maps[i].split("");
            
            for(int j = 0; j<tmp.length; j++) {
                MIRO[i][j] = tmp[j];
                
                if (MIRO[i][j].equals("S")) {
                    start = new int[]{i, j};
                }
    
                if (MIRO[i][j].equals("L")) {
                    labor = new int[]{i, j};
                }
            }
        }
        
        int result = bfs(start, "L");
        int result2 = bfs(labor, "E");
        
        if (result == -1 || result2 == -1)
            return -1;
        
        return result + result2;
    }
    
    public int bfs(int[] start, String target) {
        Queue<int[]> queue = new LinkedList<>();
        queue.add(new int[]{start[0], start[1], 0});
        
        boolean[][] visited = new boolean[MIRO.length][MIRO[0].length];
    
        while(!queue.isEmpty()) {
            int x = queue.peek()[0];
            int y = queue.peek()[1];
            int count = queue.peek()[2];
            visited[x][y] = true;
            
            if (MIRO[x][y].equals(target)) {
                return count;
            }
            
            queue.poll();
        
            for(int i = 0; i<4; i++) {
                int nx = x + dx[i];
                int ny = y + dy[i];
            
                if (nx >= 0 && nx < MIRO.length && ny >= 0 && ny < MIRO[0].length && !visited[nx][ny]) {
                    if (!MIRO[nx][ny].equals("X")) {
                        visited[nx][ny] = true;
                        queue.add(new int[]{nx, ny, count+1});
                    }
                }
            }
        }
        
        return -1;
    }
}
//출처: https://chamggae.tistory.com/199 [suhaha 개발 일지:티스토리]
```

- bfs 안에 방문 체크하는 객체를 넣어서 만들기도 한다. 
