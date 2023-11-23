```java
import java.util.*;
class Solution {
    public int solution(int[] queue1, int[] queue2) {
        int answer = 0;
        Queue<Integer> q1 = new LinkedList<>();
        Queue<Integer> q2 = new LinkedList<>();
        long allSum = 0;
        long sum1 = 0l;
        long sum2 = 0l;
        for(int i : queue1){
            q1.add(i);
            sum1+=i;
            allSum+=i;
        }
        
        for(int i : queue2){
            q2.add(i);
            sum2+=i;
            allSum+=i;
        }
        
        if(allSum % 2 != 0) {
            return -1;
        }
        
        while(true) {
            // q1.size() == 0 || q2.size() == 0 로 하면 시간 초과
            if(answer > (q1.size() + q2.size())*2){
                answer = -1;
                break;
            }
            int n = 0;
            if(sum1 > allSum / 2) {
                n = q1.poll();
                q2.add(n);
                sum1-=n;
                sum2+=n;
            } else if (sum1 < allSum / 2) {
                n = q2.poll();
                q1.add(n);
                sum1+=n;
                sum2-=n;
            } else {
                break;
            }  
            answer++;
        }
        
        return answer;
    }
}
```
