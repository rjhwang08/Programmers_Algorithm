[]()

1. Java(큐)
```java
import java.util.*;
class Solution {
    public int solution(int bridge_length, int weight, int[] truck_weights) {
        Queue<Integer> q = new LinkedList<Integer>();
        int cur = 0; // 현재 들어가야하는 트럭
        int sum = 0; // 다리를 지나가고 있는 트럭 무게의 총합
        int time = 0; // 경과 시간
        int pass_truck = 0; // 지나간 트럭 개수
        while(true) {
            time++;
            // 1) 다리를 지난 트럭을 큐에서 빼준다.
            if(!q.isEmpty() && time - q.element() == bridge_length) {
                q.remove(); // 해당 트럭이 들어온 시간
                sum -= q.remove(); // 다리에 있는 트럭 무게 합에서 빼준다.
                pass_truck++;
            }
            
            // 2) 트럭이 다리를 건넌다.
            if(cur < truck_weights.length && sum + truck_weights[cur] <= weight) {
                sum += truck_weights[cur]; // 들어간 트럭의 무게를 총합에 더해준다.
                q.add(time); // 큐에 현재 시간을 넣는다.
                q.add(truck_weights[cur++]); // 들어간 트럭의 무게를 넣어준다.
            }
            // 3) 종료조건 
            if(pass_truck == truck_weights.length) break;
        }
        
        return time;
    }
}
```
