```java
    public String solution(String phrases, int second) {
        // 여기에 코드를 작성해주세요.
				StringBuilder sb = new StringBuilder();
				char[] chars = phrases.toCharArray();
				int num = second % 14;
				for(int i = 0 ; i < 14-num ; i++) {
					sb.append('_');
				}
			  for(int i = 0 ; i < num ; i++){
					sb.append(chars[i]);
				}
				
			  String answer = sb.toString();
        return answer;
    }
```
