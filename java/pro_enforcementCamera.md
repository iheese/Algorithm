
```java
import java.util.Arrays;
class Solution {
        public int solution(int[][] routes) {
            int answer = 0;
            int camera = Integer.MIN_VALUE;
            Arrays.sort(routes, (o1, o2) -> o1[1]-o2[1]); //진출 기준으로 정렬

            for(int[] route : routes) { //주어진 배열 순회
                if (camera < route[0]) { // 진입 시점보다 작다면 -> 앞선 진출시점보다 뒷차량의 진입시점이 앞에 있으므로
                    camera = route[1]; //진출 시점에 카메라를 설치하고 진출시점으로 초기화 
                    answer++; 
                }
            }
            return answer;
        }
    }
    ```
