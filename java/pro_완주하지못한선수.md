```java
import java.util.*;
import java.util.stream.Collectors;
class Solution {
    public String solution(String[] participant, String[] completion) {
        
        Map<String, Integer> map = Arrays.stream(participant)
                .collect(Collectors.toMap(
                    p -> p, p -> 1,  (oldValue, newValue) -> (newValue += oldValue)
                ));
        
        for (String s : completion) {
            if (map.containsKey(s) && map.get(s) == 1) {
                map.remove(s);
            } else {
                map.put(s, map.get(s)-1);
            }
        }
        
        return map.keySet().iterator().next();
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
import java.util.*;
import java.util.stream.Collectors;
class Solution {
    public String solution(String[] participant, String[] completion) {

        Map<String, Integer> map = Arrays.stream(participant)
                .collect(Collectors.toMap(
                    p -> p, p -> 1,  (oldValue, newValue) -> (newValue += oldValue)
                ));

        for (String s : completion) {
            if (map.containsKey(s) && map.get(s) == 1) {
                map.remove(s);
            } else {
                map.put(s, map.get(s)-1);
            }
        }


        return map.keySet().iterator().next();
    }
}
```

```java
 for (String key : hm.keySet()) {
            if (hm.get(key) != 0){
                answer = key;
            }
        }
```

- 아래 부분 이렇게도 되는군..!

```java
//240423
import java.util.*;

class Solution {
    public String solution(String[] participant, String[] completion) {
        String answer = "";
        Map<String, Integer> map = new HashMap<>();
        
        for(String name : participant) {
            map.put(name, map.getOrDefault(name, 0) + 1);
        }
        for(String name : completion) {
            if(map.containsKey(name)) {
                map.put(name, map.get(name)-1);
            }
        } 
        
        answer = map.keySet().stream()
            .filter(name -> map.get(name) == 1)
            .findFirst().get();
        
        return answer;
    }
}
```

