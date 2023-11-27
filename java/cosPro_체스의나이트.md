```java
public int solution(String pos) {
      int answer = 0;
			Map<Character, Integer> map = new HashMap<>();
			
			Character c = 'A';	
			for(int i = 1 ; i <= 8 ; i++) {
				map.put(c, i);
				c++;
			}
			
			char[] chars = pos.toCharArray();
			
			int xIdx = map.get(chars[0]);
			int yIdx = chars[1]- '0';
			
			if(checkRange(xIdx+1,yIdx+2)) answer++;
			if(checkRange(xIdx+2,yIdx+1)) answer++;			
			if(checkRange(xIdx+2,yIdx-1)) answer++;
			if(checkRange(xIdx+1,yIdx-2)) answer++;
			if(checkRange(xIdx-2,yIdx-1)) answer++;
			if(checkRange(xIdx-1,yIdx-2)) answer++;
			if(checkRange(xIdx-2,yIdx+1)) answer++;
			if(checkRange(xIdx-1,yIdx+2)) answer++;
	
      return answer;
    }
		private boolean checkRange(int x , int y) {
			return 9 > x && x > 0 && 9 > y && y > 0;
		}
```
