[타겟 넘버](https://programmers.co.kr/learn/courses/30/lessons/43165)

1. Java(DFS)
```java
class Solution {
    public int answer = 0;
    public void dfs(int[] numbers, int target, int cur, int sum) {
        if(cur == numbers.length) {
            if(sum == target) answer++;
            return;
        }
        dfs(numbers, target, cur+1, sum + numbers[cur]);
        dfs(numbers, target, cur+1, sum + numbers[cur]*(-1));
    }
    
    public int solution(int[] numbers, int target) {
        dfs(numbers, target, 0, 0);
        return answer;
    }
}
```
