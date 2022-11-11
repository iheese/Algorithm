체육복
```java
import java.util.Arrays;
    class Solution {
        public int solution(int n, int[] lost, int[] reserve) {
            int answer = n-lost.length;

            Arrays.sort(lost);  
            Arrays.sort(reserve);  
            //정렬 안하면 체육복을 뒷번호가 빌려가는 경우가 생김 그러면 앞쪽 번호가 못가져가는 불상사가 생김
            //ex) 5, [4,2], [3,5]
            //도난 당했는데 여벌있던 친구들 먼저 빼주기
            for (int i = 0; i < lost.length; i++) {
                for (int j = 0; j < reserve.length; j++) {
                    if(lost[i]==reserve[j]){
                        answer++;
                        lost[i]=-1;
                        reserve[j]=-1;
                        break;
                    }
                }
            }

            //앞뒤 비교하면서 앞쪽부터 빌려주기
            for (int i = 0; i < lost.length; i++) {
                for (int j = 0; j < reserve.length; j++) {
                    if((lost[i]+1)==reserve[j]){
                        answer++;
                        reserve[j]=-1;
                        break;
                    }else if((lost[i]-1)==reserve[j]){
                        answer++;
                        reserve[j]=-1;
                        break;
                    }
                }
            }

            return answer;
        }
    }
```
