```java
import java.util.ArrayList;
import java.util.Arrays;
import java.util.List;
class Solution {
        public int[] solution(int[] array, int[][] commands) {
            List<Integer> list = new ArrayList<>();
            //정답 넣을 list, 마지막에 배여로 바꿔줄 예정
            for(int[] command : commands){
                int[] arr=Arrays.copyOfRange(array, command[0]-1, command[1]);   //배열 자르기
                Arrays.sort(arr); //배열 정렬
                list.add(arr[command[2]-1]);
            }  //값 찾아서 list에 넣기
            int[] answer = list.stream()
                    .mapToInt(Integer::intValue)
                    .toArray();  //리스트 배열로 변환

            return answer;
        }
    }
    ```
