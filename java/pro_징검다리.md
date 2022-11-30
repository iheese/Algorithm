```java
class Solution {
		public int solution(int distance, int[] rocks, int n) {
			int answer = 0;
			int left = 1;
			int right = distance;

			Arrays.sort(rocks); //rocks 오름차순 정렬
			while(left <= right){  // 이분 탐색 시작
				int mid = (left + right)/2;
				int removeRocks = 0; //제거해야하는 돌의 갯수
				int before = 0; //이전 돌의 위치, 돌이 제거되지 않으면 돌 위치를 앞으로

				for(int rock : rocks){ //가까운 돌부터 순회
					if(rock-before < mid){ //mid로부터먼 것부터 돌을 제거한다.
						removeRocks++;
					}else{
						before = rock; // mid 넘어가면 before을 업데이트
					}
				}
				if(distance - rocks[rocks.length-1] < mid){  //마지막 돌과 도착점 사이 거리 확인
					removeRocks++;
				}
				if(removeRocks <= n){ // 주어진 n보다 작거나 같은 만큼 돌을 없애서 최솟값 x를 만들수 있다.
					answer=mid;
					left = mid + 1;
				}else{
					right = mid - 1;
				}
			}
			return answer;
		}
	}
	```
