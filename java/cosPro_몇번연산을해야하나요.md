```java
		public int solution(int number, int target) {
		int answer = 0;
		// 연산 횟수에 대한 배열
		int[] visited = new int[10001];
		Queue<Integer> q = new LinkedList<Integer>();
		q.offer(number);
		visited[number] = 1;
		
		// number에서 시작해서 +1, -1. *2 에 대한 값을 큐에 넣고, 빼면서 다시  +1, -1. *2 하여 타겟까지 가는 
		while(!q.isEmpty()) {
			int x = q.poll();

			if(x == target)
				break;
			
			if(x+1 <= 10000 && visited[x+1] == 0) {
				visited[x+1] = visited[x]+1;
				q.offer(x+1);
			}
			if(x-1 >= 0 && visited[x-1] == 0) {
				visited[x-1] = visited[x]+1;
				q.offer(x-1);
			}
			if(2*x <= 10000 && visited[2*x] == 0) {
				visited[2*x] = visited[x]+1;
				q.offer(2*x);
			}
		}

		answer = visited[target]-1;
		return answer;
	}

```
