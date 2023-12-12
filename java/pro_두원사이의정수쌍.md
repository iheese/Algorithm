```java
class Solution {
    public long solution(int r1, int r2) {
        long answer = 0;
        long r1x = (long)Math.pow(r1,2);
        long r2x = (long)Math.pow(r2,2);
        long side = 0;
        for(int i = 0 ; i <= r2 ; i++) {
            long y2 = (long)Math.sqrt(r2x - (long)Math.pow(i,2));
            long y1 = (long)Math.sqrt(r1x - (long)Math.pow(i,2));
            // 작은 원이 x, y축에 접하는 값
            if(Math.sqrt(r1x-Math.pow(i,2))%1 == 0) {
                side++;
            }

            answer += (y2-y1)*4;
        }
 
        answer+=side*4-4;
        
        return answer;
    }
}
```

```java
// 최적화한 풀이
class Solution {
    public long solution(int r1, int r2) {
        long answer = 0;
 
        for (int i=1; i<=r2; i++) {
            long minJ = (int) Math.ceil(Math.sqrt(1.0*r1*r1 - 1.0*i*i));
            long maxJ = (int) Math.floor(Math.sqrt(1.0*r2*r2 - 1.0*i*i));
 
            answer += (maxJ - minJ + 1);
 
        }
 
        return answer * 4;
    }
}
```
