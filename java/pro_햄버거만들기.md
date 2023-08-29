```java
import java.util.*;

class Solution {
    public int solution(int[] ingredient) {
        int answer = 0;
        List<Integer> integerList = new ArrayList<>();

        for (int i = 0; i < ingredient.length; i++) {
            integerList.add(ingredient[i]);

            if (integerList.size() >= 4 &&
                    integerList.get(integerList.size() - 4) == 1  &&
                    integerList.get(integerList.size() - 3) == 2 &&
                    integerList.get(integerList.size() - 2) == 3 &&
                    integerList.get(integerList.size() - 1) == 1 ) {
                    answer++;
                    for (int j = 0; j < 4 ; j++) {
                        integerList.remove(integerList.size() - 1);
                    }
            }
        }
        return answer;
    }
}
```
