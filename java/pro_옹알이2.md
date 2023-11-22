```java
class Solution {
    public int solution(String[] babbling) {
        int answer = 0;
        String[] canSpeak = {"aya", "ye", "woo", "ma"};
        
        // 주어진 문자열 순회
        for(String b : babbling) {
            while(true){
                for(String c : canSpeak){
                    // 연속된 발음이면 break
                    if(b.contains(c+c)) {
                        break;
                    }
                    // 해당 발음 포함일 경우 해당 문자열을 #으로 변경
                    if(b.contains(c)) {
                        b = b.replace(c, "#");
                    }
                }
                // #을 다시 ""으로 변경, ayayemaaya : 발음 할 수 있는 것, yayae : 발음 할 수 없음 > 이 경우 결국 ye가 남게된다. 
                b = b.replace("#","");
                if(b.equals("")){
                    answer++;
                    break;
                } else {
                    break;
                }
            }        
        }
        
        return answer;
    }
}
```
