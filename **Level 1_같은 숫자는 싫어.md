!! 시간 효율 고려

1. 풀이 1(시간 초과.. 원인은 잘...)
```java
import java.util.*;

public class Solution {
    public int[] solution(int []arr) {
        int[] answer = {};
        ArrayList<Integer> list = new ArrayList<>();
        for(int num : arr) list.add(num);
        
        for(int i=0; i < list.size() - 1; i++){
            if(list.get(i) == list.get(i+1))
                list.remove(i--);
        }
        answer = new int[list.size()];
        for(int i=0; i < list.size(); i++)
            answer[i] = list.get(i);
        
        return answer;
    }
}
```

2. 다른 사람의 풀이 1(애초에 ArrayList에 넣을 때 이전 숫자를 비교하여 조건에 맞는 숫자만 넣기)
```java
import java.util.*;

public class Solution {
    public int[] solution(int []arr) {
        int[] answer = {};
        ArrayList<Integer> list = new ArrayList<>();
        int preNum = 10;
        for(int i=0; i < arr.length; i++){
            if(arr[i] != preNum){
                list.add(arr[i]);
                preNum = arr[i];
            }
        }
        answer = new int[list.size()];
        for(int i=0; i < list.size(); i++)
            answer[i] = list.get(i);
        
        return answer;
    }
}
```

3. 다른 사람의 풀이 2
```java
import java.util.*;

public class Solution {
    public int[] solution(int []arr) {
        List<Integer> list = new ArrayList<Integer>();
        list.add(arr[0]);

        for (int i = 1; i < arr.length; i++) {

            if (arr[i] != arr[i - 1])
                list.add(arr[i]);
        }

        int[] answer = new int[list.size()];

        for (int i = 0; i < list.size(); i++)
            answer[i] = list.get(i);

        return answer;
    }
}
```
