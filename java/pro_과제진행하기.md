```java
import java.util.*;

class Solution {
    public String[] solution(String[][] plans) {
        Assignment[] arr = new Assignment[plans.length];
        
        // 과제 생성
        for(int i = 0 ; i < plans.length; i++) {
            arr[i] = new Assignment(plans[i][0], plans[i][1], plans[i][2]);
        }
        // 정렬
        Arrays.sort(arr, (o1,o2) -> {
            return o1.start - o2.start;
        });
        
        // 진행 중인 과제
        Stack<Assignment> stack = new Stack<>();
        List<String> answer = new ArrayList<>();
        
        int curTime = -1;
        
        for(int i = 0; i < arr.length ; i++) {
            if(stack.isEmpty()) {
                stack.push(arr[i]);
                continue; // 다음 반복으로 넘어감
            }
            
            Assignment curAss = stack.peek();
            Assignment newAss = arr[i];
            
            curTime = curAss.start;
            
            if(curTime + curAss.time <= newAss.start) {
                recursivePop(stack, newAss, curTime, answer);
            } else {
                curAss.time -= newAss.start-curTime;
            }
            stack.push(newAss);
        }
        // 마지막꺼 넣기
         while (!stack.isEmpty()) {
            answer.add(stack.pop().name);
         }
        
        return answer.toArray(new String[0]);
    }
    
    // 조건에 맞게 값 빼기
    public void recursivePop(Stack<Assignment> stack, Assignment newAss, int curTime, List<String> answer) {
        if(stack.isEmpty()) {
            return;
        }
        Assignment curAss = stack.peek();
        
        if(curTime + curAss.time <= newAss.start) {
            answer.add(stack.pop().name);
            recursivePop(stack, newAss, curTime+curAss.time, answer);
        } else {
            curAss.time -= newAss.start - curTime;
        }
    }
    
    // 과제 객체
    static class Assignment {
        private String name;
        private int start;
        private int time;
    
        public Assignment(String name, String start, String time) {
            this.name = name;
            this.start = timeToMinutes(start);
            this.time = Integer.parseInt(time);
        }
        
        private int timeToMinutes(String start) {
            String[] arr = start.split(":");
            return Integer.parseInt(arr[0]) * 60 + Integer.parseInt(arr[1]); 
        }
    }
}
```
