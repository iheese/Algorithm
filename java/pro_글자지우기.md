```java
class Solution {
    public String solution(String my_string, int[] indices) {
        StringBuffer sb = new StringBuffer(my_string); // 가변 문자열
        for(int i : indices) { // 인덱스배열 순회
            sb.setCharAt(i, ' '); // 해당 인덱스의 문자변경
        }

        return sb.toString().replaceAll(" ", ""); // 다시 합치기
    }
}
```
