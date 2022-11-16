// 프로그래머스 신고 결과 받기 성공!
```
import java.util.*;

class Solution {
    public int[] solution(String[] id_list, String[] report, int k) {
        int[] answer = new int[id_list.length]; //정답 정수 배열
        Map<String, HashSet<String>> reported = new HashMap<>(); //신고 당한 사람을 중심으로
        Map<String, Integer> idx = new HashMap<>(); 
        
        for(int i=0;i<id_list.length;i++){
            String name = id_list[i]; //id_list대로 이름을 넣어준다.
            reported.put(name, new HashSet<>()); //신고 당한 사람 이름(key), 신고한사람 이름(value, 중복피함)
            idxMap.put(name, i); //이름에 해당하는 인덱스로 접근하기 위해 인덱스 넣어준다.
         } //초기화
        
        for(String s: report ){ 
            String[] str = s.split(" "); //split으로 값을 분리
            String from =str[0]; //신고자
            String to =str[1]; //신고당한 사람
            reported.get(to).add(from); // 신고 당한 사람의 HashSet에 신고자 이름 넣어준다.
        }
        
        for(int i=0;i<id_list.length;i++){  
            HashSet<String> sent = reported.get(id_list[i]); // 신고자 HashSet을 얻어낸다.
            if(sent.size()>=k){ //k보다 크면
                for(String name :sent){ //이름을 돌면서
                    answer[idx.get(name)]++;  //이름의 해당 idx 순번의 값을 올린다.
                }
            }
        }
 
        return answer; //리턴!
    }
}
```
