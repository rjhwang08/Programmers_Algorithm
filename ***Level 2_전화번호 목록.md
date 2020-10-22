[전화번호 목록](https://programmers.co.kr/learn/courses/30/lessons/42577)

1. Java(해쉬 사용 X 풀이1)
```java
import java.util.*;
class Solution {
    public boolean solution(String[] phone_book) {
        boolean answer = true;
        Arrays.sort(phone_book); // 정렬을 하면 유사한 접두어를 지닌 전화번호를 쉽게 비교 가능
        
        for(int i=1; i < phone_book.length; i++) {
            if(phone_book[i-1].length() > phone_book[i].length()) continue; // 이것을 해주는 이유 : "12111" -> "13", 즉 앞에 번호 길이가 항상 작은 경우만 있는건 아니라는 것!
            String temp = phone_book[i].substring(0, phone_book[i-1].length());
            if(temp.equals(phone_book[i-1])) {
                answer = false;
                break;
            }
        }
        return answer;
    }
}
```

[contains()](https://mine-it-record.tistory.com/137)
[startsWith()와 endWith()](https://jamesdreaming.tistory.com/86)

2. Java(해쉬 사용 X 풀이2)_메소드만 쓰면 위에 과정 전혀 해줄 필요가 없었다...
```java
import java.util.*;
class Solution {
    public boolean solution(String[] phone_book) {
        boolean answer = true;
        Arrays.sort(phone_book);
        
        for(int i=1; i < phone_book.length; i++) {
        //  if(phone_book[i].contains(phone_book[i-1])) { // contains()메소드만 쓰면 그냥 포함되어 있는지 바로 비교 가능! - 틀렸다!!
        //      answer = false;
        //      break;
        //  }
        // 주의!! contains는 앞에만 있는 경우 뿐만 아니라 중간에 포함되어도 true로 반환함. 따라서 접두어 판단을 할 수 없음
            if(phone_book[i].startsWith(phone_book[i-1])) { // startsWith() 메소드를 사용하면 깔끔하게 해결
                answer = false;
                break;
            }
        }
        return answer;
    }
}
```
