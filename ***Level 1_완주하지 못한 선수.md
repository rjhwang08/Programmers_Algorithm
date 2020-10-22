1. 이중 for문 사용(시간 초과) <- 오답(선수가 100,000명이기 때문에 이중 for문을 사용하면 시간초과가 발생한다.)
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

[Hash 란?](https://hyeonstorage.tistory.com/265)
[Hash 사용법](https://coding-factory.tistory.com/556)
[getOrDefault() 란?](https://highseekmj.tistory.com/20)

2. Hash 사용 O 풀이1
```java
import java.util.*;
class Solution {
    public String solution(String[] participant, String[] completion) {
        String answer = "";
        HashMap<String,Integer> hashMap = new HashMap<>();
        // getOrDefault()는 이미 key가 존재하는 경우 동명이인 처리를 위함임
        for(String s : participant) hashMap.put(s, hashMap.getOrDefault(s,0) + 1); // 이미 존재하면 더해준다.
        for(String s : completion) hashMap.put(s, hashMap.getOrDefault(s,0) - 1); // 기존에 존재하는 참가자에서 완주한 사람을 빼준다.
        
        // keySet하고 또 get하는 건 매우 비효율적인 코드이다. get할 때마다 계속 HashMap을 search하기 때문
        // 따라서 key, value를 같이 가져올 때는 항상 entrySet을 사용해야 한다!
        for(Map.Entry<String, Integer> entry : hashMap.entrySet()) {
            if(entry.getValue() != 0) {
                answer = entry.getKey();
                break;
            }
        }
        return answer;
    }
}
```

3. Hash 사용 O 풀이2
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

4. Hash 사용 X 풀이(배열을 정렬 후 비교)
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
