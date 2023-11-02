```java
import java.util.*;
class Solution{
	
	public static void main(String []argh)
	{
		Scanner sc = new Scanner(System.in);
		
		while (sc.hasNext()) {
            Stack<Character> stack = new Stack<>();
			String input=sc.next();
            //Complete the code
            char[] chars = input.toCharArray();
            boolean check = true;
            for (char c : chars) {
                if (c == '}' || c == ']' || c == ')') {
                    if (stack.isEmpty()) {
                        // 스택이 비어있고 닫힌 괄호 있을 땐 바로 나가서 false 리턴하게 구현
			check = false;
                        break;
                    } else if ((c == '}' && stack.peek() == '{')
                            ||(c == ']' && stack.peek() == '[')
                            ||(c == ')' && stack.peek() == '(')) {
                        stack.pop();
                    }
                } else {
                    stack.push(c);
                }
            }
		// 위 주석 예시 말고는 스택 비어있는지 확인 후 리턴
            if(!check) {
                System.out.println(false);
            } else {
                System.out.println(stack.isEmpty());
            }
		}
	}
}
```

```java
import java.util.*;
class Solution{
    public static void main(String[] args) {
        Scanner sc = new Scanner(System.in);
        
        while (sc.hasNext()) {
            String input = sc.next();
            //Complete the code
            boolean isValid = isBracketValid(input);
            System.out.println(isValid);
        }
    }

    public static boolean isBracketValid(String input) {
        Stack<Character> stack = new Stack<>();
        for (char c : input.toCharArray()) {
            if (isClosingBracket(c)) {
                if (stack.isEmpty() || !isMatchingBracket(stack.pop(), c)) {
                    return false;
                }
            } else {
                stack.push(c);
            }
        }
        return stack.isEmpty();
    }

    public static boolean isClosingBracket(char c) {
        return c == '}' || c == ']' || c == ')';
    }

    public static boolean isMatchingBracket(char opening, char closing) {
        return (opening == '{' && closing == '}') ||
               (opening == '[' && closing == ']') ||
               (opening == '(' && closing == ')');
    }
}
```
