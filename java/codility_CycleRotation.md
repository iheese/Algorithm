```
	 class Solution {
		public int[] solution(int[] A, int K) {
			for(int j=0;j<K;j++){
				int temp=A[A.length-1];  // 마지막 값 임시저장
				for (int i = A.length-2; i >=0 ; i--) { //마지막제외한 부분부터 앞에 값에 저장
					A[i+1]=A[i];
				}
				A[0]=temp; //마지막값은 첫번째로
			}
			return A;			
            }
		}

```
