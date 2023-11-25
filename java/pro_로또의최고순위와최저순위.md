```java
class Solution {
    public int[] solution(int[] lottos, int[] win_nums) {
        int[] answer = new int[2];
        int count = win_nums.length;
        int correct = 0;
        int zero = 0;
        for(int i = 0 ; i < count; i++) {
            for(int j = 0 ; j < count ; j++) {
                if(win_nums[i] == lottos[j]) {
                    correct++;
                }
            }
        }
        
        for(int i = 0 ; i < count ; i++){
            if(lottos[i] == 0) {
                zero++;
            }
        }
        System.out.println(zero +" "+ correct);
        answer[0] = 7-(correct+zero) > 6? 6 : 7-(correct+zero);
        answer[1] = 7-correct > 6? 6 : 7-correct;
        
        return answer;
    }
}
```
