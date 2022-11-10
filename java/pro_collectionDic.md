
```java
class Solution {
		static String alpabets = "AEIOU";
		static int[] orders = { 781,156,31,6,1};
		//일의 자리: 1씩 증가
		//십의 자리: 1+5^1 = 6씩 증가
		//백의 자리: 6+5^2 = 31씩 증가
		//천의 자리 : 31 + 5^3 = 156씩 증가
		//만의 자리 : 156 + 5^4 = 781씩 증가
		//뒤의 각 자리수에 5개 들어갈 수 있고(5^n) 그 전 자리수갯수만큼 더해준다.
		public int solution(String word) {
			int answer = word.length();

			for (int i = 0; i < word.length(); i++) {
				int index= alpabets.indexOf(word.charAt(i));
				answer+=(orders[i]* index);
			}

			return answer;
		}
	}
	```
