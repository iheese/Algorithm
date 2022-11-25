```java
class Solution {
        boolean[] visited;
        int answer=51;
        public int solution(String begin, String target, String[] words) {
            visited = new boolean[words.length];
            dfs(words, begin, target, 0);

            if(answer==51) return 0;
            else return answer;
        }

        private void dfs(String[] words, String begin, String target, int count){
                if(begin.equals(target)){ //target에 도달하면 더 작은 횟수를 answer에 저장한다.
                    answer = Math.min(count, answer);
                    return;
                }
                for (int i = 0; i<words.length;i++){
                    if(visited[i]) continue;
                    if(!visited[i] && changeOneWord(begin, words[i])){ //방문하지 않았고 한개만 바뀌었을 때
                        visited[i]=true;  //방문처리
                        dfs(words, words[i], target, count+1); //재귀
                        visited[i]=false;
                }
            }
        }

        private boolean changeOneWord(String word1, String word2){ //다음 단계로 넘어갈 때 한 개만 바뀔 수 있다.
            int count=0;
            char[] charArray1 =word1.toCharArray();
            char[] charArray2 =word2.toCharArray();

            for (int i = 0; i < word1.length(); i++) {
                if(charArray1[i] != charArray2[i]) count++;
            }
            if(count==1){
                return true;
            }
            return false;
        }
    }
    ```
