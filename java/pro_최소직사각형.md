```java
class Solution {
		public int solution(int[][] sizes) {
			int answer = 0;
            int maxh = 0;
            int maxw = 0;
     
            for(int[] size : sizes) {
                int w = Math.max(size[0], size[1]);
                int h = Math.min(size[0], size[1]);
                
                maxw = Math.max(maxw, w);
                maxh = Math.max(maxh, h);         
            }
            
            
            answer = maxh * maxw;
			return answer;
			
		}
	}
```
