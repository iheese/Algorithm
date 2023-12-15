```java
class Solution {
    public int solution(int n) {
        String temp = Integer.toString(n, 3);
        String change = new StringBuilder(temp).reverse().toString();
        return Integer.parseInt(change, 3);
    }
}
```

- 관련 문제 경험이 있어 쉽게 풀렸다
- String k진수 수= Integer.toString(int n, int k) 은 n은 10진수 숫자, k은 몇진수로 나타낼지 하면 String 값으로 n을 k진수변환해서 리턴해준다.
- int s의 10진수 수= Integer.parseInt(String s, int n) 는 n진수로 나타낸 s 문자열을 10진수로 변환해서 리턴해준다.
- StringVBuilder의 reverse() 는 문자열을 뒤집는데 아주 유용하다.

```java
// 좋아요 많이 받은 답에 더하기 순서만 바꾸기 리버스를 지웠다.

class Solution {
    public int solution(int n) {
        String a = "";

        while(n > 0){
            a = a + (n % 3) ;
            n /= 3;
        }

        return Integer.parseInt(a,3);
    }
}
```

- String에 더하기를 하면 저렇게 쌓안다 아주 좋은 아이디어인 것 같다.

