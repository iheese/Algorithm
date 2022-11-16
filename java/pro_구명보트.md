```java
import java.util.Arrays;
    class Solution {
        public int solution(int[] people, int limit) {
            //최소한의 횟수로 옮기려면 몸무게 큰  사람 + 제일 작은 사람이 같이 가야 한다. 
            int count = 0;
            Arrays.sort(people); //정렬
            int min = 0; 
            //max + min 사람 몸무게로 반복문
            for (int max = people.length-1; min <= max ; max--) {
                //합계가 리밋보다 작을 때 다음 min값 비교
                if(people[min]+people[max]<=limit){
                    min++;
                }
                //함계가 리밋보다 크면  max를 1번을 그냥 보내야함
                count++;
            }

            return count;
        }
    }

    ```
