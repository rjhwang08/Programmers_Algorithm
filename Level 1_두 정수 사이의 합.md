1. 풀이
```java
class Solution {
    public long solution(int a, int b) {
        long answer = 0;
        if(a <= b) {
            for(int i=a; i <= b; i++)
            answer += i;
        }else{
            for(int i=b; i <= a; i++)
            answer += i;
        }
        
        //for(int i=Math.min(a,b); i <= Math.max(a,b); i++)  //조건문 쓰지 않고 Math 함수를 이용하는 방법
        //    answer += i;
        return answer;
    }
}
```

2. 다른 사람의 풀이1(공식 이용)
```java
class Solution {

    public long solution(int a, int b) {
        return sumAtoB(Math.min(a, b), Math.max(b, a));
    }

    private long sumAtoB(long a, long b) {
        return (b - a + 1) * (a + b) / 2;
    }
}
```
