```
//FrogJmp
class Solution {
		public int solution(int X, int Y, int D) {
			int count=0;
			while(X+(D*count)<Y){
				count++;
			}
			return count;
		}
	}
	
public int solution(int X, int Y, int D) {  
  return (int) Math.ceil((Y - X) / (double) D);
}

```
