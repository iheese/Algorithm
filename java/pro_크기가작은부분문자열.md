크기가 작은 부분문자열

```java
class Solution {
    public int solution(String t, String p) {
        int answer = 0;
        int tLength = t.length(); 
        int pLength = p.length(); // p 최대범위

        for(int i = 0 ; i < tLength-pLength+1 ; i++) {
            long tnum = Long.parseLong(t.substring(i, i+pLength)); 
            long pnum = Long.parseLong(p);

            if(pnum >= tnum) {
                answer++;
            }
        }

        return answer;
    }
}
```
