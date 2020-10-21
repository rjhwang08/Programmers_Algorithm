[여행경로](https://programmers.co.kr/learn/courses/30/lessons/43164)

1. Java(DFS)_처음 풀이
```java
class Solution {
    public String[] answer = {}; // 정답 문자열 배열
    public void  dfs(String[][] tickets, boolean[] check, int step, int cur, String s) {
    // step:항공권을 몇개 사용했는지 카운트, cur:현재 출발한 항공권, s:도착 지역을 문자열 형태로 이어 붙임(sum과 같은 용도)
        if(step >= tickets.length) {
            String[] ans = s.split(",");
            
            if(answer.length == 0) answer = ans; // 정답 배열이 비어있는 경우
            else {
                // 가능한 경로가 2개 이상일 경우 알파벳 순서가 앞서는 경로를 찾는다
                for(int i=0; i < ans.length; i++) {
                  // 도시 하나씩 차례로 알파벳 순서 비교
                	if(ans[i].compareTo(answer[i]) == 0) continue;
                	else if(ans[i].compareTo(answer[i]) < 0) { // ans에 있는 도시가 더 빠른 경우
                        answer = ans;
                        break;
                    }
                    else break;
                }
            }
            
            return;
        }
        
        for(int next=0; next < tickets.length; next++) {
            if(check[next]) continue; // 이미 사용한 항공권이면 skip
            
            // 현재 사용한 항공권의 도착지가 다음 사용할 항공권의 출발지와 같으면 dfs
            if(tickets[cur][1].equals(tickets[next][0])) {
                check[next] = true;
                dfs(tickets, check, step+1, next, s + "," + tickets[next][1]);
                check[next] = false;
            }
        }
    }
    
    public String[] solution(String[][] tickets) {
        boolean[] check = new boolean[tickets.length];
        
        for(int i=0; i < tickets.length; i++) {
            if(tickets[i][0].equals("ICN")) { // i번째 항공권의 출발지가 ICN면 dfs
                check[i] = true;
                dfs(tickets, check, 1, i, "ICN," + tickets[i][1]);
                check[i] = false;
            }
        }
        
        return answer;
    }
}
```

2. Java(DFS)_위에 코드 속도 향상
```java
class Solution {
    public String answer = "";
    public void  dfs(String[][] tickets, boolean[] check, int step, int cur, String s) {
        if(step >= tickets.length) { // 이 부분에서 불필요한 과정을 줄여, 코드는 줄이고 속도는 향상시켰다.
            // 방법은 s를 문자열 배열로 다시 나누지 않고 그 자체로 비교했다는 것이다.
            if(answer.length() == 0) answer = s;
            else if(s.compareTo(answer) < 0) answer = s;
            return;
        }
        
        for(int next=0; next < tickets.length; next++) {
            if(check[next]) continue; // 이미 사용한 항공권이면 skip
            
            if(tickets[cur][1].equals(tickets[next][0])) {
                check[next] = true;
                dfs(tickets, check, step+1, next, s + "," + tickets[next][1]);
                check[next] = false;
            }
        }
    }
    
    public String[] solution(String[][] tickets) {
        boolean[] check = new boolean[tickets.length];
        
        for(int i=0; i < tickets.length; i++) {
            if(tickets[i][0].equals("ICN")) {
                check[i] = true;
                dfs(tickets, check, 1, i, "ICN," + tickets[i][1]);
                check[i] = false;
            }
        }
        
        return answer.split(",");
    }
}
```
