둘만의 암호

```java
class Solution {
    public String solution(String s, String skip, int index) {
        String answer = "";
        
        for (int i = 0 ; i< s.length() ; i++) {
            char c = s.charAt(i);
            for (int j = 0 ; j<index; j++) {
                c+=1;
                if (c > 'z') {
                    c -= 26;
                }
                if (skip.contains(String.valueOf(c))) {
                    j--;
                }
            }
            answer += c;
        }

        return answer;
    }
}
```

``java
//24.04.17
class Solution {
    public String solution(String s, String skip, int index) {
        String answer = "";
        char[] chars = s.toCharArray();
        char[] skips = skip.toCharArray();
        
        int[] alpabetIdx = new int[26];
        
        for(char c : skips){
           alpabetIdx[c-'a'] = 1;
        }
        
        for(int i = 0; i < chars.length ; i++) {
            char temp = chars[i];
            int count = index;
            for(int j = 0 ; j < index ; j++) {
                temp++;
                if(temp > 'z') {
                    temp -= 26;
                }
                if(alpabetIdx[temp - 'a'] != 0) {
                    j--;
                } 
                
            }
            
            answer+= String.valueOf(temp);
        }
        
        return answer;
    }
}
```

- 어렵네..ㅠㅠ
