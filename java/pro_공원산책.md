```java

class Solution {
    public int[] solution(String[] park, String[] routes) {
        int sx = 0;
        int sy = 0;
        char[][] arr = new char[park.length][park[0].length()];
        
        // 2차원 배열화
        for (int i = 0; i < park.length; i++) {
            arr[i] = park[i].toCharArray();
            
            // 시작 값 등록
            if (park[i].contains("S")) {
                sy = i;
                sx = park[i].indexOf("S");
            }
        }
        
        for (String st : routes) {
            // 방향 정하기
            String way = st.split(" ")[0];
            // 얼마나 갈지 정하기
            int len = Integer.parseInt(st.split(" ")[1]);
            // 이동값 저장할 변수 세팅
            int nx = sx;
            int ny = sy;
            
            // 이동할 만큼 반복문 돌림
            for (int i = 0; i < len; i++) {
                if(way.equals("E")) {
                    nx++;
                }
                if(way.equals("W")) {
                    nx--;
                }
                if(way.equals("S")) {
                    ny++;
                }
                if(way.equals("N")) {
                    ny--;
                }
                // park 외의 범위를 벗어나지 않고 잘 이동하고 있을 때
                if(nx >= 0 && ny >= 0 && ny < arr.length && nx < arr[0].length) {
                    // X를 만나면 반복문 중단
                    if(arr[ny][nx] == 'X') {
                        break;
                    }
                    // 문제없이 잘 이동하면
                    if(i == len -1 ) {
                        // sx, sy 에 이동값 등록
                        sx = nx;
                        sy = ny;
                    }
                }
            }
        }
        int[] answer = {sy, sx};
        return answer;
    }
}
```
