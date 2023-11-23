```java

class Solution {
    public int solution(int alp, int cop, int[][] problems) {
        int maxAlp = 0;
        int maxCop = 0;
        
        for(int[] problem : problems) {
            maxAlp = Math.max(maxAlp, problem[0]);
            maxCop = Math.max(maxCop, problem[1]); 
        }
        // 초기 코딩력과 알고력이 문제의 코딩력, 알고력보다 클 경우 max값에 맞춰준다.
        if(alp >= maxAlp) {
            alp = maxAlp;
        }
        if(cop >= maxCop) {
            cop = maxCop;
        }
        
        // max 값으로 채워주기
        int[][] dp = new int[maxAlp+2][maxCop+2];
        
        for(int i = alp ; i<= maxAlp ; i++) {
            for(int j = cop; j <= maxCop; j++) {
                dp[i][j] = Integer.MAX_VALUE;
            }
        }
        // 0에서 시작
        dp[alp][cop] = 0;
        
        for(int i = alp ; i <= maxAlp ; i++){
            for(int j = cop ; j <=maxCop ; j++) {
                // 알고력 트레이닝
                dp[i+1][j] = Math.min(dp[i+1][j], dp[i][j] + 1);
                // 코딩력 트레이닝
                dp[i][j+1] = Math.min(dp[i][j+1], dp[i][j] + 1);
                
                // 문제풀기
                for(int[] p : problems) {
                    if(i >= p[0] && j >= p[1]) {
                        // 둘 다 목표치 넘겼을 때 : 목표치 넘은 것과 현재값에서 시간 소요한 값 중 작은 것
                        if(i + p[2] > maxAlp && j+ p[3] > maxCop) {
                            dp[maxAlp][maxCop] = Math.min(dp[maxAlp][maxCop], dp[i][j] + p[4]);
                        // 알고력만 목표치 넘겼을 때 : 코딩력 계속 최솟값 계산
                        } else if (i + p[2] > maxAlp) {
                            dp[maxAlp][j+p[3]] = Math.min(dp[maxAlp][j+p[3]], dp[i][j] + p[4]);
                        // 코딩력만 목표치 넘겼을 때 : 알고력 계속 최솟값 계산
                        } else if (j + p[3] > maxCop) {
                            dp[i+p[2]][maxCop] = Math.min(dp[i+p[2]][maxCop], dp[i][j] +p[4]);
                        // 둘 다 목표치 못넘겼을 때 : 두 개다 최솟값 계산
                        } else if (i + p[2] <= maxAlp && j + p[3] <= maxCop) {
                            dp[i+p[2]][j+p[3]] = Math.min(dp[i + p[2]][j + p[3]], dp[i][j] + p[4]);
                        }
                    }
                }
            }
        }
        
        return dp[maxAlp][maxCop];
    }
}
```
