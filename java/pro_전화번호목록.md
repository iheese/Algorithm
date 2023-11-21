```java
import java.util.Arrays;
class Solution {
    public boolean solution(String[] phone_book) {
        boolean answer = true;
        Arrays.sort(phone_book);
        
        for(int i = 0; i < phone_book.length-1 ; i++) {
            if(phone_book[i+1].startsWith(phone_book[i])) {
                answer = false;
            }
        }
        
        return answer;
    }
}
```

```java

// 해시맵 이용하기
import java.util.*;

class Solution {
    public boolean solution(String[] phone_book) {
        Map<String, Integer> map = new HashMap<>();
        // 맵에 값 넣어주기
        for(String number : phone_book) {
            map.put(number, 1);
        }
        // 전화번호목록을 돌면서 해당 번호가 프리픽스로 key에 들어갔는지 확인
        for(String number : phone_book) {
            for(int j = 1; j < number.length() ; j++) {
                String prefix = number.substring(0,j);
                if(map.containsKey(prefix)) {
                    return false;
                }
            }
        }
        
        return true;
    }
}
```
