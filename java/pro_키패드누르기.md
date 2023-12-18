```java
import java.util.*;
class Solution {
    public String solution(int[] numbers, String hand) {
        // 초기 엄지값
        int right = 11;
        int left = 10;
        // Map에 저장
        Map<Integer, int[]> map = new HashMap<>();
        map.put(1, new int[]{0,0});
        map.put(2, new int[]{1,0});
        map.put(3, new int[]{2,0});
        map.put(4, new int[]{0,1});
        map.put(5, new int[]{1,1});
        map.put(6, new int[]{2,1});
        map.put(7, new int[]{0,2});
        map.put(8, new int[]{1,2});
        map.put(9, new int[]{2,2});
        map.put(0, new int[]{1,3});
        map.put(10, new int[]{0,3});
        map.put(11, new int[]{2,3});
        
        StringBuilder sb = new StringBuilder();
        // 오른손, 왼손 지정 번호일 때
        for(int i = 0 ; i < numbers.length ; i++) {
            if(numbers[i] == 1 || numbers[i] == 4 || numbers[i] == 7) {
                sb.append('L');
                left = numbers[i];
            } else if (numbers[i] == 3 || numbers[i] == 6 || numbers[i] == 9) {
                sb.append('R');
                right = numbers[i];
            } else {
                // 가운데 라인 숫자일 때 
                for(int j = 0 ; j < map.size() ; j++) {
                    if(j == numbers[i]) {
                        int[] num = map.get(j);
                        int[] rightNum = map.get(right);
                        int[] leftNum = map.get(left);
                        // 거리가 같으면 무슨 손 잡이인지 확인
                        if(calculate(num, rightNum) == calculate(num, leftNum)) {
                            if(hand.equals("right")) {
                                sb.append('R');
                                right = numbers[i];
                            } else {
                               sb.append('L');
                               left = numbers[i]; 
                            }
                            // 거리 계산시 가까운걸로!
                        } else if (calculate(num, rightNum) > calculate(num, leftNum)) {
                            sb.append('L');
                            left = numbers[i]; 
                        } else {
                            sb.append('R');
                            right = numbers[i];
                        }
                    }
                }      
            }
        }
        
        return sb.toString();
    }
    
    // 거리 계산
    private int calculate(int[] num, int[] hand){
        return Math.abs(num[0] - hand[0]) + Math.abs(num[1] - hand[1]);
    }
}
```

- 나름 열심히 풀었는데 정신이 없다.

```java

2
3
4
5
6
7
8
9
10
11
12
13
14
15
16
17
18
19
20
21
22
23
24
25
26
27
28
29
30
31
32
33
34
35
36
37
38
39
40
41
42
43
44
45
46
47
48
49
50
51
class Solution {
    //        0부터 9까지 좌표 {y,x}
    int[][] numpadPos = {
            {3,1}, //0
            {0,0}, //1
            {0,1}, //2
            {0,2}, //3
            {1,0}, //4
            {1,1}, //5
            {1,2}, //6
            {2,0}, //7
            {2,1}, //8
            {2,2}  //9
    };
    //초기 위치
    int[] leftPos = {3,0};
    int[] rightPos = {3,2};
    String hand;
    public String solution(int[] numbers, String hand) {
        this.hand = (hand.equals("right")) ? "R" : "L";

        String answer = "";
        for (int num : numbers) {
            String Umji = pushNumber(num);
            answer += Umji;

            if(Umji.equals("L")) {leftPos = numpadPos[num]; continue;}
            if(Umji.equals("R")) {rightPos = numpadPos[num]; continue;}
        }
        return answer;
    }

    //num버튼을 누를 때 어디 손을 사용하는가
    private String pushNumber(int num) {
        if(num==1 || num==4 || num==7) return "L";
        if(num==3 || num==6 || num==9) return "R";

        // 2,5,8,0 일때 어디 손가락이 가까운가
        if(getDist(leftPos, num) > getDist(rightPos, num)) return "R";
        if(getDist(leftPos, num) < getDist(rightPos, num)) return "L";

        //같으면 손잡이
        return this.hand;
    }

    //해당 위치와 번호 위치의 거리
    private int getDist(int[] pos, int num) {
        return Math.abs(pos[0]-numpadPos[num][0]) + Math.abs(pos[1]-numpadPos[num][1]);
    }
}
```

- 좋아요 많이 받은 풀이, 이유가 있다 정말
