```	
	//BinaryGap
	static class Solution {
		public int solution(int N) {
			String binaryString = Integer.toBinaryString(N); //정수를 2진수로
			char[] chars = binaryString.toCharArray(); //2진수를 char 배열로
			int count=0;
			int max=0;
			for(int i=0; i<chars.length-1;i++){ 
				if(chars[i]=='1') { //1 나오면 값 0으로 초기화 
					count=0;
				}else {
					count++; // 0이면 1 더하고 
					if(chars[i+1]=='1'){ //다음 숫자 확인하여 1이면 끝이니까
						if(count>max){  
							max=count; //최대값과 비교해준다.
						}
					}
				}
			}
			return max;
		}
	}
```
