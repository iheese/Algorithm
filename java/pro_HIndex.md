```java
import java.util.Arrays;
class Solution {
		public int solution(int[] citations) {
			int answer = 0 ;
			Arrays.sort(citations); //정렬
			for (int j = 0; j < citations.length; j++) {
				int used = citations.length - j ; //최대값부터 내리면서 가장 큰값을 출력한다.

				if( citations [j]>= used){
					answer = used;
					break;
					}
				}

			return answer;
		}
	}
	```
