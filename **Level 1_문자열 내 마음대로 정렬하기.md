- 못풀었음.. 다른 사람 코드 참조하여 풀이
- 아래 방법 말고 추가로 더 찾아서 공부 [참고](https://sas-study.tistory.com/211)

```java
import java.util.*;

class Solution {
    public String[] solution(String[] strings, int n) {
        String[] answer = new String[strings.length];
        String[] subStrings = new String[strings.length];
        
        for(int i=0; i < strings.length; i++){
            subStrings[i] = strings[i].charAt(n) + strings[i];
        }
        
        Arrays.sort(subStrings);
        for(int i=0; i < subStrings.length; i++)
            answer[i] = subStrings[i].substring(1,subStrings[i].length());
        
        return answer;
    }
}
```
