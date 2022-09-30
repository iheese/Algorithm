
```
//TapeEquilibrium
	static class Solution {
		public int solution(int[] A) {
			int sum=0;
			for (int i = 0; i < A.length; i++) {
				sum+=A[i];
			}
			ArrayList<Integer> arr = new ArrayList<>();
			int acum=0;
			for (int i = 0; i < A.length; i++) {
				acum+=A[i];
				arr.add(Math.abs(sum-acum*2));
			}
			Collections.sort(arr);
			return arr.get(0);
		}
	}
	
	    public static int solution(int[] A) {
        List sumList = new ArrayList();
 
        int left = 0;
        int right = 0;
        int sum = 0;
 
        for(int i : A)  sum += i;
 
        for(int j = 1 ; j < A.length ; j++){
            left += A[j-1];
            right = sum - left;
            sumList.add(Math.abs(left - right));
        }
 
        return (int)Collections.min(sumList);
    }
```
