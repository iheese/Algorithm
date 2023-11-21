```java
import java.util.*;

class Solution {
    public int[] solution(String[] genres, int[] plays) {
        List<Integer> answer = new ArrayList<>();
        // 누적합 구하는 map
        Map<String, Integer> num = new HashMap<>();
        // 장르별 고유번호와 재생횟수 map 저장
        Map<String, HashMap<Integer, Integer>> music = new HashMap<>();
        
        for(int i = 0 ; i < genres.length ; i++) {
            // 재생횟수 누적합
            num.put(genres[i], num.getOrDefault(genres[i], 0) + plays[i]);
                        
            if(!music.containsKey(genres[i])) {
                HashMap<Integer, Integer> map = new HashMap<>();
                map.put(i, plays[i]);
                music.put(genres[i], map);
            } else {
                music.get(genres[i]).put(i, plays[i]);
            }
        }
        // 누적합의 장르 추출
        List<String> keySet = new ArrayList(num.keySet());
        // 정렬
        Collections.sort(keySet, (s1, s2) -> num.get(s2)-(num.get(s1)));
        
        for(String key : keySet) {
            Map<Integer, Integer> map = music.get(key);
            List<Integer> musicKey = new ArrayList(map.keySet());
            // 재생횟수 기준으로 내림차순
            Collections.sort(musicKey, (s1, s2) -> map.get(s2) - (map.get(s1)));
            
            answer.add(musicKey.get(0));
            
            if(musicKey.size() > 1) {
                answer.add(musicKey.get(1));
            }
            
        }        
        
        return answer.stream().mapToInt(i -> i).toArray();
    }
}
```
