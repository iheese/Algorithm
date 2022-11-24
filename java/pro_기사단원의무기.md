```java
import java.util.ArrayList;
import java.util.List;

	class Solution {
		public int solution(int number, int limit, int power) {
			int answer = 0;
			List<Integer> list = new ArrayList<>();
			for (int i = 1; i <=number ; i++) {
				int count=0;
				for (int j = 1; j <= Math.sqrt(i); j++) {
					if(i%j==0){
						count++; //시간 초과 때문에 전체를 조회하지 않고 제곱근까지 조회
					}
				}
				if(Math.sqrt(i)%1==0){ //제곱근이 딱 나누어 떨어지는 정수 16, 4 등..
					list.add(count*2-1); //*2하고 1개를 빼준다.
				}else{
					list.add(count*2); //나머지는 *2
				}
				
			}
			for(int i : list){
				if(i>limit){
					answer+=power; //리밋보다 크면 파워를 더해주고
				}else{
					answer+= i; //나머지는 그냥 더해준다.
				}
			}

			return answer;
		}
	}
	```
