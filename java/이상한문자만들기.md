```java
// 내풀이
class Solution {
    public String solution(String s) {
        StringBuilder sb = new StringBuilder();
        
        int len = 0;
        while(s.length() != len) {
            char[] chars = s.toCharArray();
            int idx = 0;
            for(int i = 0 ; i < chars.length ; i++) {
                if(chars[i] == ' ') {
                    sb.append(" ");
                    idx = 0;
                } else {
                    if(idx%2 == 0) {
                        sb.append(Character.toUpperCase(chars[i]));
                    } else {
                        sb.append(Character.toLowerCase(chars[i]));
                    }
                    idx++;
                }
                len++;
            }
        }
        return sb.toString();
    }
}
```

- 앞 뒤 중간에 몇 개씩 공백이 나올지 모른다는 것이 포인트인 문제
- 공백 나오면 그냥 stringbuilder 에 추가하고 문자 나오면 짝수번, 홀수번 확인해서 대소문자로 변경해주면 된다. 인덱스 초기화 잊지 않기

```java
// 다른 사람 풀이
class Solution {
  public String solution(String s) {
        char[] chars = s.toCharArray();
        int idx = 0;

        for (int i = 0; i < chars.length; i++) {
            if (chars[i] == ' ')
                idx = 0;
            else
                chars[i] = (idx++ % 2 == 0 ? Character.toUpperCase(chars[i]) : Character.toLowerCase(chars[i]));
        }

        return String.valueOf(chars);
  }
}
```

- idx 비교하여 대소문자 변경하고 +1 된다.


```java
class Solution {
  public String solution(String s) {

        String answer = "";
        int cnt = 0;
        String[] array = s.split("");

        for(String ss : array) {
            cnt = ss.contains(" ") ? 0 : cnt + 1;
            answer += cnt%2 == 0 ? ss.toLowerCase() : ss.toUpperCase(); 
        }
      return answer;
  }
}
```
 

- 공백을 대소문자 변환해도 공백이다. 
- 3항 연산자
