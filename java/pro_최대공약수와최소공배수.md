```java
class Solution {
    public int[] solution(int n, int m) {
        int[] answer = new int[2];
        int min= Math.min(n,m);
        int gcd = 1;
        
        // 최소공배수 구하기
        for(int i = 2 ; i <= min; i++) {
            if(n%i == 0 && m%i == 0) {
                gcd= Math.max(gcd, i);
            }
        }
        
        // 최대공약수 구하기
        int lcm = gcd * n/gcd * m/gcd;
        answer[0] = gcd;
        answer[1] = lcm;
        
        return answer;
    }
}
```

```java
class Solution {
    public int[] solution(int n, int m) {
       int[] answer = new int[2];

        answer[0] = gcd(n,m);
        answer[1] = (n*m)/answer[0];
        return answer;
    }
    // 재귀함수를 이용
    public static int gcd(int p, int q) {
        if (q == 0) return p;
        return gcd(q, p%q);
   }
}
```

- 재귀를 이용한 풀이 대단..
