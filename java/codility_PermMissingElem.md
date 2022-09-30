```
//PermMissingElem
	static class Solution {
		public int solution(int[] A) {
			int sum = (A.length+1)*(A.length+2)/2;
			for (int i = 0; i < A.length; i++) {
				sum-=A[i];
			}
			return sum;
			}
		}
		
	static class Solution {
		public int solution(int[] A) {
			Arrays.sort(A);
			for (int i = 0; i < A.length; i++) {
				if(i+1 != A[i]) return i+1;
			}
			return A.length+1;
			}
		}
```
