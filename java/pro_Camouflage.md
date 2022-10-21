```
import java.io.IOException;
import java.util.HashMap;

class Solution {
        public int solution(String[][] clothes) {
            int answer = 1;
            HashMap<String, Integer> map = new HashMap<>(); //종류 별로 갯수를 저장할 해시맵
            for (int i = 0; i < clothes.length; i++) { 
                String kind = clothes[i][1]; //종류 확인
                if(!map.containsKey(kind)) { //종류가 없으면
                    map.put(kind, 1); //종류랑 1 넣어주고
                }else{ //종류가 있으면
                    map.put(kind, map.get(kind) + 1); //종류에 1 더해주기
                }
            }
            for (Integer i: map.values()){
                answer *= (i+1); // 해당 종류 옷을 안입었을 경우를 포함하여 곱하기 //상의: 1번상의, 2번상의, 안입었을때
            }
            answer=answer-1; //하지만 모든 옷을 안입은 경우는 없다
            return answer;
        }
    }
    ```
