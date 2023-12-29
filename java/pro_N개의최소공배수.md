```java
class Solution {
    public int solution(int[] arr) {
        // 처음 2개로 최소공배수 구하기
        int answer = lcm(arr[0], arr[1]);
        // 길이가 2면 바로 끝, 1이면 첫번째 값 리턴
        if(arr.length == 2){
            return answer;
        } else if(arr.length == 1) {
            return arr[0];
        }
        // 3이상이면 반복문으로!
        for (int i = 2; i < arr.length ; i++) {
            answer = lcm(answer, arr[i]);
        }
        return answer;
    }
    
    // 최소공배수 구하는 메소드
    private int lcm(int n, int m) {
        int max = Math.max(n, m);
        int min = Math.min(n, m);
        // 나눠 떨어지거나 작은값이 1이면 바로 큰 값 리턴
        if(max % min == 0 || min == 1) {
            return max;
        } else {
            int x = 1;
            int i = 2;
            // 소인수분해하면서 값을 구한다.
            while(true) {
                if(i >= min) {
                    break;
                }
                if(max % i == 0 && min % i == 0) {
                    max = max/i;
                    min = min/i;
                    x *= i;
                } else {
                    i++;
                } 
            } 
            // 다 곱한값이 최소공배수
            return x * max * min;
        } 
    }
}
```

```java
class NLCM {
    public long nlcm(int[] num) {
        long answer = num[0], g;
        for (int i = 1; i < num.length; i++) {
            g = gcd(answer, num[i]);
            answer = g * (answer / g) * (num[i] / g);
        }
        return answer;
    }

    public long gcd(long a, long b) {
        if (a > b)
            return (a % b == 0) ? b : gcd(b, a % b);
        else
            return (b % a == 0) ? a : gcd(a, b % a);
    }
}
```

- 최대공약수를 이용한 풀, 내풀이랑 생각은 같은데 똑똑한 풀이다.. 정말 재귀까지 굳굳
