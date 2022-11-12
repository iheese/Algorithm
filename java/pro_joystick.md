- 조이스틱
```java
class Solution {
		public int solution(String name) {
			int sum=0;
			int move = name.length()-1; // 계속 >으로 이동했을 때
			for (int i = 0; i < name.length(); i++) {
				if(name.charAt(i)<='N'){
					sum+=(name.charAt(i)-65); //A문자 유니코드값이 65로 시작
				}else{
					sum+=(26-(name.charAt(i)-65)); //Z부터 1, W:2 ...
				}

				//A의 위치를 구하자
				int index = i+1;
				//다음 인덱스가 중간에 있는 A라면
				while(index < name.length() && name.charAt(index)=='A'){
					index++;
				}
				// >으로 쭉가는것과 i까지 갔다가 다시 i만큼 돌아가서 맨뒤로 가는 것 중  최솟값
				move = Math.min(move, i * 2 + name.length() - index);
				// 아예 먼저 맨뒤로 먼저 갔다가 다시 시작점으로 돌아와서 i까지 가는 것 중 최솟값
				move = Math.min(move, (name.length() - index) * 2 + i);
			}


			return sum+move;
		}
	}
	```
