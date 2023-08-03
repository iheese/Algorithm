```java
class Solution {
    public int[] solution(String[] wallpaper) {

        char[][] arr = new char[wallpaper.length][wallpaper[0].length()];
        int xmin=50;
        int ymin=50;
        int xmax=0;
        int ymax=0;

        for (int i=0; i<wallpaper.length; i++) {
            arr[i]= wallpaper[i].toCharArray();
        }

        for (int i = 0; i< arr.length; i++) {
            for (int j = 0; j< arr[i].length ;j++){
                if(arr[i][j] == '#'){
                    xmin=Math.min(xmin, i);
                    ymin=Math.min(ymin, j);
                    xmax=Math.max(xmax, i+1);
                    ymax=Math.max(ymax, j+1);
                }
            }
        }
        int[] answer = {xmin, ymin, xmax, ymax};
        return answer;
    }
}
```
