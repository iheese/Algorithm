```java
    public int solution(String s1, String s2) {
        // 여기에 코드를 작성해주세요.
				int max1 = compare(s1, s2);
				int max2 = compare(s2, s1);
			 	
				int max = Math.max(max1, max2);
				
        int answer = s1.length() + s2.length() - max;
        return answer;
    }
		
		private int compare(String s1, String s2) {
			int max = 0;
			for(int i = 0 ; i < s1.length() ; i++) {
					for(int j = 0 ; j < s2.length() ; j++){
						if(s1.substring(i, s1.length()).equals(s2.substring(0, j)))	{
							max = Math.max(j, max);
						}
					}
				}
			return max;
		} 
```
