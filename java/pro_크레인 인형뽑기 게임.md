```
import java.io.IOException;
import java.util.Stack;

public class Main {
	
	
	public static void main(String[] args) throws IOException {
		int[][] board = {{0,0,0,0,0},{0,0,1,0,3},{0,2,5,0,1},{4,2,4,4,2},{3,5,1,3,1}};
		int[] moves = {1,5,3,5,1,2,1,4};

		System.out.println(Solution.solution(board, moves));

	}

	static class Solution {
		static public int solution(int[][] board, int[] moves) {
			Stack<Integer> stack = new Stack<>();
			int answer = 0;

			for (int i = 0; i < moves.length; i++) {
				for (int j = 0; j <board.length ; j++) {
					if(board[j][moves[i]-1] !=0 ){
						if(stack.isEmpty()){
							stack.push(board[j][moves[i]-1]);
						}else{
							if(stack.get(stack.size()-1)==board[j][moves[i]-1]){
								answer++;
								stack.pop();
							}else{
								stack.push(board[j][moves[i]-1]);
							}
						}
						board[j][moves[i]-1]=0;
						break;
					}
				}
			}

			return answer*2;
		}
	}
}
```
