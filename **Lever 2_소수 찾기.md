[소수 찾기](https://programmers.co.kr/learn/courses/30/lessons/42839)

1. Java
```java
class Solution {
    public int answer = 0;    
    public boolean prime(int num) {
        if(num < 2) return false;
        for(int i=2; i*i <= num; i++) {
            if(num % i == 0) return false;
        }
        return true;
    }
    public void permutation(int[] arr, int step, int len, String s) {
        if(step >= len) {
            int num = Integer.parseInt(s);
            if(prime(num)) answer++;
            return;
        }
        for(int i=0; i < 10; i++) {
            if(arr[i] == 0) continue; // 개수가 0이면 skip
            // 가장 앞에 0이 오는 경우를 빼야 중복이 안생긴다.
            if(step == 0 && i == 0) continue; //예)2자리 11은 3자리 011과 같아서 중복이 된다.
            arr[i]--;
            permutation(arr, step+1, len, s + i);
            arr[i]++;
        }
    }
    public int solution(String numbers) {
        int len = numbers.length(); // 입력받은 숫자 길이
        int[] arr = new int[10]; // 0 ~ 9까지의 숫자 개수를 담는 배열
        for(int i=0; i < len; i++)
            arr[numbers.charAt(i) - '0']++;
        
        for(int i=1; i <= len; i++)
            permutation(arr, 0, i, "");
        
        return answer;
    }
}
```
