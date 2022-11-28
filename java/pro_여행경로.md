```java
class Solution {
		boolean[] visited;  //방문체크
		ArrayList<String> allRoute; //모든 루트 탐색
		public String[] solution(String[][] tickets) {
			int count=0;
			visited = new boolean[tickets.length];
			allRoute = new ArrayList<>();

			dfs("ICN", "ICN", tickets, count); //ICN에서 시작
			Collections.sort(allRoute); //답들 중 알파벳 순서 제일 빠른 것으로 출력
			String[] answer = allRoute.get(0).split(" ");

			return answer;
		}
		private void dfs(String start, String route, String[][] tickets, int count){
			if(count == tickets.length){ //티켓 끝까지 돌면 루트에 넣기
				allRoute.add(route);
				return;
			}

			for (int i = 0; i < tickets.length; i++) {
				if(start.equals(tickets[i][0]) && !visited[i]){ //방문하지 않았고 시작과 같다면
					visited[i]=true; //방문처리
					dfs(tickets[i][1], route + " " + tickets[i][1], tickets, count+1); //해당 다음이 start가 되고 루트에 계속 더해준다.
					visited[i]=false; //모든 경우를 탐색하기 위해 다시 false
				}
			}
		}
	}
	```
