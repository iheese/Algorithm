문자열의 뒤의 n글자

```java
class Solution {
    public String solution(String my_string, int n) {         
        int length = my_string.length();
        String answer = my_string.substring(length-n, length);
        return answer;
    }
}
```

접두사인지 확인하기


```java
class Solution {
    public int solution(String my_string, String is_prefix) {
        boolean isPrefix = my_string.startsWith(is_prefix);
        return isPrefix? 1 : 0;
    }
}
```
