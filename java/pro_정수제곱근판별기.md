```java
class Solution {
    public long solution(long n) {
        double answer = -1;
        double k = Math.sqrt(n);
        if(isInteger(k)){
            answer = Math.pow(k+1,2);
        }
        return (long)answer;
    }
    private boolean isInteger(double num) {
	    return Math.floor(num) == num;
}
//public boolean isInteger(double num) {
//	return num % 1 == 0.0;
//}

//public boolean isInteger(double num) {
//	return num == (int) num;
//}

}
```

```java
1
2
3
4
5
6
7
8
9
10
class Solution {
  public long solution(long n) {
      if (Math.pow((int)Math.sqrt(n), 2) == n) {
            return (long) Math.pow(Math.sqrt(n) + 1, 2);
        }

        return -1;
  }
}
```
