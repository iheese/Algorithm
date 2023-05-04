import java.util.HashMap;
import java.util.Map;

public class Solution {
    public String[] solution(String[] players, String[] callings) {

        Map<String, Integer> map = new HashMap();

        for (int i = 0; i < players.length; i++) {
            map.put(players[i], i);
        }

        for (String calling : callings) {
            int rank = map.get(calling);
            String front = players[rank-1];
            players[rank]=front;
            players[rank-1] =calling;
            map.put(calling , rank-1);
            map.put(front, rank);
        }
        return players;
        //for 두개 돌렸더니 시간 초과 그럴떄는 자료구조부터 고려해야한다. 
    }
}
