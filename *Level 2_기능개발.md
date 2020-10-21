[기능개발](https://programmers.co.kr/learn/courses/30/lessons/42586)

1. Java(내 풀이)
```java
import java.util.ArrayList;
class Solution {
    public int[] solution(int[] progresses, int[] speeds) {
        int[] answer = {};
        ArrayList<Integer> list = new ArrayList<Integer>();
        int cur = 0;
        while(true) {
            for(int i=0; i < progresses.length; i++) {
                if(progresses[i] >= 100) continue;
                progresses[i] += speeds[i];
            }
            int cnt = 0;
            for(int i=cur; i < progresses.length; i++) {
                if(progresses[i] < 100) break;
                else {
                    cur = i+1;
                    cnt++;
                }
            }
            if(cnt > 0) list.add(cnt);
            if(cur >= progresses.length) break;
        }
        answer = new int[list.size()];
        for(int i=0; i < list.size(); i++)
            answer[i] = list.get(i);
        return answer;
    }
}
```

2. Java(다른 사람 풀이)
```java
import java.util.ArrayList;
class Solution {
    public int[] solution(int[] progresses, int[] speeds) {
        int[] answer = {};
        int[] days = new int[101];
        int day = 0;
        for(int i=0; i < progresses.length; i++) {
            while(progresses[i] + day*speeds[i] < 100)
                day++;
            days[day]++;
        }
        
        ArrayList<Integer> list = new ArrayList<Integer>();
        for(int i=1; i <= 100; i++)
            if(days[i] != 0) list.add(days[i]);
        
        answer = new int[list.size()];
        for(int i=0; i < list.size(); i++)
            answer[i] = list.get(i);
        return answer;
    }
}
```
