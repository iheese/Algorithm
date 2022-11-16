```java
import java.util.ArrayList;
import java.util.Collections;
import java.util.Comparator;
import java.util.List

class Solution {
		public String solution(int[] numbers) {
			List<String> list = new ArrayList<>();
			String answer = "";

			for(int n : numbers){ //int -> String
				list.add(Integer.toString(n));
			}

			Collections.sort(list, new Comparator<String>() {
				@Override
				public int compare(String o1, String o2) {
					return (o2+o1).compareTo(o1+o2); //리턴값이 음수 내림차순
					//return (o1+o2).compareTo(o2+o1); 리턴값이 양수 오름차순
				}
			});  //list string 합친거 비교

			if(list.get(0).equals("0")) return "0"; //첫 글자가 0이면 0리턴

			for(String str : list){
				answer+=str; //문자열 이어 붙이기
			}
			return answer;
		}
	}
```
