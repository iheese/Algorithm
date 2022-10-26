	```java
	import java.util.*;
	class Solution {
		public int solution(int[] priorities, int location) {
			//우선순위 큐, 디폴트는 오름차순, 내림차순으로 바꿔주었다.
			PriorityQueue<Integer> pq = new PriorityQueue<>(Collections.reverseOrder());

			for(int i : priorities){
				pq.add(i);  //내림차순 큐에 넣어준다.
			}
			int answer = 0;

			while(!pq.isEmpty()) {  //내림차순 큐가 빌 때까지 반복
				for (int i = 0; i < priorities.length; i++) {
					if(pq.peek() == priorities[i]){  //제일 큰 값과 우선순위 배열의 값이 같다면
						pq.poll(); //제일 큰 값을 빼고 
						answer++;  //그 값의 순서는 1번이 된다. 

						if(location == i){ //찾고자 하는 location과 같다면 리턴 아니면  패스
							return answer;
						}
					}
				}
			}
			return  answer;
		}
		```
