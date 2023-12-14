```java
import java.util.*;
import java.util.Map.Entry;

class Solution {
    public int solution(int k, int[] tangerine) {
        int answer = 0;
        Map<Integer, Integer> map = new HashMap<>();
        
        for(int i : tangerine) {
            map.put(i, map.getOrDefault(i, 0)+1);
        }
    
        int count = k;
        Iterator<Integer> list = map.values().iterator();
        Integer[] arr = new Integer[map.size()];
        int idx = 0;
        
        while(list.hasNext()) {
            arr[idx] = list.next();
            idx++;
        }
        
        Arrays.sort(arr, Collections.reverseOrder());
        
        for(int i = 0; i < arr.length ; i++) {
            if(count <= 0) break;
            count-=arr[i];
            answer++;
        }
        
        return answer;
    }
}
```

- 해시맵 이용해보려다가 그냥 배열 어렵게 구하기 되버

```java
// 개선 코드
import java.util.*;
import java.util.Map.Entry;

class Solution {
    public int solution(int k, int[] tangerine) {
        int answer = 0;
        int max = 0;
        for(int i : tangerine) {
            max = Math.max(i, max);
        }
        
        Integer[] arr = new Integer[max];
        
        Arrays.fill(arr,0);
        
        for(int i = 0; i < tangerine.length; i++) {
            arr[tangerine[i] - 1]++;
        }
        
        Arrays.sort(arr, Collections.reverseOrder());
        
        int count = k;
        for(int i = 0; i < arr.length ; i++) {
            if(count <= 0) break;
            count-=arr[i];
            answer++;
        }
        
        return answer;
    }
}
```

```java
// 좋아요 많은 코드

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
import java.util.*;

class Solution {
    public int solution(int k, int[] tangerine) {
        int answer = 0;
        HashMap<Integer,Integer> map =new HashMap<>();

        for (int t : tangerine) {
            map.put(t, map.getOrDefault(t, 0) + 1);
        }

        List<Integer> list = new ArrayList<>(map.keySet());
        list.sort((o1, o2) -> map.get(o2)-map.get(o1));

        for(Integer key:list){
            k -=map.get(key);
            answer++;
            if(k<=0){
                break;
            }
        }

        return answer;
    }
}
```

- 해시맵 쓸라믄 저렇게 쓰는게 좋았을 것 같다. keyset 사용해서 리스트화해서 사용
