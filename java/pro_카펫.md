```java
class Solution {
        public int[] solution(int brown, int yellow) {
            int[] answer = new int[2];

            //총 카펫 갯수
            int area = brown + yellow;

            //1부터 확인
            for (int i = 1; i < area; i++) {
                int row = i;
                int col = area / row;
                
                //카펫의  가로 길이는 세로 길이와 같거나, 세로보다 길다.
                if(row > col) continue;
                
                //안쪽 노란색의 갯수 일치하는지 확인
                if(((row - 2) * (col - 2))==yellow){
                    answer[0]= col;
                    answer[1]= row;
                    return answer;
                }
            }

            return answer;
        }
    }
```
