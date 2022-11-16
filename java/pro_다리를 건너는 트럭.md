```
import java.util.*;
static class Solution {
		public int solution(int bridge_length, int weight, int[] truck_weights) {
			Queue<Integer> queue = new LinkedList<>(); //큐 이용 (다리라고 생각)
			int time = 0; //시간
			int sum = 0; //다리 위에 올라간 트럭 무게 합
			for (int t : truck_weights) {  //모든 트럭이 통과해야한다.
				while(true){ //반복문 계속 돌린다.
					if(queue.isEmpty()){  //다리가 비워져 있을 때
						queue.add(t); // 첫번째 트럭을 올려주고
						sum+=t;  //트럭 무게 합 더해주고
						time++; //시간 1초 지나감
						break; //다음 트럭!
					}else if(queue.size() == bridge_length){ //다리에 트럭이 가득 찼을 때
						sum-=queue.poll();  //queue에서도 빼주고 다리가 버틸 수 있는 무게도 빼준다.
					}else{ //다리가 다 차지는 않았을 때는 무게를 고려해줘야 한다.
						if(sum + t<=weight){  // 하나 더 올라가도 버틸 수 있으면
							queue.add(t); //올리고
							sum+=t; //트럭 무게 합 더해주고
							time++; //1초 지나감
							break; //다음 트럭
						}else{
							queue.add(0); // 넘었다면 0을 넣고 기다려준다.
							time++;
						}
					}
				}
			}
			return time+bridge_length; //마지막도 나갈 수 있게 기다린다.
		}
	}

	```
