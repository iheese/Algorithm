```java
// 역시 시간 초과로 안되는 풀이였다.
class Solution {
    public int[] solution(int[] numbers) {
        int[] answer = new int[numbers.length];
        
        for(int i = 0 ; i < answer.length ; i++) {
            answer[i] = -1;
        }
        
        for(int i = 0; i < numbers.length-1;i++) {
            for(int j = i+1; j < numbers.length; j++ ){
                if(numbers[i] < numbers[j]) {
                    answer[i] = numbers[j];
                    break;
                } else { 
                    continue;
                }
            }
        }
        
        return answer;
    }
}
```

```
import java.util.Stack;
class Solution {
    public int[] solution(int[] numbers) {
        int[] answer = new int[numbers.length];
        
        Stack<Integer> stack = new Stack<>();
        
        // 스택에 인덱스 넣기
        stack.push(0);
        
        // 인덱스 1부터 순회
        for(int i = 1; i < numbers.length ; i++) {
            // 스택에 값이 있고 스택 peek 값보다 numbers의 값이 크면 큰수로 해당
            while(!stack.isEmpty() && numbers[stack.peek()] < numbers[i]) {
                answer[stack.pop()] = numbers[i];
            }
            // 현재 인덱스는 넣어줌
            stack.push(i);
        }
        
        // 뒤에 큰수 없는 경우 다 -1로
        while(!stack.isEmpty()) {
            answer[stack.pop()] = -1;
        }
        
        return answer;
    }
}
//https://sasca37.tistory.com/306
// 어렵군
```
