1. 풀이
```java
import java.util.Arrays;
class Solution {
    public int[] solution(int[] array, int[][] commands) {
        int[] answer = new int[commands.length];
        int[] subArray = {};
        
        for(int i=0; i < commands.length; i++){
            int len = commands[i][1] - commands[i][0] + 1;
            subArray = new int[len];
            for(int j=0; j < len; j++)
                subArray[j] = array[j+commands[i][0]-1];
            Arrays.sort(subArray);
            answer[i] = subArray[commands[i][2]-1];
        }
        
        return answer;
    }
}
```

2. 다른 사람의 풀이(Arrays.copyOfRange 이용)
```java
import java.util.Arrays;
class Solution {
    public int[] solution(int[] array, int[][] commands) {
        int[] answer = new int[commands.length];

        for(int i=0; i<commands.length; i++){
            int[] temp = Arrays.copyOfRange(array, commands[i][0]-1, commands[i][1]);
            Arrays.sort(temp);
            answer[i] = temp[commands[i][2]-1];
        }

        return answer;
    }
}
```
