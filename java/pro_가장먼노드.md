```java
Solution {
		boolean[] visited;
		ArrayList<ArrayList<Integer>> graph = new ArrayList<>();
		int[] distance;
		public int solution(int n, int[][] edge) {
			visited = new boolean[n+1];
			distance = new int[n + 1];
			int answer=0;

			for (int i = 0; i <= n; i++) {
				graph.add(i, new ArrayList<>()); //각 객체에 초기화
			}
			for (int i = 0; i < edge.length; i++) {
				graph.get(edge[i][0]).add(edge[i][1]); // 인접 그래프 만들어주기
				graph.get(edge[i][1]).add(edge[i][0]);
			}

			visited[1] = true;
			Queue<Integer> queue = new LinkedList<>();

			queue.add(1);
			while(!queue.isEmpty()){//bfs 시작
				int now = queue.poll(); //하나 뺴고
				for(int i : graph.get(now)){ //해당 연결된 것 순회
					if(!visited[i]){ //방문하지 않았다면
						queue.add(i); //큐에 넣고
						visited[i]=true; //방문 처리
						distance[i] = distance[now]+1; //해당 인덱스 거리는 현재에서 하나 더한 값
					}
				}
			}
			Arrays.sort(distance); //오름차순 절렬
			int max = distance[distance.length-1]; //제일  먼 값이 일치할 때 갯수 구하기
			for(int i = distance.length-1; distance[i]==max ;i--){
				answer++;
			}

			return answer;
		}
	}
	```
