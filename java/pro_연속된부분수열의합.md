```java
class Solution {
    public int[] solution(int[] sequence, int k) {
        int[] answer = new int[]{0, sequence.length - 1};
        
        int left = 0;
        int right = 1;
        
        int sum = sequence[0];
        
        while(left < right) {
            if(sum == k) {
                change(right, left, answer);
                sum-=sequence[left++];
                // sum이 k보다 더 크다면 left를 오른쪽으로 이동
            }else if (sum > k) {
                sum -= sequence[left++];
                // sum이 k보다 작다면 right를 오른쪽으로 이동, 작을 때 분기는 다 이곳으로
            } else if (right < sequence.length) {
                sum += sequence[right++];
            } else {
                 break;
            }
        }
        
        return answer;
    }
    
    // 길이가 더 짧은 값으로 정답 변경
    private void change(int right, int left, int[] answer) {
        if(right - left -1 < answer[1] - answer[0]) {
            answer[0] = left;
            answer[1] = right -1;
        }
    }
}
```
