[배열에서 요소 찾는 여러가지 방법](https://riptutorial.com/ko/java/example/7262/%EB%B0%B0%EC%97%B4%EC%97%90%EC%84%9C-%EC%9A%94%EC%86%8C-%EC%B0%BE%EA%B8%B0)

1. 풀이 
```java
class Solution {
    public String solution(String[] seoul) {
        String answer = "";
        for(int i=0; i < seoul.length; i++){
            if(seoul[i].equals("Kim")){
                answer = "김서방은 " + i + "에 있다";
                break;
            }
        }
        return answer;
    }
}
```


2. 다른 사람의 풀이
```java
import java.util.Arrays;

public class FindKim {
    public String findKim(String[] seoul){
        //x에 김서방의 위치를 저장하세요.
        int x = Arrays.asList(seoul).indexOf("Kim");

        return "김서방은 "+ x + "에 있다";
    }

    // 실행을 위한 테스트코드입니다.
    public static void main(String[] args) {
        FindKim kim = new FindKim();
        String[] names = {"Queen", "Tod","Kim"};
        System.out.println(kim.findKim(names));
    }
}
```
