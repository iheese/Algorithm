```java
class Solution {
		public int solution(int[][] sizes) {
			int answer = 0;
			int maxv = 0;
			int maxh = 0;
			
			for(int i = 0; i< sizes.length;i++){
				int v = Math.max(sizes[i][0],sizes[i][1]); //가로를 무조건 긴 부분
				int h = Math.min(sizes[i][0],sizes[i][1]); //세로는 가장 짧은 부분
				maxv = Math.max(maxv, v); //가로 중에 더 긴 거
				maxh = Math.max(maxh, h); //세로 중에 더 긴 것 (다 포함해야함)
			}
			answer = maxv*maxh;
			return answer;
			
		}
	}
```
