```java

class Solution {
    public int[] solution(String s) {
        int[] answer = new int[s.length()];
        answer[0] = -1;
        
        char[] charArray = s.toCharArray();
        
        for(int i = 1 ; i < charArray.length ; i++) {
            char[] sub = s.substring(0,i).toCharArray();
            for (int j = sub.length-1 ; j>=0 ; j--) {
                if(charArray[i] == sub[j]) {
                // 반복문 탈출 처리 제대로!!    
		answer[i] = i-j;
                    break;
                } else {
                    answer[i] = -1;
                }
            }
        }
        return answer;
    }
}
```
