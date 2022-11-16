	```java
	class Solution {
		int[] findParent;

		//부모 찾기
		public int find(int child){
			if(findParent[child] == child){
				return child;
			}else{
				return findParent[child] = find(findParent[child]);
			}
		}

		public int solution(int n, int[][] costs) {

			//가중치 기준으로 오름차순
			Arrays.sort(costs, (o1, o2) -> {
				Integer a = o1[2];
				Integer b = o2[2];
				return a.compareTo(b);
			});

			//초기 배열애서 부모는 자기 자신
			findParent = new int[n];
			for (int i = 0; i < n; i++) {
				findParent[i]=i;
			}

			//부모가 같지 않다면 연결이 안된 최솟값이므로 연결
			int answer = 0;
			for (int i = 0; i < costs.length; i++) {
				int firstIsland = find(costs[i][0]);
				int secondIsland = find(costs[i][1]);
				if(firstIsland != secondIsland){
					findParent[secondIsland] = firstIsland;
					answer+=costs[i][2];
				}
			}

			return answer;
		}
	}
	```
