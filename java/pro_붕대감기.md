```java
import java.util.*;

class Solution {
    public int solution(int[] bandage, int health, int[][] attacks) {
        int now = health;
        int time = attacks[attacks.length-1][0];
        int bandageTime = 0;
        Map<Integer, Integer> map = new HashMap<>();
        // 공격 map에 저장
        for(int[] attack : attacks) {
            map.put(attack[0], attack[1]);
        }
        
        // 시간따라 반복문 순회
        for(int i = 1 ; i <= time ; i++) {
            // 공격이 있을 경우
            if(map.containsKey(i)){
                now -= map.get(i);
                bandageTime = 0; 
            } else { // 공격이 없을 경우
                now += bandage[1];
                bandageTime++;
                
                // 공격없는데 연속 성공했을 경우
                if(bandageTime == bandage[0]) {
                    now +=  bandage[2];
                    bandageTime = 0;
                }
                
                // 체력 임계값 설정
                if(now > health) {
                    now = health;
                }
            }
            // 0 이하되면 -1 로 끝!
            if(now <= 0) {
                return -1;
            }
        }
        return now;
    }
}

```

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
class Solution {
    public int solution(int[] bandage, int health, int[][] attacks) {
        int maxHealth = health;
        int curTime = 0;
        for(int i=0; i<attacks.length; i++){
            int time = attacks[i][0];
            int damage = attacks[i][1];
            int timeDiff = time - curTime - 1;
            int healingAmount = (bandage[1] * timeDiff) 
                + bandage[2] * (timeDiff/bandage[0]);

            if(health + healingAmount >= maxHealth){
                health = maxHealth;
            } else{
                health += healingAmount;
            }
            health -= damage;
            if(health<=0) return -1;
            curTime = time;
        }
        return health;
    }
}

```

- 이렇게도 풀수있따...

