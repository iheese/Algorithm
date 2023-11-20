```java
import java.util.*;

class Solution {
    List<Integer> list = new ArrayList<>();
    boolean[] check = new boolean[7];
    public int solution(String numbers) {
        int answer = 0;
        for(int i = 0; i < numbers.length(); i++) {
            dfs(numbers,"",i+1);
        }
        
        for(int i =0 ; i < list.size(); i++) {
            if(isPrime(list.get(i))) {
                answer++;
            }
        }
        
        return answer;
    }
    
    private void dfs(String str, String temp, int m) {
        if(temp.length() == m) {
            int num = Integer.parseInt(temp);
            if(!list.contains(num)){
                list.add(num);
            }
        }
        
        for(int i = 0; i < str.length(); i++) {
            if(!check[i]) {
                check[i] = true;
                temp += str.charAt(i);
                dfs(str, temp, m);
                check[i] = false;
                temp = temp.substring(0, temp.length() - 1); 
            }
        }
    }
    
    // 소수 판단    
    private boolean isPrime(int num) {
        if(num < 2) {
            return false;
        }
        
        for(int i = 2; i <= Math.sqrt(num); i++) {
            if(num % i == 0) {
                return false;
            }
        }
        return true;
    }
}

```
