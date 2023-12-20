```java
class Solution {
    public int solution(String[] board) {
        int answer = -1;
        int oCnt = 0; 
        int xCnt = 0;
        
        for(int i = 0 ; i < 3 ; i++) {
            oCnt += countChar(board[i], 'O');
            xCnt += countChar(board[i], 'X');
        }
        
        // X가 더 많으면 규칙 위반
        if(xCnt > oCnt) {
            return 0;
        }
        
        // O가 X보다 2개 이상 많으면 위반
        if(oCnt > xCnt + 1) {
            return 0;
        } 
        
        // O이 이겼는데 수가 같을 때 
        if(hasWin(board, 'O')){
            if(oCnt == xCnt) {
                return 0;
            }
        }
        
         // X이 이겼는데 O이 X보다 1개 많으면 규칙 위반 
        if(hasWin(board, 'X')){
            if(oCnt == xCnt +1 ) {
                return 0;
            }
        }
        
        return 1;
    }
    
    // 문자 세기
    private int countChar(String str, char c){
        int count = 0;
        char[] chars = str.toCharArray();
        for(char ch : chars) {
            if(ch == c) {
                count++;
            }
        }
        return count;
    }
    
    // 게임 승리 경우
    private boolean hasWin(String[] board, char c) {
        // 가로 검사
        for(int i = 0 ; i < board.length ; i++){
            if(board[i].charAt(0) == c &&
               board[i].charAt(1) == c &&
               board[i].charAt(2) == c) {
                return true;
            }
        }
        
        // 세로 검사
        for(int i = 0 ; i < board.length ; i++){
            if(board[0].charAt(i) == c &&
               board[1].charAt(i) == c &&
               board[2].charAt(i) == c) {
                return true;
            }
        }
        
        // 대각선 검사
        if(board[0].charAt(0) == c &&
           board[1].charAt(1) == c &&
           board[2].charAt(2) == c ) {
                return true;
        }
        if(board[0].charAt(2) == c &&
           board[1].charAt(1) == c &&
           board[2].charAt(0) == c ) {
                return true;
        }
        return false;
    }
}

```

- 모든 반례를 찾는 것이 힘들었다. 
