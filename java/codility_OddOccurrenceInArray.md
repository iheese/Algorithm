```
//OddOccurrencesInArray

// 내꺼 11점...ㅠㅠㅠ
	class Solution {
		public int solution(int[] A) {
			int ans=0;
			for (int j = 0; j < A.length; j++) {
				for (int i =0; i < A.length; i++) {
					if (A[j] == A[i]) {
							break;
					}else{
						ans=A[j];
					}
				}
			}
			return ans;
		}
	}

// 해쉬셋을 이용한 방법
    public int solution(int[] A) {
        int answer = -1;
        HashSet<Integer> hs = new HashSet<>();

        int size = A.length;
        for(int i=0 ; i<size ; i++) {
            if( hs.contains(A[i]) ){
                //존재
                hs.remove(A[i]);
            }
            else {
                //없으면
                hs.add(A[i]);
            }
        }
        ArrayList<Integer> al = new ArrayList<>(hs);
        answer = al.get(0);
        return answer;
    }

//xor 연산 이용한 방법

class Solution{
	pulbic int solution(int[] A){
	int answer = 0;
	for(int num : A){
		answer ^=num;
	}
	return answer;
	}
}

```
