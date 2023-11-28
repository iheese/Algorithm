```java
    public int solution(String[] bishops) {
        // 여기에 코드를 작성해주세요.
				Map<Character, Integer> map = new HashMap<>();
				
				char c = 'A';
				for(int i = 1 ; i <= 8 ; i++) {
					map.put(c, i);
					c++;
				}
			
				boolean[][] board = new boolean[8][8];
				
				
				for(String s : bishops){
					char[] chars = s.toCharArray();
					int i = map.get(chars[0]) -1;
					int j = chars[1] - '0' - 1;
					while(checkRange(i, j)) {		
						board[i][j] = true;
						i++;
						j++;
					}
					i = map.get(chars[0]) -1;
					j = chars[1] - '0' - 1;
					while(checkRange(i, j)) {		
						board[i][j] = true;
						i--;
						j--;
					}
					i = map.get(chars[0]) -1;
					j = chars[1] - '0' - 1;
					while(checkRange(i, j)) {		
						board[i][j] = true;
						i--;
						j++;
					}
					i = map.get(chars[0]) -1;
					j = chars[1] - '0' - 1;
					while(checkRange(i, j)) {		
						board[i][j] = true;
						i++;
						j--;
					}
				}
			    
				int answer = 0;
				for(int i = 0 ; i < 8 ; i++){
					for(int j = 0 ; j < 8 ; j++){
						if(!board[i][j]) answer++;
					}
				}
			
        return answer;
    }
	
		private boolean checkRange(int i , int j) {
			return i >= 0 && i < 8 && j >= 0 && j < 8;
		}
```
