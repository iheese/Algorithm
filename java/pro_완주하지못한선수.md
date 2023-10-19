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
