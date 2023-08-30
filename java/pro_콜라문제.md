```java
class Solution {
    public int solution(int a, int b, int n) {
        int answer = 0;
        
        while ( n >= a) {
            int get = n/a*b;
            answer += get;
            int x = n%a;
            n = get + x;
        }
        
        return answer;
    }
}
```
