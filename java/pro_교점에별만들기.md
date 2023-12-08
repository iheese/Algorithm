```java
import java.util.*;
class Solution {
    public String[] solution(int[][] line) {
        String[] answer = {};
        List<long[]> list = new ArrayList<>();
        long minX = Long.MAX_VALUE;
        long maxX = Long.MIN_VALUE;
        long minY = Long.MAX_VALUE;
        long maxY = Long.MIN_VALUE;
        
        long dx,dy;
        for(int i = 0; i < line.length-1 ; i++) {
            long a = line[i][0];
            long b = line[i][1];
            long e = line[i][2];
            for(int j = i+1; j < line.length ; j++ ) {
                long c = line[j][0];
                long d = line[j][1];
                long f = line[j][2];
                
                long adbc = a*d - b*c;
                if(adbc == 0) continue;  // 평행
                
                long bfed = b*f - e*d;
                if(bfed%adbc !=0) continue; // x가 정수가 아님
                
                long ecaf = e*c - a*f;
                if(ecaf%adbc !=0) continue; // y가 정수가 아님
                
                dx = bfed / adbc;
                dy = ecaf / adbc;
                
                list.add(new long[]{dx, dy});
                // 교점의 최대 최소 구하기
                minX = Math.min(minX, dx);
                maxX = Math.max(maxX, dx);
                minY = Math.min(minY, dy);
                maxY = Math.max(maxY, dy);
            }
        }
        // 세로 Y, 가로가 X 가 된다. 
        boolean[][] temp = new boolean[(int) (maxY - minY + 1)][(int) (maxX - minX + 1)];
        
        for(long[] longs : list){
            // 0,0 중심인 교점들을 x는 양수방향으로 이동, y는 음수 방향으로 뺴준다. 
            int x = (int)(longs[0] - minX);
            int y = (int)(longs[1] - maxY);
            
            temp[Math.abs(y)][Math.abs(x)] = true;
        }
        
        answer = new String[temp.length];
        
        for(int i = 0; i < temp.length; i++) {
            StringBuilder sb = new StringBuilder();
            for(boolean b: temp[i]) {
                if(b) {
                    sb.append("*");
                } else {
                    sb.append(".");
                }
            }
            answer[i] = sb.toString();
        }
        
        return answer;
    }
}
```
