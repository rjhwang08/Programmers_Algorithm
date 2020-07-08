1. 풀이
```java
class Solution {
    boolean solution(String s) {
        boolean answer = true;
        int pcnt = 0;
        int ycnt = 0;

        for(int i=0; i < s.length(); i++){
            if(s.charAt(i) == 'p' || s.charAt(i) == 'P')
                pcnt++;
            else if(s.charAt(i) == 'y' || s.charAt(i) == 'Y')
                ycnt++;
        }
        answer = (pcnt == ycnt) ? true : false;
        return answer;
    }
}
```

2. 다른 사람의 풀이1(모두 소문자로 바꾸로 p,y 합쳐서 카운트)
```java
class Solution {
    boolean solution(String s) {
        s = s.toLowerCase();
        int count = 0;

        for (int i = 0; i < s.length(); i++) {

            if (s.charAt(i) == 'p')
                count++;
            else if (s.charAt(i) == 'y')
                count--;
        }

        if (count == 0)
            return true;
        else
            return false;
    }
}
```

3. 다른 사람의 풀이2(ㄷㄷ)
```java
class Solution {
    boolean solution(String s) {
        s = s.toUpperCase();

        return s.chars().filter( e -> 'P'== e).count() == s.chars().filter( e -> 'Y'== e).count();
    }
}
```
