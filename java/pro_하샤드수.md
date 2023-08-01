```java
class Solution {
    public boolean solution(int x) {
        int sum=0;
        int temp = x;
        while(temp/10 != 0){
            sum += temp%10;
            temp=temp/10;
        }
        sum += temp%10;
        return x%sum == 0 ? true: false;
    }
}

```
