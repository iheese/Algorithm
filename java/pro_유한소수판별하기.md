```java
```java
// 내풀이
class Solution {
    public int solution(int a, int b) {
        int answer = 1;
        int anum = a;
        int bnum = b;
        int num = 2; // 나누는 수
        for(int i = a ; i >=2 ; i--) {
            if(anum == 1) {
                break;
            }
            if(anum % i == 0 && bnum % i == 0){
                anum = anum / i;
                bnum = bnum / i;
            }
        }
        
        while(bnum != 1) {
            if(bnum % 2 == 0) {
                bnum = bnum / 2;
            } else if( bnum % 5 == 0) {
                bnum = bnum /5;
            } else {
                return 2;
            }
        }
        
        return answer;
    }
}
```

```java
// 재귀 최대공약수를 이용한 풀이
class Solution {
    public int solution(int a, int b) {
        b /= gcd(a, b);
        while (b != 1) {
            if (b % 5 == 0) {
                b /= 5;
                continue;
            }
            if (b % 2 == 0) {
                b /= 2;
                continue;
            }
            return 2;
        }
        return 1;
    }

    private int gcd(int a, int b) {
        if (b == 0) {
            return a;
        }
        return gcd(b, a % b);
    }
}
```

```java
// 숫자 범위 1000 아래에서 2의 소인수 최대 9개 존재 가능, 5의 소인수 4개 존재가능
// 2^9 * 5^4 = 320000을 곱해서 나눈다. 
class Solution {
    public int solution(int a, int b) {
        int answer = ((a*320000)%b == 0) ? 1 : 2;
        return answer;
    }
}
```

```

