```java
import java.util.*;
class Solution {
    public int[] solution(int[] numbers) {
        int[] answer = {};
        Set<Integer> set = new HashSet<>();
        for(int i = 0 ; i < numbers.length-1; i++) {
            for(int j = i+1 ; j < numbers.length; j++) {
                set.add(numbers[i]+numbers[j]);
            }
        }
        // Set to array
        Integer[] arr = set.toArray(new Integer[0]);
        
        Arrays.sort(arr);
        
        return Arrays.stream(arr).mapToInt(Integer::intValue).toArray();
    }
}
```

- 비효율적으로 풀었다.

```java
import java.util.*;
class Solution {
    public int[] solution(int[] numbers) {
        int[] answer = {};
        Set<Integer> set = new HashSet<>();
        for(int i = 0 ; i < numbers.length-1; i++) {
            for(int j = i+1 ; j < numbers.length; j++) {
                set.add(numbers[i]+numbers[j]);
            }
        }           
              
        return set.stream().sorted().mapToInt(Integer::intValue).toArray();
    }
}

```

- 위 코드를 개선한 코드

```java
import java.util.Iterator;
import java.util.Set;
import java.util.TreeSet;

class Solution {
    public int[] solution(int[] numbers) {
        Set<Integer> sumNumber = new TreeSet();

        for(int i = 0; i < numbers.length-1; i++){
            for(int j = i+1; j < numbers.length; j++){
                sumNumber.add(numbers[i] + numbers[j]);
            }
        }

        int[] answer = new int[sumNumber.size()];
        int index = 0;
        Iterator itor = sumNumber.iterator();
        while(itor.hasNext()){
            answer[index] = (int)itor.next();
            index++;
        }

        return answer;
    }
}
```

- TreeSet을 이용하면 자동 오름차순 정렬해준다. 
- 좋은 방법이다. 
