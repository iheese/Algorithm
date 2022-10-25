	```java
	class Solution {
		boolean solution(String s) {
			Stack<Character> stack = new Stack<>(); //stack 이용하기

			for(char c : s.toCharArray()){ //String을 char 배열로 만들어줌
				if(c==')'){ //)가 먼저 나올 떼
					if(stack.isEmpty()){ //비어있으면
						return false; //메소드 끝!
					}
					stack.pop(); //아니면 젤 위에 있는거 빼고
				}else{
					stack.push(c); // ( 면 넣기
				}
			}
			if(stack.isEmpty()) return true; //다 돌았을 때 비어있으면 true
			else return false; //뭔가 남아있으면 false
		}
	}
	```
