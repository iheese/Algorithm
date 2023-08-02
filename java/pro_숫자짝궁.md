```java
import java.util.*;

class Solution {
    public String solution(String X, String Y) {
        
        int[] cntX = new int[10]; // 숫자 배열 만들기
        int[] cntY = new int[10];

        for (String x : X.split("")) {
            cntX[Integer.parseInt(x)]++;  // 어떤 숫자가 몇 개 있는 지 알 수 있게
        }

        for (String y : Y.split("")) {
            cntY[Integer.parseInt(y)]++;
        }
        
        StringBuffer sb = new StringBuffer();  // 가변 문자열 사용하여 처리

        for (int i = 9 ; i>=0 ; i--) { // 최대값을 만들어야 하므로 역순회
            while (cntX[i]>0 && cntY[i]>0) { // 두개다 해당 값이 있으면
                cntX[i]--;  // 추가된 값은 하나씩 제거
                cntY[i]--;
                sb.append(Integer.toString(i));   // 가변 문자열에 추가
            }
        }

        String answer = sb.toString();
        
        if(answer.startsWith("0")) {
            answer = "0";
        } else if (answer.isEmpty()){
            answer = "-1";
        }
        return answer;
    }
}
```
