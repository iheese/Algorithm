```java
class Solution {
		public int solution(int[] money) {
			//점화식 dp[i] = max(money[i] + dp[i-2], dp[i-1]) //이전집까지 턴것, 현재집과 전전 집까지 턴것의 합
			int[] firstStart = new int[money.length];
			int[] secondStart = new int[money.length];
			firstStart[0] = firstStart[1] = money[0];
			secondStart[1] = money[1];

			for (int i = 2; i < money.length; i++) {
				firstStart[i] = Math.max(firstStart[i-1], money[i]+firstStart[i-2]);
				secondStart[i] = Math.max(secondStart[i-1], money[i]+ secondStart[i-2]);
			}

			return Math.max(firstStart[money.length-2], secondStart[money.length-1]);
		}
	}
	```
