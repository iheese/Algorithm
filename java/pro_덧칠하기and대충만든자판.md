덧칠하기

```java
class Solution {
    public int solution(int n, int m, int[] section) {
        int max = 0;
        int answer = 0;

        for (int i : section) {
            if (i < max) {
                continue;
            }
            answer++;
            max = i + m;
        }
        
        return answer;
    }
}
```

대충 만든 자판

```java

import java.util.HashMap;

class Solution {
    public int[] solution(String[] keymap, String[] targets) {
        HashMap<String, Integer> map = new HashMap<>();
        int[] ret = new int[targets.length];
        
        for(String key : keymap) {
            for(int i=0 ; i<key.length() ; i++) {
                String c = key.substring(i,i+1);
                if(!map.containsKey(c) || i< map.get(c)) {
                    map.put(c, i+1);
                }
            }
        }
        
        for(int i=0 ; i<targets.length ; i++) {
            int cnt = 0;
            for(int j=0 ; j<targets[i].length() ; j++) {
                String c = targets[i].substring(j, j+1);
                if(!map.containsKey(c)) {
                    cnt = -1;
                    break;
                } else {
                    cnt += map.get(c);
                }
            }
            ret[i] = cnt;
        }
        return ret;
    }
}
```
