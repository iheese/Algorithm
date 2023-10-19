```java

import java.util.*;
class Solution {
    public int solution(int[] nums) {
        int answer = 0;
        int choice = nums.length/2; // 선택 가능한 폰켓몬 수
        Set<Integer> set = new HashSet<>();
        
	// set에 넣으면 중복이 사라진다.
        for (int n : nums) {
            set.add(n);
        }
        
	// set 길이보다 선택 갯수가 작거나 같으면 
        if (set.size() >= choice){
            answer = choice; // 선택갯수가 정답이 되고
        } else {
            answer = set.size(); // 아니면 set 길이가 정답이 된다.
        }
        
        return answer;
    }
}

```

```java

import java.util.Arrays;
import java.util.stream.Collectors;

class Solution {
    public int solution(int[] nums) {
        return Arrays.stream(nums) //배열 스트림으로 만들고
                .boxed() // 객체화한 int 배열
                .collect(Collectors.collectingAndThen(Collectors.toSet(),
                        phonekemons -> Integer.min(phonekemons.size(), nums.length / 2)));
		// set으로 만든다. 
		// collectingAndThen collecting 하고 그 결과로 메소드 호출하게 해준다.     
	}
}
```


