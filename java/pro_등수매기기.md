```java
// 나의 풀이
import java.util.*;
class Solution {
    public int[] solution(int[][] score) {
        float[] aver = new float[score.length];
        Float[] sorted = new Float[score.length];
        int[] answer = new int[score.length];
        
        for(int i = 0 ; i < score.length; i++) {
            aver[i] = average(score[i][0], score[i][1]);
            sorted[i] = average(score[i][0], score[i][1]);
            answer[i] = Integer.MAX_VALUE;
        }
        
        Arrays.sort(sorted, Collections.reverseOrder());
        
        for(int i = 0 ; i < sorted.length ; i++) {
            for(int j = 0 ; j < aver.length ;j++) {
                if(sorted[i] == aver[j]) {
                    answer[j] = Math.min(i+1, answer[j]);
                }   
            }
        }
        
        return answer;
    }
    
    private float average(int a, int b) {
        return (a+b)/2f;
    }
}
```

```java
// 추천 많은 풀이 아주 깔끔스
import java.util.*;
class Solution {
    public int[] solution(int[][] score) {
        List<Integer> scoreList = new ArrayList<>();
        for(int[] t : score){
            scoreList.add(t[0] + t[1]);
        }
        scoreList.sort(Comparator.reverseOrder());

        int[] answer = new int[score.length];
        for(int i=0; i<score.length; i++){
            answer[i] = scoreList.indexOf(score[i][0] + score[i][1])+1;
        }
        return answer;
    }
}

```
