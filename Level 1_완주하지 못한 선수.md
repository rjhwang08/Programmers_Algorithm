1. 이중 for문 사용(시간 초과) <- 오답
```java
class Solution {
    public String solution(String[] participant, String[] completion) {
        String answer = "";
        
        for(String pname : participant){
            boolean flag = false;
            for(int i=0; i < completion.length; i++){
                if(pname.equals(completion[i])){
                    flag = true;
                    completion[i] = "";
                    break;
                }
            }
            if(flag == false){
                answer = pname;
                break;
            }
        }
        return answer;
    }
}
```

2. Hash 사용 O 풀이
```java
import java.util.*;

class Solution {
    public String solution(String[] participant, String[] completion) {
        String answer = "";
        Map<String, Integer> hashMap = new HashMap<>();
        int val = 0;
        
        for(String pname : participant){
            if(!hashMap.containsKey(pname))
                hashMap.put(pname, 1);
            else{
                val = hashMap.get(pname) + 1;
                hashMap.put(pname, val);
            }
        }
        
        for(String cname : completion){
            val = hashMap.get(cname) - 1;
            hashMap.put(cname, val);
        }
        
        for(String key : hashMap.keySet()){
            if(hashMap.get(key) == 1){
                answer = key;
                break;
            }
        }
        return answer;
    }
}
```

3. Hash 사용 X 풀이(배열을 정렬 후 비교)
```java
import java.util.*;

class Solution {
    public String solution(String[] participant, String[] completion) {
        Arrays.sort(participant);
        Arrays.sort(completion);
        
        int i;
        for(i = 0; i < completion.length; i++){
            if(!participant[i].equals(completion[i]))
                return participant[i];;
        }
        return participant[i];
    }
}
```
