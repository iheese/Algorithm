```java
class Solution {
    public int solution(int[] number) {
        int answer = 0;
        
        for(int i = 0 ; i < number.length -2 ; i++) {
            for(int j = i+1 ; j < number.length -1 ; j++) {
                for(int k = j+1 ; k < number.length ; k++) {
                    if(number[i] + number[j] + number[k] == 0){
                        answer++;
                    }
                }
            }
        }
        
        
        return answer;
    }
}
```

```java
// DFS
class Solution {
    boolean[] visited;
    int answer = 0;
    public int solution(int[] number) {
        visited = new boolean[number.length];            
        dfs(number, number.length, 0, 3);       
        return answer;
    }
    
    private void dfs(int[] number, int n , int start, int r) {
        if(r == 0) {
            int sum = 0;
            for(int i = 0 ; i < n ; i++) {
                if(visited[i]) {
                    sum+=number[i];
                }
            }
            
            if(sum == 0){
                answer++;
            }
            return;
        }
        for(int i = start ; i < n ; i++) {
            if(!visited[i]) {
                visited[i] = true;
                dfs(number, n, i, r-1);
                visited[i] = false;
            }
        }
        
    }
}
```
