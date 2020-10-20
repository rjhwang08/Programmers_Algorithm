[단어 변환](https://programmers.co.kr/learn/courses/30/lessons/43163)

1. Java(DFS)
```java
class Solution {
    public int answer = 0;
    public void dfs(String cur, String target, String[] words, boolean[] check, int cnt) {
    // cur은 현재 단어, target은 목표 단어, cnt는 단계 횟수
        // 종료 조건
        if(cnt > words.length) return; // cnt가 단어 집합의 크기보다 커진다는 것은 모든 단어들을 탐색했지만 정답에 도달하지 못했다는 의미이므로 종료 
        if(cur.equals(target)) { // 현재 단어가 목표 단어에 도달한 경우
            if(answer == 0) answer = cnt;
            else answer = Math.min(answer, cnt);
            return;
        }
        
        // 단어 집합에 있는 단어들을 탐색한다.
        for(int i=0; i < words.length; i++) {
            if(check[i]) continue; // 이미 사용한 단어면 skip
            check[i] = true;
            int c = 0; // i번째 단어가 cur과 몇 개가 다른지 카운트
            for(int j=0; j < cur.length(); j++)
                if(cur.charAt(j) != words[i].charAt(j)) c++;
            if(c == 1) dfs(words[i], target, words, check, cnt+1); // 한 개의 문자만 바꿀 수 있으므로 c가 1인 경우만 dfs를 돌린다.
            check[i] = false; // 중요! 반드시 사용하고 나면 풀어줘야 한다!
        }
    }
    
    public int solution(String begin, String target, String[] words) {
        boolean[] check = new boolean[words.length]; // 해당 단어를 사용했는지 체크
        dfs(begin, target, words, check, 0);
        return answer;
    }
}
```
