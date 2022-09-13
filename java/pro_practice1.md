```
	class Solution {
		public int solution(int n) {
			int answer = 0;

			for (int i = 2; i < n; i++) {
				if((n-1)%i==0) {
					answer=i;
                    break;
				}
			}
			
			return answer;
		}
	}
```

```
//짝수와 홀수
		class Solution {
			public String solution(int num) {
				String answer = "";
				if(num%2==0){
					answer="Even";
				}else{
					answer="Odd";
				}
				return answer;
			}
		}

```

```
// 자릿수 더하기
public class Solution {
		public int solution(int n) {
			int answer = 0;
			while(n>=1){
				answer+=n%10;
				n=n/10;
			}
			return answer;
		}
	}
	
```
