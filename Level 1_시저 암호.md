1. 풀이 
```java
class Solution {
    public String solution(String s, int n) {
        String answer = "";
        StringBuilder sb = new StringBuilder();
        for(int i=0; i < s.length(); i++){
            char ch = s.charAt(i);
            if(ch >= 'A' && ch <= 'Z')
                sb.append((char)((ch+n)>'Z' ? (ch+n)%'Z'+'A'-1:ch+n));
            else if(ch >= 'a' && ch <= 'z')
            	sb.append((char)((ch+n)>'z' ? (ch+n)%'z'+'a'-1:ch+n));
            else if(ch == ' ')
                sb.append(' ');
        }
        answer = sb.toString();
        return answer;
    }
}
```

2. 풀이2
```java
class Solution {
    public String solution(String s, int n) {
        String answer = "";
        StringBuilder sb = new StringBuilder();
        for(int i=0; i < s.length(); i++){
            char ch = s.charAt(i);
            if(ch >= 'A' && ch <= 'Z')
                sb.append((char)((ch+n-'A')%26 + 'A'));
            else if(ch >= 'a' && ch <= 'z')
            	sb.append((char)((ch+n-'a')%26 + 'a'));
            else if(ch == ' ')
                sb.append(' ');
        }
        answer = sb.toString();
        return answer;
    }
}

3. 다른 사람의 풀이
```java
class Caesar {
    String caesar(String s, int n) {
        String result = "";
    n = n % 26;
    for (int i = 0; i < s.length(); i++) {
      char ch = s.charAt(i);
      if (Character.isLowerCase(ch)) {
        ch = (char) ((ch - 'a' + n) % 26 + 'a');
      } else if (Character.isUpperCase(ch)) {
        ch = (char) ((ch - 'A' + n) % 26 + 'A');
      }
      result += ch;
    }
        return result;
    }

    public static void main(String[] args) {
        Caesar c = new Caesar();
        System.out.println("s는 'a B z', n은 4인 경우: " + c.caesar("a B z", 4));
    }
}
```
```
