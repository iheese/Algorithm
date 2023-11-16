```java
import java.util.*;
class Solution {
    int sum;
    boolean[][] visited;
    public int[] solution(String[] maps) {
        List<Integer> list = new ArrayList<>();
        sum = 0;
	// 방문 확인
        visited = new boolean[maps.length][maps[0].length()];
        
	// 이중 for 문으로 확인
        for(int i = 0; i<maps.length ; i++) {
            for(int j = 0; j < maps[0].length(); j++) {
                dfs(maps, visited, i, j);
                // dfs 다 돌고 리스트에 넣고 sum 초기화
		if(sum > 0) {
                    list.add(sum);
                    sum = 0;
                }
            }
        }
        
        if(list.size() == 0) return new int[]{-1};
        
        int[] answer = new int[list.size()];
        
        for(int i=0; i <answer.length; i++) {
            answer[i] = list.get(i);
        }
        
        Arrays.sort(answer);
        
        return answer;
    }
    // 	dfs 메소드
    private void dfs(String[] maps, boolean[][] visited, int i, int j) {
        // 범위 벗어나면 나가기
	if(i<0 || j<0 || i >= maps.length || j>= maps[0].length()){
            return;
        }
        // X는 바다, 방문했다면 넘어가기
        if(maps[i].charAt(j) == 'X' || visited[i][j]) {
            return;
	// 아니면 방문 처리하고 값 더하기
        } else {
            visited[i][j] = true;
            sum+=maps[i].charAt(j) - '0';
        }
	// 4방면으로 이동하기
        dfs(maps, visited, i+1, j);
        dfs(maps, visited, i-1, j);
        dfs(maps, visited, i, j+1);
        dfs(maps, visited, i, j-1);
    }
}

```
