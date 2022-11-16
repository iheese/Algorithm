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
