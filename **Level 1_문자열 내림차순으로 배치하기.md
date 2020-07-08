[문자열 자르는 방법](https://coding-factory.tistory.com/73)

1. 풀이1(String에 '+'로 이어 붙이기 <- '+'는 매번 새로운 객체를 만들어서 느림)
```java
import java.util.Arrays;
import java.util.Collections;
class Solution {
    public String solution(String s) {
        String answer = "";
        
        String[] arr = new String[s.length()];  // char 배열은 primitive type이라 Collections.reverseOrder()을 사용하지 못함 -> 객체 배열 필요
	arr = s.split("");                   // 글자 하나씩 자르는 방법 1
        //for(int i=0; i < s.length(); i++)  // 글자 하나씩 자르는 방법 2
        //    arr[i] = Character.toString(s.charAt(i));
            
        Arrays.sort(arr, Collections.reverseOrder());
        
        for(String word : arr)
        	answer = answer + word;
        
        return answer;
    }
}
```

2. 풀이2(StringBuilder 이용 <- 속도 up) [why?](https://hardlearner.tistory.com/288)
```java
import java.util.Arrays;
import java.util.Collections;
class Solution {
    public String solution(String s) {
        String answer = "";
        StringBuilder sb = new StringBuilder();
        String[] arr = new String[s.length()];
        
	arr = s.split("");
        Arrays.sort(arr, Collections.reverseOrder());
        
        for(String word : arr)
        	sb.append(word);
        answer = sb.toString();
        
        return answer;
    }
}
```

3. 다른 사람의 풀이
```java
import java.util.Arrays;

public class ReverseStr {
    public String reverseStr(String str){
    char[] sol = str.toCharArray();
    Arrays.sort(sol);
    return new StringBuilder(new String(sol)).reverse().toString();
    }

    // 아래는 테스트로 출력해 보기 위한 코드입니다.
    public static void main(String[] args) {
        ReverseStr rs = new ReverseStr();
        System.out.println( rs.reverseStr("Zbcdefg") );
    }
}
```
