```java
import java.util.*;
class Solution {
    public int[] solution(int[] arr) {
        int[] temp = arr.clone();
        int[] answer = new int[arr.length - 1];
        if(temp.length - 1 == 0) return new int[]{-1};
        
	// 최소값을 뽑기 위해 배열 정렬했다.
	Arrays.sort(temp);

        int i = 0;
        int j = 0;
	// 마지막 값까지 확인하면서 answer 채워주기
        while(answer.length -1 >= j) {
            if(temp[0] != arr[i]){
                answer[j] = arr[i];
                i++;
                j++;
            } else {
                i++;
            } 
        }
        
        return answer;
    }
}
```

- 조금 정신없게 푼 것 같다.

```java
import java.util.Arrays;
import java.util.stream.Stream;
import java.util.List;
import java.util.ArrayList;

class Solution {
  public int[] solution(int[] arr) {
      if (arr.length <= 1) return new int[]{ -1 };
      int min = Arrays.stream(arr).min().getAsInt();
      return Arrays.stream(arr).filter(i -> i != min).toArray();
  }
}
```

- 좋아요 많은 코드는 역시 스트림을 이용했다. 
 
