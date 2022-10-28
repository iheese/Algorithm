```java
	class Solution {
		public int[] solution(int[] prices) {
			int[] answer = new int[prices.length];

			for(int i= 0 ; i< prices.length ; i++){
				for (int j = i+1; j < prices.length ; j++) {
                    answer[i]++;
                    //3초의 시점에서 1초 뒤에 떨어지는건 안떨어지는 것으로 보니까
					// 더하고 확인
                    if(prices[i]>prices[j])
						break;
				}
			}
			return answer;

		}
	}
	```
