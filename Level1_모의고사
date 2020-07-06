1. 풀이1
```java
class Solution {
    public int[] solution(int[] answers) {
        int[] answer = {};
        int[] st1 = {1, 2, 3, 4, 5};
        int[] st2 = {2, 1, 2, 3, 2, 4, 2, 5};
        int[] st3 = {3, 3, 1, 1, 2, 2, 4, 4, 5, 5};
        int[] cnt = new int[3];

        for(int i=0; i < answers.length; i++){
            if(answers[i] == st1[i%5]) cnt[0]++;
            if(answers[i] == st2[i%8]) cnt[1]++;
            if(answers[i] == st3[i%10]) cnt[2]++;
        }

        int max = cnt[0];
        for(int i=1; i < 3; i++){
            if(cnt[i] > max) max = cnt[i];
        }

        int num = 0;
        for(int i=0; i < 3; i++){
            if(cnt[i] == max) num++;
        }
        answer = new int[num];

        num = 0;
        for(int i=0; i < 3; i++){
            if(cnt[i] == max)
                answer[num++] = i + 1;
        }

        return answer;
    }
}
```

2. 풀이 2(다른 사람 답안)
```java
import java.util.ArrayList;
class Solution {
    public int[] solution(int[] answer) {
        int[] a = {1, 2, 3, 4, 5};
        int[] b = {2, 1, 2, 3, 2, 4, 2, 5};
        int[] c = {3, 3, 1, 1, 2, 2, 4, 4, 5, 5};
        int[] score = new int[3];
        for(int i=0; i<answer.length; i++) {
            if(answer[i] == a[i%a.length]) {score[0]++;}
            if(answer[i] == b[i%b.length]) {score[1]++;}
            if(answer[i] == c[i%c.length]) {score[2]++;}
        }
        int maxScore = Math.max(score[0], Math.max(score[1], score[2]));
        ArrayList<Integer> list = new ArrayList<>();
        if(maxScore == score[0]) {list.add(1);}
        if(maxScore == score[1]) {list.add(2);}
        if(maxScore == score[2]) {list.add(3);}
        return list.stream().mapToInt(i->i.intValue()).toArray();
    }
}
```
