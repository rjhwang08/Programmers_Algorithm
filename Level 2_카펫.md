[카펫](https://programmers.co.kr/learn/courses/30/lessons/42842)

1. Java
```java
class Solution {
    public int[] solution(int brown, int yellow) {
        int[] answer = new int[2];
        int total = brown + yellow; // 전체 격자 개수
        
        // x, y는 갈색의 세로와 가로(x*y = total, x <= y)
        for(int x=3; x*x <= total; x++) { // 갈색 세로는 최소 3칸 부터
            if(total % x != 0) continue; // 차례로 x가 인수가 맞는지 부터 확인
            int y = total / x;
            
            // r, c는 노란색의 세로와 가로(r*c = yellow, r <= c)
            int r = x - 2; // 갈색은 테두리 1줄 이므로 노란색은 갈색에서 2를 빼면 된다.
            if(yellow % r != 0) continue; // 마찬가지로 인수가 맞는지 확인
            int c = yellow / r;
            if(y-c != 2) continue;
            answer[0] = y; answer[1] = x;
            break;
        }
        
        return answer;
    }
}
```
