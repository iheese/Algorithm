```java
import java.util.*;

class Solution {
    public long solution(int[] weights) {
        long answer = 0;

        Arrays.sort(weights);
        Map<Double, Integer> map = new HashMap<>();
        
        for(int w : weights) {
            // 자신
            double a = w*1.0;
            // 비가 3m, 2m 일 때
            double b = (w*2.0)/3.0;
            // 비가 4m, 2m 일 때
            double c = (w*1.0)/2.0;
            // 비가 4m, 3m 일 때
            double d = (w*3.0)/4.0;
            
            if(map.containsKey(a)) {
                answer+= map.get(a);
            }
            if(map.containsKey(b)) {
                answer+= map.get(b);
            }
            if(map.containsKey(c)) {
                answer+= map.get(c);
            }
            if(map.containsKey(d)) {
                answer+= map.get(d);
            }
            map.put((w*1.0), map.getOrDefault((w*1.0),0)+1);
        }
        return answer;
    }
}
```

- 풀이 참조해서 풀었다.. 어우 어려웠당

```java
class Solution {
    public long solution(int[] weights) {
        long answer = 0;
        long[] arr = new long[1001];

        for(int i = 0; i < weights.length; i++){
            arr[weights[i]]++;    
        }

        for(int i = 100; i < 1001; i++){
            if(arr[i] == 0) continue;
            answer += (arr[i] * (arr[i] - 1)) / 2;

            if((4 * i) / 3 > 1000) continue;
            if(i % 3 == 0){
                answer += arr[i] * arr[(4 * i) / 3];
            }

            if((3 * i) / 2 > 1000) continue;
            if(i % 2 == 0){
                answer += arr[i] * arr[(3 * i) / 2];
            }

            if(2 * i >1000) continue;
            answer += arr[i] * arr[2 * i];
        }

        return answer;
    }
}

```

- 좋아요가 많은 답 비가 될 수 있는 경우가 3개, 같은 무개일 경우 뿐이라 일일히 비교하여 값을 구해준다.
