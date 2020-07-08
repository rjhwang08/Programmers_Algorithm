- 문제는 쉽지만 다른 풀이에서 배울 개념이 많음!!

1. 풀이(음...)
```java
class Solution {
    public boolean solution(String s) {
        if(s.length() != 4 && s.length() != 6)
            return false;
        for(int i=0; i < s.length(); i++){
            if(s.charAt(i)!='0' && s.charAt(i)!='1' && s.charAt(i)!='2' && s.charAt(i)!='3' && s.charAt(i)!='4' && s.charAt(i)!='5' && s.charAt(i)!='6' && s.charAt(i)!='7' && s.charAt(i)!='8' && s.charAt(i)!='9')
                return false;
        }
        return true;
    }
}
```

2. 다른 사람의 풀이1(**)[예외처리](https://highcode.tistory.com/6)
```java
class Solution {
  public boolean solution(String s) {
      if(s.length() == 4 || s.length() == 6){
          try{
              int x = Integer.parseInt(s);
              return true;
          } catch(NumberFormatException e){
              return false;
          }
      }
      else return false;
  }
}
```

3. 다른 사람의 풀이2(정규식 표현) [정규식 표현](https://nesoy.github.io/articles/2018-06/Java-RegExp) [matches](https://codechacha.com/ko/java-string-matches/)
```java
import java.util.*;

class Solution {
  public boolean solution(String s) {
        if (s.length() == 4 || s.length() == 6) return s.matches("(^[0-9]*$)");
        return false;
  }
}
```
