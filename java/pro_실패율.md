```java
import java.util.*;
class Solution {
    public int[] solution(int N, int[] stages) {
        int[] answer = new int[N];
        int entire = 0;
        int part = 0;
        Double[] arr = new Double[N];
        
        // 실패율 구하기, 아무값도 없으면 Nan이 들어가서 계산이 안된다. 0 넣어줘야함
        for(int i = 1 ; i <= N ; i++) {
            entire = 0;
            part = 0;
            for(int j = 0; j < stages.length; j++) {
                if(i <= stages[j]) {
                    entire++;
                }
                
                if(i == stages[j]) {
                    part++;
                }
            }
            arr[i-1] = (double) part/entire > 0? (double) part/entire : 0;
        }
        
        // 내림차순 나열
        Double[] temp = arr.clone();
        Arrays.sort(temp, Collections.reverseOrder());
        
        // 반복문 두개 돌려서 일치하면 해당 인덱스 넣어주기
        for(int i = 0 ; i < arr.length; i++) {
            for(int j = 0 ; j < temp.length ; j++) {
                if(arr[i] == temp[j]) {
                    answer[j] = i+1;                    
                }
            }
        }
        
        return answer;
    }
}

```

- 역시 출력해보면서 값 확인하면 쉽게 풀린다.
- 0/0 은 Nan 되기 때문에 처리해줘야한다.

```java
1
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
52
import java.util.ArrayList;
import java.util.Collections;
import java.util.List;

class Solution {
    public int[] solution(int N, int[] lastStages) {
        int nPlayers = lastStages.length;
        int[] nStagePlayers = new int[N + 2];
        for (int stage : lastStages) {
            nStagePlayers[stage] += 1;
        }

        int remainingPlayers = nPlayers;
        List<Stage> stages = new ArrayList<>();
        for (int id = 1 ; id <= N; id++) {
            double failure = (double) nStagePlayers[id] / remainingPlayers;
            remainingPlayers -= nStagePlayers[id];

            Stage s = new Stage(id, failure);
            stages.add(s);
        }
        Collections.sort(stages, Collections.reverseOrder());

        int[] answer = new int[N];
        for (int i = 0; i < N; i++) {
            answer[i] = stages.get(i).id;
        }
        return answer;
    }

    class Stage implements Comparable<Stage> {
        public int id;
        public double failure;

        public Stage(int id_, double failure_) {
            id = id_;
            failure = failure_;
        }

        @Override
        public int compareTo(Stage o) {
            if (failure < o.failure ) {
                return -1;
            }
            if (failure > o.failure ) {
                return 1;
            }
            return 0;
        }
    }
}
```

- 알고리즘도 객체지향적으로 잘푼 사람들이 신기하다.. 좋은 풀이인듯!

