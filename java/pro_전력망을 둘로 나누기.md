```java
class Solution {
		public List<Integer>[] list;
		public int solution(int n, int[][] wires) {
			int answer = 100;

			list = new List[n+1];
			for (int i = 0; i <= n  ; i++) {
				list[i] = new ArrayList<>();
			}

			for(int[] wire : wires){
				list[wire[0]].add(wire[1]);
				list[wire[1]].add(wire[0]);
			}

			for(int[] wire : wires){
				int n1 = bfs(wire[0], wire[1], n); //한쪽 방향 
				int n2 = bfs(wire[1], wire[0], n); //반대편 방향

				answer = Math.min(answer, Math.abs(n1-n2));
			}

			return answer;
		}

		//bfs
		public int bfs(int v1, int v2, int n){
			//큐 생성
			Queue<Integer> queue = new LinkedList<>();
			boolean[] visited = new boolean[n+1];
			int count=0;

			queue.add(v1); //큐에 시작 노드 넣어줌
			visited[v1] = true; //방문확인

			//큐가 빌 때까지 반복
			while(!queue.isEmpty()){

				int now =  queue.poll(); //하나를 꺼내고
				count++; //횟수를 더한다.

				for(int next : list[now]){ //시작점의 리스트를 순회하면서
					if(next != v2 && !visited[next]){ //방문하지 않았거나, 간선을 끊어서 처리
						queue.add(next);
						visited[next]=true;
					}
				}
			}
			return count;
		}
	}
```

```java
import java.util.*; 
class Solution {
    int[][] arr;
	public int solution(int n, int[][] wires) {
        int answer = n;
        arr = new int[n+1][n+1];
        
        // 인접행렬 생성
        for(int i = 0; i < wires.length; i++) {
            arr[wires[i][0]][wires[i][1]] = 1;
            arr[wires[i][1]][wires[i][0]] = 1;
        }
        
        int a,b;
        for(int i = 0; i < wires.length ; i++) {
            a = wires[i][0];
            b = wires[i][1];
            
            // 선 끊기
            arr[a][b] = 0;
            arr[b][a] = 0;
            
            // 선 차이 최솟값 갱신
            answer = Math.min(answer, bfs(a, n));
            
            // 선 다시 연결
            arr[a][b] = 1;
            arr[b][a] = 1;
        }
        return answer;
    }
		
    //bfs
	private int bfs(int start, int n){
	    boolean[] visited = new boolean[n+1];
        int count = 1;
        // 큐 생성, 시작값 넣기
        Queue<Integer> q = new LinkedList<>();
        q.add(start);
        
        while(!q.isEmpty()) {
            int next = q.poll();
            visited[next] = true;
            
            for(int i = 1 ; i <= n ; i++) {
                if(visited[i]) continue; // 이미 확인했으면 다음 반복으로
                if(arr[next][i] == 1) {
                    q.add(i);
                    count++;
                }
            }
        }
        return (int) Math.abs(count - (n-count));
	}
}

```

