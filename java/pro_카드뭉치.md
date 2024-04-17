```java
import java.util.*;

class Solution {
    public String solution(String[] cards1, String[] cards2, String[] goal) {
        String answer = "Yes"; 
        
        Queue<String> queue1 = new LinkedList<>();  //큐 사용
        Queue<String> queue2 = new LinkedList<>();
        
	// 큐세팅
        for (String card1 : cards1) {
            queue1.add(card1);
        }
        
        for (String card2 : cards2) {
            queue2.add(card2);
        } 
        
        // 비어있지 않고 값이 일치하면 하나 빼준다. 
        for (int i = 0 ; i < goal.length ; i++) {
                        
            if (!queue1.isEmpty() && goal[i].equals(queue1.element())) {
                queue1.poll();
            } else if (!queue2.isEmpty() && goal[i].equals(queue2.element())){
                queue2.poll();
            } else {
                answer = "No";
                break;
            }
        }
        
	// cards 1,2 에는 카드가 남아 있을 수 있다. 
        return answer;
    }
}

```

```java
//24.04.17

import java.util.*;
class Solution {
    public String solution(String[] cards1, String[] cards2, String[] goal) {
        String answer = "Yes";
        Queue<String> q1 = new LinkedList<>();
        Queue<String> q2 = new LinkedList<>();
        
        for(String s : cards1) {
            q1.offer(s);
        }
        
        for(String s : cards2) {
            q2.offer(s);
        }
        
        for(int i = 0 ; i < goal.length ; i++) {
            if(goal[i].equals(q1.peek())) {
                q1.poll();
            } else if(goal[i].equals(q2.peek())) {
                q2.poll();
            } else {
                answer = "No";
                break;
            }
        }
        
        
        return answer;
    }
}
```

- 놀랍게 유사하군
