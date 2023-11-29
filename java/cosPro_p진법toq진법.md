```java
 public String solution(String s1, String s2, int p, int q) {
        // 여기에 코드를 작성해주세요.
        String answer = "";
		// Integer.parseInt(s1, p) 처럼 p진법으로 변환한 것 10진법으로 변경해서 계산
		int sum = Integer.parseInt(s1, p) + Integer.parseInt(s2, p);
				// 10진법으로 변환한거 q진법으로 변환하여 String으로 리턴
        return Integer.toString(sum, q);
    }
```
