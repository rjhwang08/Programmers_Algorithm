[네트워크](https://programmers.co.kr/learn/courses/30/lessons/43162)

1. Java(DFS)
```java
class Solution {
    public void dfs(int[][] com, boolean[] check, int cur) {  // cur은 현재 방문한 컴퓨터
        check[cur] = true; // 네트워크에 포함되었으니까 true
        for(int i=0; i < com.length; i++) { // cur과 연결된 컴퓨터를 조사
            if(com[cur][i] == 0 || check[i]) continue; // 연결되어 있지 않거나, 이미 방문했으면 skip
            dfs(com, check, i);
        }
    }
    public int solution(int n, int[][] computers) {
        int answer = 0;
        boolean[] check = new boolean[n]; // n개의 컴퓨터에 대해 이미 네트워크에 포함되어 있는지 체크
        for(int i=0; i < n; i++) {
            if(check[i]) continue;
            answer++; // false라는 것은 아직 방문하지 못했다는 것이므로 i번째 컴퓨터 부터 새로운 네트워크가 생기는 거니까 1
            dfs(computers, check, i);
        }
        return answer;
    }
}
```
