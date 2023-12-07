```java
import java.util.*;

class Solution {
    public int[][] solution(int[][] data, String ext, int val_ext, String sort_by) {
        
        List<Data> list = new ArrayList<>();
        for(int i = 0 ; i < data.length; i++) {
            list.add(new Data(data[i][0],data[i][1],data[i][2],data[i][3])); 
        }
        
        List<Data> answerList = new ArrayList<>();
        
        for(Data d : list) {
            if(ext.equals("code")) {
                if(d.getCode() < val_ext) {
                    answerList.add(d);
                }
            } else if(ext.equals("date")) {
                if(d.getDate() < val_ext) {
                    answerList.add(d);
                }
            } else if(ext.equals("maximum")) {
                if(d.getMaximum() < val_ext) {
                    answerList.add(d);
                }
            } else {
                if(d.getRemain() < val_ext) {
                    answerList.add(d);
                }
            }
        } 
        
        if(sort_by.equals("code")) {
            Collections.sort(answerList, (a,b) -> a.getCode() - b.getCode());
        } else if(sort_by.equals("date")) {
            Collections.sort(answerList, (a,b) -> a.getDate() - b.getDate());  
        } else if(sort_by.equals("maximum")) {
            Collections.sort(answerList, (a,b) -> a.getMaximum() - b.getMaximum());    
        } else {
            Collections.sort(answerList, (a,b) -> a.getRemain() - b.getRemain());    
        }
        
        int[][] answer = new int[answerList.size()][4];
        
        for(int i = 0 ; i< answerList.size(); i++) {
            answer[i][0] = answerList.get(i).getCode();
            answer[i][1] = answerList.get(i).getDate();
            answer[i][2] = answerList.get(i).getMaximum();
            answer[i][3] = answerList.get(i).getRemain();
        }
        
        return answer;
    }
    
    static class Data {
        private int code;
        private int date;
        private int maximum;
        private int remain;
        
        public Data(int code, int date, int maximum, int remain) {
            this.code = code;
            this.date = date;
            this.maximum = maximum;
            this.remain = remain;
        }
        
        public int getCode() {
            return this.code;
        }
        public int getDate() {
            return this.date;
        }
        public int getMaximum() {
            return this.maximum;
        }
        public int getRemain() {
            return this.remain;
        }
    }
}

```
