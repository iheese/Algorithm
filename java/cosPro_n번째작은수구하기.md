```java
List<Integer> list = new ArrayList<>();
    public int solution(int[] card, int n) {
        // 여기에 코드를 작성해주세요.
        int answer = 0;
		// 해당 인덱스가 카드 번호, 인덱스 값이 카드 갯구가 몇개 있는지
		// 1,2,1,3 > 인덱스 1 : 2, 인덱스 2: 1, 인덱스 3: 1
		int[] cardCnt = new int[10];
		// 사용한 카드 갯수, 위 원본하고 비교하면서 재귀를 돈다. 
		int[] curCnt = new int[10];
		
		for(int i = 0; i <card.length ; i++) {
			cardCnt[card[i]]++;
		}
		
		makeNum(cardCnt, curCnt, card.length, 0);
		
		if(list.indexOf(n) >= 0 ) {
			answer = list.indexOf(n)+1;
		} else {
			answer = list.indexOf(n);
		}
		
        return answer;
    }
    
		private void makeNum (int[] cardCnt, int[] curCnt, int lev, int num) {
			if(lev == 0) {
				list.add(num);
				return;
			}
			for(int i = 1; i < 10; i++) {
				if(curCnt[i] < cardCnt[i]) {
					curCnt[i]++;
					makeNum(cardCnt, curCnt, lev -1 , num*10+i);
					curCnt[i]--;
				}
			}	
	}
```
