```java
import java.util.*;
import java.util.stream.*;

class Solution {
    public int solution(int[] scoville, int K) {
        int answer = 0;
        
        List<Integer> list = Arrays.stream(scoville)
            .boxed()
            .sorted().
            collect(Collectors.toList());
        
        while(list.get(0) < K) {
            if(list.size() == 1  && list.get(0) < K) {
                answer = -1 ;
                break;
            }
            Integer first = list.get(0);
            Integer second = list.get(1);
            list.remove(first);
            list.remove(second);
            list.add(first + second * 2);
            Collections.sort(list);
            answer++;
        }
        
        return answer;
    }
}

```

- 효율성 실패 코드

```java
import java.util.*;

class Solution {
    public int solution(int[] scoville, int K) {
        int answer = 0;
        
        PriorityQueue<Integer> q = new PriorityQueue<>();
        
        for(int i = 0 ; i < scoville.length ; i++) {
            q.add(scoville[i]);
        }
        
        while(q.peek() < K) {
            if(q.size() == 1) {
                return -1;
            }
            q.add(q.poll() + q.poll() *2);
            answer++;
        }
        return answer;
    }
}

```

- PriorityQueue를 사용하면 쉽게 풀리는 문제였다.
- PriorityQueue 생성시 Collections.reverseOrder() 넣어주면 내림차순으로 나온다.

```java
PriorityQueue<Integer> priorityQueue = new PriorityQueue<>(Collections.reverseOrder());
```

- 이외에 람다식(익명홤수)로 호출해서 적을 수도 있고, new Coparator 로 compare 오버라이딩해서 작성할수도 있다.

```java
// 오름차순
int[][] points = {{1,3}, {-2,2}, {-4,1}};

//1. 람다식 이용
Queue<int[]> pq = new PriorityQueue<>((a,b)->(a[0]*a[0]+a[1]*a[1])-(b[0]*b[0]+b[1]*b[1]));

//2. Comparator 이용
Queue<int[]> pq = new PriorityQueue<>(new Comparator<int[]>() {
	@Override
	public int compare(int[] o1, int[] o2) {
		int o1Result = o1[0]*o1[0] + o1[1]*o1[1];
		int o2Result = o2[0]*o2[0] + o2[1]*o2[1];
		return o1Result-o2Result;
	}
});

// 내림차순
//1. 람다식 이용
Queue<int[]> pq = new PriorityQueue<>((a,b)->(b[0]*b[0]+b[1]*b[1])-(a[0]*a[0]+a[1]*a[1]));

//2. Comparator 이용
Queue<int[]> pq = new PriorityQueue<>(new Comparator<int[]>() {
	@Override
	public int compare(int[] o1, int[] o2) {
		int o1Result = o1[0]*o1[0] + o1[1]*o1[1];
		int o2Result = o2[0]*o2[0] + o2[1]*o2[1];
		return o2Result-o1Result;
	}
});

//출처: https://ynzu-dev.tistory.com/entry/JAVA-Priority-Queue우선순위-큐-우선순위-조건-변경하기 [기록:티스토리]

```
