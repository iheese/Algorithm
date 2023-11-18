```java
class Solution {
    public String[] solution(int n, int[] arr1, int[] arr2) {
        String[] answer = new String[n];
        for(int i = 0; i < n ; i++) {
            char[] chars1 = binaryChars(arr1[i], n);
            char[] chars2 = binaryChars(arr2[i], n);
            StringBuilder sb = new StringBuilder();
            for(int j = 0 ; j < n ; j++) {
                
                if(chars1[j] == '1' || chars2[j] == '1') {
                    sb.append("#");
                } else {
                    sb.append(" ");
                }
            }
            answer[i] = sb.toString();
        }
        return answer;
    }
    
    private char[] binaryChars(int i, int n) {
        String binaryString = Integer.toBinaryString(i);
    
        while(binaryString.length() != n) {
            binaryString = "0" + binaryString;
        }
        return binaryString.toCharArray();
    }
}
```
