```
import java.util.HashMap;
import java.util.Map;

public class Solution {
    public int[] solution(String[] name, int[] yearning, String[][] photo) {
        int[] answer = new int[photo.length]; //리턴값 만들기 
        Map<String, Integer> map = new HashMap<>();
        for (int i = 0; i < name.length; i++) {
            map.put(name[i], yearning[i]);
        }
        
        //2차원 배열 포토를 다 돌아도 최대 700이므로 그냥 2중 for 사용
        for (int i = 0; i < photo.length; i++) {
            int sum = 0;
            for (int j = 0; j < photo[i].length; j++) {
                if(map.containsKey(photo[i][j])){
                    sum+=map.get(photo[i][j]);
                }
            }
            answer[i]=sum;
        }

        return answer;
        }
}
```
