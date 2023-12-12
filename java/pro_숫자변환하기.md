 
```java
// 자료구조 queue, set 이용
import java.util.*;
class Solution {
    public int solution(int x, int y, int n) {
        int answer = 0;
        Queue<Integer> q = new LinkedList<>();
        Set<Integer> visited = new HashSet<>();
        q.add(x);
        visited.add(x);
        
        while(!q.isEmpty()) {
            int size = q.size();
            for(int i = 0; i < size; i++){
                int cur = q.poll();
                if(cur == y) {
                    return answer;
                }
                
                if(cur+n <= y && !visited.contains(cur+n)){
                    q.add(cur+n);
                    visited.add(cur+n);
                }
                if(cur*2 <= y && !visited.contains(cur*2)){
                    q.add(cur*2);
                    visited.add(cur*2);
                }
                if(cur*3 <= y && !visited.contains(cur*3)){
                    q.add(cur*3);
                    visited.add(cur*3);
                }
            }
            answer++;
        }
        return -1;
    }
}
```

```java
// dp

import java.util.*;
class Solution {
    public int solution(int x, int y, int n) {
        int[] dp = new int[y+1];
        for(int i = 0 ; i < y+1; i++) {
            dp[i] = Integer.MAX_VALUE;
        }
        
        dp[x] = 0;
        
        for(int i = x ; i < y+1 ; i++) {
            if(dp[i] == Integer.MAX_VALUE) continue;
            
            if(i + n <= y) {
                dp[i+n] = Math.min(dp[i+n], dp[i]+1);
            }
            
            if(i * 2 <= y) {
                dp[i*2] = Math.min(dp[i*2], dp[i]+1);
            }
            
            if(i * 3 <= y) {
                dp[i*3] = Math.min(dp[i*3], dp[i]+1);
            }
        }
        if(dp[y] == Integer.MAX_VALUE){
            return -1;
        } 
        return dp[y];
    }
}
```

