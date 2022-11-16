```
//수박수박
	static class Solution {
		static public String solution(int n) {
			StringBuilder sb = new StringBuilder();

			for(int i=1;i<=n;i++){
				if(i%2!=0){
					sb.append("수");
				}else{
					sb.append("박")
				}
			}
			return sb.toString();
		}
	}
```

```
//완료하지 못한  선수
	class Solution {
		public String solution(String[] participant, String[] completion) {

			for (int i = 0; i < completion.length; i++) {
				int count=0;
				for (int j = 0; j < participant.length; j++) {
					if (completion[i].equals(participant[j])) {
						count++;

						if(count==1){
							participant[j] = "x";
						}else{
							break;
						}
					}
				}
			}
			String answer = null;
			for (String i : participant) {
				if (!i.equals("x")) {
					answer = i;
				}
			}

			return answer;
		}
	}
```
```
import java.util.HashMap;

class Solution {
    public String solution(String[] participant, String[] completion) {
        String answer ="";
        HashMap<String, Integer> hm = new HashMap<>();
        for(String player : participant) hm.put(player, hm.getOrDefault(player, 0) + 1);
        for(String player : completion) hm.put(player, hm.get(player) -1);
        for(String key : hm.keySet()) {
        	if(hm.get(key) != 0) {
        		answer = key;
        		System.out.println(answer);
        		break;
        	}
        }
        return answer;
    }
}
import java.util.*;
class Solution {
    public String solution(String[] participant, String[] completion) {
        Arrays.sort(participant);
        Arrays.sort(completion);
        int i;
        for ( i=0; i<completion.length; i++){
            if (!participant[i].equals(completion[i])){
                return participant[i];
            }
        }
        return participant[i];
    }
}
```
