```java
import java.util.*;
class Solution {
    public int solution(String[][] book_time) {
        int answer = 0;
        int[] day = new int[1441];
        
        for(int i = 0 ; i < book_time.length ; i++) {
            int[] num = changeMinute(book_time[i]);
            for(int j = num[0] ; j <= num[1] ; j++) {
                if(j > 1440) break;
                day[j]++;
            }
        }
        
        for(int i = 0 ; i < day.length; i++) {
            answer= Math.max(answer, day[i]);
        }
        
        return answer;
    }
    
    private int[] changeMinute(String[] time) {
        int[] numTime = new int[2];
        String[] first= time[0].split(":");
        String[] second= time[1].split(":");
        numTime[0] = Integer.parseInt(first[0]) * 60 +  Integer.parseInt(first[1]);
        numTime[1] =  Integer.parseInt(second[0]) * 60 +  Integer.parseInt(second[1]) + 9;
        return numTime;
    }
}
```

- 10분 청소시간 계산시 하루 배열을 넘어가면 종료해줘야 한다.

```java
import java.util.Arrays;
import java.util.PriorityQueue;

class Solution {
    public int solution(String[][] book_time) {

        int[][] bkt = new int[book_time.length][];

        for (int i = 0; i < book_time.length; i++) {
            bkt[i] = new int[] { parseTime(book_time[i][0]), parseTime(book_time[i][1]) + 10 };
        }

        Arrays.sort(bkt, (a, b) -> a[0] - b[0]);

        PriorityQueue<int[]> que = new PriorityQueue<>((a, b) -> a[1] - b[1]);
        int ans = 0;

        for (int i = 0; i < bkt.length; i++) {
            while (!que.isEmpty() && que.peek()[1] <= bkt[i][0]) {
                que.poll();
            }
            que.add(bkt[i]);
            ans = Math.max(ans, que.size());
        }

        return ans;
    }

    protected int parseTime(String time) {

        String[] hhmm = time.split(":");
        int hour = Integer.parseInt(hhmm[0]), min = Integer.parseInt(hhmm[1]);
        return hour * 60 + min;

    }
}
```

- 많은 사람들이 프라이머리큐로 풀었다.
- 어렵다..
