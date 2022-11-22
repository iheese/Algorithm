```java
class Solution {
		int answer=0;
		public int solution(int[] numbers, int target) {
			dfs(target, numbers, 0, 0);
			return answer;
		}
		private void dfs(int target, int[] numbers, int depth, int sum){
				if(depth == numbers.length){ //depth가 끝까지 간 경우
					if(target==sum){ //타겟값과 같으면 값에 더하기
						answer++;
					}
				}else { //아니면 해당 값 + or - 하고 다음 깊이로 넘어간다.
					dfs(target, numbers, depth+1, sum+numbers[depth]);
					dfs(target, numbers, depth+1, sum-numbers[depth]);
				}
			}
		
	}
	```
