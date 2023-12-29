```java
import java.util.*;
class Solution {
    public long solution(long n) {
        // String 변환
        String s = String.valueOf(n);
        // char[] 변환
        char[] chars = s.toCharArray();
        // 오름차순으로 나열
        Arrays.sort(chars);
        String str = "";
        // 꺼꾸로 다시 붙여서 Long 으로 변환해서 리턴
        for(int i = chars.length - 1 ; i >= 0 ; i--) {
            str += chars[i];
        }
        
        return Long.parseLong(str);
    }
}
```

- 나의 코드 단순하게.. 풀어봤다

```java
public class ReverseInt {
    String res = "";
    public int reverseInt(int n){
        res = "";
        Integer.toString(n).chars().sorted().forEach(c -> res = Character.valueOf((char)c) + res);
        return Integer.parseInt(res);
    }
}
```

- 좋아요 많은 코드, 스트림으로 정말 잘 푸셨다.. 꺼꾸로 붙이기할 때 저렇게 하면 되는구나 싶었다.

```java
import java.util.*;

class Solution {
  public long solution(long n) {
        String[] list = String.valueOf(n).split("");
        Arrays.sort(list);

        StringBuilder sb = new StringBuilder();
        for (String aList : list) sb.append(aList);

        return Long.parseLong(sb.reverse().toString());
  }
}
```

- StringBuilder의 reverse() 는 참 유용하다.

```java
import java.util.*;
import java.util.stream.Collectors;

class Solution {
    public long solution(long n) {

        // Character 리스트로 변환
        List<Character> characters = String.valueOf(n).chars().mapToObj(c -> (char)c).collect(Collectors.toList());

        //Collections.sort(characters, Collections.reverseOrder());

        String str = characters.stream()
                .map(String::valueOf)
                .sorted(Comparator.reverseOrder())
                .collect(Collectors.joining());

        return Long.parseLong(str);
    }
}
```

- Collections.sort 써도 되고 sorted 스트림 메소드 이용해도 된다. 
