```java
class Solution {
    public int solution(int storey) {
        int answer = 0;
        char[] chars = String.valueOf(storey).toCharArray();
        int[] arr = new int[chars.length];
        for(int i = 0; i< chars.length; i++) {
            arr[i] = chars[i] - '0';
        }
        // 일의 자리부터 확인
        for(int i = arr.length -1 ; i >= 0 ; i--){
            // 5보다 크면 10와 차액을 더하고 위의 자리 수를 1올린다.
            if(arr[i]>5){
                answer += 10-arr[i];
                
                // 마지막이면 1개 더해준다, 1 올라갔을테니/ 아니면 앞의 숫자를 1올려줌
                if(i == 0) {
                    answer++;
                } else {
                    arr[i-1]++;
                }
                // 5일 경우 , 앞자리가 5보다 큰지 확인, 1 올렸을 때 5 이상인 경우만 올리는 것이 더 적게 사용할 수 있음
            }else if(arr[i] == 5 && i>0 && arr[i-1] >=5) {
                arr[i-1]++;
                answer+=5;
            } else {
                answer+=arr[i];
            }
        }
        
        return answer;
    }
}
```

```java
class Solution {
    public int solution(int storey) {
        int answer = 0;
        while (storey != 0) {
            int upperNumber = (storey %100)/10;
            int number = storey % 10;
            if (number > 5 || number == 5 && upperNumber>=5) {
                storey += 10;
                answer += (10 - number);
            } else {
                answer += number;
            }
            storey = storey / 10;
        }  
        return answer;
    }
}
```

- 맨 뒤 2개만 획인하면서 값을 구하는 방식, 이처럼 구현하고 싶었는데..
- UpperNumber는 10의자리, number는 일의 자리/ 일의 자리를 제거해가며 값을 계산


```java
class Solution {
    public int solution(int storey) {
        return storey < 10 ? Math.min(storey, 11 - storey) : Math.min(storey % 10 + solution(storey / 10), 10 - storey % 10 + solution(storey / 10 + 1));
    }
}
```

- 후덜덜
