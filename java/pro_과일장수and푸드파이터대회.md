과일장수

```java
import java.util.Arrays;

class Solution {
    public int solution(int k, int m, int[] score) {
        int answer = 0;
        Arrays.sort(score);
        
        for (int i = score.length-1; i>=0 ; i--) {
            if((score.length - i) % m ==0) {
                answer += score[i] * m;
            }
        }
        
        return answer;
    }
}
``

푸드파이터 대회

```java
class Solution {
    public String solution(int[] food) {
        String answer = "";
        StringBuffer sb = new StringBuffer("0");

        for (int i = food.length-1 ; i >= 1 ; i--) {
            if((food[i]/2) > 0 ) {
                for(int j =0 ; j < food[i]/2 ; j++) {
                    sb.insert(0, i);
                    sb.insert(sb.length(), i);
                }
            }
        }
        return sb.toString();
    }
}

``
