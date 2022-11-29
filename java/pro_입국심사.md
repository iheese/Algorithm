
```java
import java.util.Arrays;
class Solution {
		public long solution(int n, int[] times) {
			long answer = 0;

			Arrays.sort(times); // 시간 나열
			long start = 1; //최선의 경우
			long end = (long) times[times.length-1] * n; //최악의 경우

			while(start<=end){ // 
				long sum = 0;
				long mid = (start + end )/2; //최선과 최악의 중간 값으로 확인
				for(int time : times){ 
					sum+=mid/time; //중앙 값으로 몇명을 심사할 수 있는지 확인
				}
                //sum은 중간값일때 심사할 수 있는 사람
				if(sum>=n){ //sum이  크면
					end=mid-1; //end값을 하나 뒤로
					answer = mid; //중앙값을 answer로
				}else { //작으면
					start = mid+1; //start가 앞으로
				}
			}

			return answer;
		}
	}
	```
