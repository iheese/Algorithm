```
	static class Solution {
		public int[] solution(int[] progresses, int[] speeds) {
			int[] array= new int[speeds.length];
			List<Integer> list = new ArrayList<>();
			for (int i = 0; i < progresses.length; i++) {
				if ((100-progresses[i])%speeds[i] !=0){
					array[i]=(100-progresses[i])/speeds[i]+1;
				}else{
					array[i]=(100-progresses[i])/speeds[i];
				} // 얾마나 걸리는지 array에 넣기!
			}
			int count=1;
			int prev=array[0]; //첫번쨰꺼랑 비교
			for (int i = 1; i < array.length; i++) {
				if(prev<array[i]){ //작으면
					list.add(count); //카운트 바로 넣고
					count=1; //1로 초기화
					prev= array[i]; //prev 바꿔줌
				}else{
					count++; //크면 count 올림
				}
			}
			list.add(count);

			int[] answer = new int[list.size()];
			for (int i = 0; i < list.size(); i++) {
				answer[i]= list.get(i);
			}
			return answer;
		}
	}

	```
