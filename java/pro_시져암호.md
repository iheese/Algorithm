```java
class Solution {
    public String solution(String s, int n) {

        StringBuilder sb = new StringBuilder();
        char[] chars = s.toCharArray();
        for(char c : chars){
            // 띄어쓰기
            if(c == ' ') {
                sb.append(' ');
                continue;
            } else {
                // 소문자인데 z를 넘길 경우
                if(c+n > 'z' && c <= 'z' && c >= 'a') {
                    sb.append((char)(c + n - ('z'-'a'+1)));\
                // 대문자인데 Z를 넘길 경우
                } else if (c + n > 'Z' && c <= 'Z' && c >= 'A') {
                    sb.append((char)(c + n - ('Z'-'A'+1)));
                } else {
                    sb.append((char)(c + n));
                }
            }
        }
        return sb.toString();
    }
}
```

- 내풀이

```java
lass Caesar {
    String caesar(String s, int n) {
        String result = "";
    n = n % 26;
    for (int i = 0; i < s.length(); i++) {
      char ch = s.charAt(i);
      if (Character.isLowerCase(ch)) {
        ch = (char) ((ch - 'a' + n) % 26 + 'a');
      } else if (Character.isUpperCase(ch)) {
        ch = (char) ((ch - 'A' + n) % 26 + 'A');
      }
      result += ch;
    }
        return result;
    }
}
```

- 대소문자는 Character.isLowerCase, Character.isUpperCase 로 확인가능
- 깔끔하다!
