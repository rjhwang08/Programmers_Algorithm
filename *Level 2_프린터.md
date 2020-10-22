[프린터](https://programmers.co.kr/learn/courses/30/lessons/42587)

1. Java(큐)
```java
import java.util.*;
class Solution {
    public int solution(int[] priorities, int location) {
        Integer[] pri_sort = new Integer[priorities.length];  // 우선순위 높은 순으로 정렬 배열
        for(int i=0; i < priorities.length; i++)
            pri_sort[i] = priorities[i];
        // 역순 정렬(Collections를 사용하기 위해 래퍼클래스 Integer 사용)
        Arrays.sort(pri_sort, Collections.reverseOrder());
        // 대기목록 역할을 하는 Queue 생성(우선순위가 아닌, 인덱스로 저장)
        Queue<Integer> q = new LinkedList<Integer>();
        for(int i=0; i < priorities.length; i++) {
            q.add(i);
        }
        
        int cur_max = 0; // 현재 가장 높은 우선순위를 가리킨다.
        while(!q.isEmpty()) {
            // 1) 대기열 해당 인덱스가 가리키는 우선순위가 가장 높은 우선순위인지 비교
            if(priorities[q.peek()] == pri_sort[cur_max]) {
                cur_max++; // 맞으면 다음 우선순위로 이동
                if(q.remove() == location) break; // 인쇄되는 우선순위가 location인지 비교
                continue;
            }
            // 2) 1)에 해당되지 않으면 목록 가장 뒤로 이동
            q.add(q.remove());
        }
        return cur_max;
    }
}
```
