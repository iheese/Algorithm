```java

import java.util.*;
class Solution {
    public int solution(int[] picks, String[] minerals) {
        int answer = 0;
        int[][] section = new int[minerals.length/5+1][3];
        int num = picks[0] + picks[1] + picks[2];
        for(int i = 0; i < minerals.length && num > 0 ; i++) {
            // 광물을 곡갱이 종류별로 캤을 때 피로도를 구한다. 
            switch(minerals[i]) {
                case "diamond" :
                    section[i/5][0] += 1;
                    section[i/5][1] += 5;
                    section[i/5][2] += 25;
                    break;
                case "iron" :
                    section[i/5][0] += 1;
                    section[i/5][1] += 1;
                    section[i/5][2] += 5;
                    break;
                case "stone" :
                    section[i/5][0] += 1;
                    section[i/5][1] += 1;
                    section[i/5][2] += 1;
                    break;
            }
            // 연속 5개 치면 갯수 하나 빼줌
            if(i%5 == 4) num--;
        }
        

        // 내림차순, 돌 곡갱이를 사용한 것이 피로도가 많이 드는데 그걸 먼저 꺠야 최소 피로도로 깰수있다. 
        Arrays.sort(section, (o1, o2) -> (o2[2]-o1[2]));
        
        // 2차원 배열 확인 출력
        //System.out.println(Arrays.deepToString(section));
        // 다이아몬드 곡갱이부터 사용, dia, iron, stone 곡갱이 순임
        for(int i =0, pick = 0 ; i < section.length; i++) {
            // 해당 인덱스의 곡갱이를 다 쓰면 다음 곡갱이 사용하기 위해 넘김
            while(pick < 3 && picks[pick] ==0) pick++;
            if(pick == 3) {
                break;
            }
            // 곡갱이 사용
            picks[pick]--;
            answer+=section[i][pick];
        }
        
        return answer;
    }
}

```

- 각 종류의 곡갱이로 깬 피로도를 구한다.
- 피로드 중에 돌로 깼을 때 가장 피로도가 큰 순으로 정렬
- 다이아, 철, 돌 순으로 깨서 최소값을 구한다.
