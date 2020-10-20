[네트워크](https://programmers.co.kr/learn/courses/30/lessons/43162)

1. Java(DFS)
```java
class Solution {
    public void dfs(int[][] com, boolean[] check, int cur) {
        check[cur] = true;
        for(int i=0; i < com.length; i++) {
            if(com[cur][i] == 0 || check[i]) continue;
            dfs(com, check, i);
        }
    }
    public int solution(int n, int[][] computers) {
        int answer = 0;
        boolean[] check = new boolean[n];
        for(int i=0; i < n; i++) {
            if(check[i]) continue;
            answer++;
            dfs(computers, check, i);
        }
        return answer;
    }
}
```
