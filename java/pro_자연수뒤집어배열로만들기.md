```java
class Solution {
    public int[] solution(long n) {
        char[] chars = String.valueOf(n).toCharArray();
        int[] answer = new int[chars.length];
        
        for(int i = 0 ; i < chars.length; i++) {
            answer[i] = chars[chars.length-i-1] - '0';
        }
        
        return answer;
    }
}
```

```java
class Solution {
    public int[] solution(long n) {
        return new StringBuilder().append(n).reverse().chars().map(Character::getNumericValue).toArray();
    }
}
```

- for 을 이용한 것이 0.02 ~ 0.05초, stream은 2.09~2.77 초가 걸린다.
