```java
    public int solution(int a, int b) {
        // 여기에 코드를 작성해주세요.
        int answer = 0;
				// 제곱이나 세제곱이면 값 더해주기
				for (int i = a ; i <= b ; i++) {
					if(checkPower2(i)) answer++;
					if(checkPower3(i)) answer++; 
					
				}
				
        return answer;
    }
		// 제곱인지 확인
		private boolean checkPower2(int a){
			for(int i = 2 ; i <= Math.sqrt(a) ; i++){
				if(Math.pow(i, 2) == a && isPrime(i)) {
					return true;
				} 
			}
			return false;
		}
		// 세제곱인지 확인
		private boolean checkPower3(int a){
			for(int i = 2 ; i <= Math.sqrt(a) ; i++){
				if(Math.pow(i, 3) == a && isPrime(i)) {
					return true;
				} 
			}
			return false;
		}
		// 소수인지 확인
		private boolean isPrime(int a) {
			for(int i = 2 ; i <= Math.sqrt(a) ; i++){
				if(a % i == 0) {
					return false;
				} 
			}
			return true;
		}
```

- 다른 답

```java
  public int solution(int a, int b) {
        // 여기에 코드를 작성해주세요.
        int answer = 0;
			
        //a와 b가 10억 이하 자연수이므로 1천 이하의 소수의 제곱수와 세제곱수만 가능			
        // 1천 이하의 소수를 구하고, 소수의 제곱수와 세제곱수가 a,b 사이에 들어가는 개수를 구함			
        //1천 이하의 소수를 구하기
        ArrayList<Integer> sosu = new ArrayList<>();

        boolean isSosu;
        //2부터 1000까지의 수가 소수인지 검사
        for(int i=2;i<1000;i++){
            isSosu=true;
            //i가 j로 나누어 떨어지면 소수가 아님(i가 2일때는 for문 실행되지 않음)
            for(int j=2;j<i;j++){
                if(i%j==0){
                    isSosu=false;
                    break;
                } 
            }
            //for문 수행결과 isSosu가 true이면 sosu ArrayList에 추가
            if(isSosu){
                sosu.add(i);						
            }					
        }
        //소수의 제곱수와 세제곱수의 개수 구하기			
        for(int i =0;i<sosu.size();i++){					
            //소수의 제곱수가 a이상 b이하이면 answer를 1증가
            if((Math.pow(sosu.get(i),2)>=a) && (Math.pow(sosu.get(i),2)<=b)){												
                answer++;
            } 
            //소수의 세제곱수가 a이상 b이하이면 answer를 1증가
            if((Math.pow(sosu.get(i),3)>=a) && (Math.pow(sosu.get(i),3)<=b)){												
                answer++;
            }  					
        }
      	return answer;
//출처: https://woogong80.tistory.com/130
```
