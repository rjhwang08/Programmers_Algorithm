[멀쩡한 사각형](https://programmers.co.kr/learn/courses/30/lessons/62048)

- 문제 조건에서 W, H가 최대 1억까지 가능한 것을 인지하고, 연산 시 반드시 long형으로 형변환 해줘야 한다.

1. Java(내 풀이)_ 테스트 11 (3392.80ms, 52.2MB)
```java
class Solution {
    public long solution(int w, int h) {
        long answer = 1;
        long wl = Long.valueOf(w);
        long hl = Long.valueOf(h);
        
        long minus = 0;
        long div = 0;
        for(long i=1; i <= wl; i++){
            if((hl*i%wl) == 0){
                div = i;
                break;
            }
        }
        for(long i=1; i <= div; i++){
            minus = minus + (hl*i/wl - hl*(i-1)/wl);
            if(hl*i%wl != 0) minus++;
        }
        answer = wl*hl - minus*(wl/div);
        return answer;
    }
}
```

[풀이 참고](https://taesan94.tistory.com/55#recentEntries)
2. Java(다른 사람 풀이 참고-규칙을 이용한 연산)_테스트 11 통과 (0.04ms, 52.6MB)
```java
class Solution {
    public long gcd(long a, long b) {
        if(b == 0) return a;
        else return gcd(b, a % b);
    }    
    public long solution(int w, int h) {
        long answer = 1;
        long wl = Long.valueOf(w);
        long hl = Long.valueOf(h);
        answer = wl * hl - (wl + hl - gcd(wl, hl));
        return answer;
    }
}
```
