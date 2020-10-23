[]()

1. Java(해시)
```java
import java.util.*;
class Solution {
    public int solution(String[][] clothes) {
        int answer = 1;
        HashMap<String, Integer> hashMap = new HashMap<String, Integer>();
        
        // 옷 종류를 Key, 그리고 해당 종류에 속하는 옷 개수를 Value(옷 종류가 중요하지 해당 옷이 어떤 옷인지는 중요치 않음)
        for(int i=0 ; i < clothes.length; i++)
            hashMap.put(clothes[i][1], hashMap.getOrDefault(clothes[i][1], 0) + 1);
        
        // 종류에 1을 더해서 곱하는 이유는 해당 종류를 고르지 않는 경우의 수를 포함하기 위해서임
        for(Map.Entry<String, Integer> entry : hashMap.entrySet())
            answer *= (entry.getValue() + 1);
        // 마지막으로 리턴 값에서 1을 빼주는 이유는, 옷을 하나도 고르지 않는 경우를 빼주기 위해서이다.
        return answer - 1;
    }
}
```
