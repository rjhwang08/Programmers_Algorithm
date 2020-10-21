[주식가격](https://programmers.co.kr/learn/courses/30/lessons/42584)

1. Java(이중 for문)
```java
class Solution {
    public int[] solution(int[] prices) {
        int[] answer = new int[prices.length];
        
        for(int i=0; i < prices.length; i++) {
            int cnt = 0;
            for(int j=i+1; j < prices.length; j++) {
                cnt++;
                if(prices[i] > prices[j]) break;
            }
            answer[i] = cnt;
        }
        return answer;
    }
}
```

2. Java(스택)
```java
import java.util.Stack;
class Solution {
    public int[] solution(int[] prices) {
        int[] answer = new int[prices.length];
        Stack<Integer> stack = new Stack<Integer>();  // 스택에 인덱스를 넣어준다.
        
        stack.add(0);
        for(int i=1; i < prices.length; i++) {
            while(!stack.isEmpty() && prices[stack.peek()] > prices[i]) { // 만약 현재 스택의 마지막에 있는 인덱스의 수보다 지금 들어온 인덱스의 수가 작다면
                int idx = stack.pop(); // pop을 해서
                answer[idx] = i - idx; // answer 배열에 인덱스의 차이만큼 넣어준다.
            }
            stack.add(i);
        }
        // 모든 인덱스를 탐색할 때까지 스택에서 나오지 못한 인덱스를 
        while(!stack.isEmpty()) {
                int idx = stack.pop();
                answer[idx] = prices.length - 1 - idx;
        }
        return answer;
    }
}
```
