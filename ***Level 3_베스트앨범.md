[베스트앨범](https://programmers.co.kr/learn/courses/30/lessons/42579#)

[HashMap 정렬](https://ponyozzang.tistory.com/404)

1. Java(해시)
```java
import java.util.*;
import java.util.Map.Entry;

class Pair implements Comparable<Pair> { // <곡의 고유 번호, 재생 횟수>를 담는 클래스
    int num, play;
    Pair(int num, int play) {
        this.num = num;
        this.play = play;
    }
    @Override
    public int compareTo(Pair o) {
        if(this.play == o.play) { // 재생 횟수가 같으면 고유 번호 기준 오름차순 정렬
            return this.num - o.num;
        }
        return o.play - this.play; // 그 외에는 재생 횟수 기준 내림차순 정렬
    }
}

class Solution {
    public int[] solution(String[] genres, int[] plays) {
        ArrayList<Integer> answer = new ArrayList<>();
        HashMap<String, Integer> hashMap = new HashMap<String, Integer>(); // 장르, 총 재생 횟수
        
        for(int i=0; i < genres.length; i++) // 장르별 총 재생 횟수 입력
            hashMap.put(genres[i], hashMap.getOrDefault(genres[i], 0) + plays[i]);
        
        // hashMap을 Value(총 재생 횟수)로 내림차순 정렬
        List<Entry<String, Integer>> list = new ArrayList<>(hashMap.entrySet()); // entrySet()을 리스트에 담아서 리스트를 내림차순 정렬
        Collections.sort(list, new Comparator<Entry<String, Integer>>() {
           @Override
            public int compare(Entry<String, Integer> obj1, Entry<String, Integer> obj2) {
                return obj2.getValue().compareTo(obj1.getValue()); // 오름차순으로 하려면 obj2와 obj1의 위치를 바꾸면 된다.
            }
        });
        
        // 정렬된 장르의 리스트를 탐색하면서 해당 장르에 속하는 곡들을 리스트에 <고유 번호, 재생 횟수> 형태로 담는다.
        for(Entry<String, Integer> entry : list) {
            List<Pair> temp = new ArrayList<>(); // 임의의 리스트
            
            for(int i=0; i < genres.length; i++) {
                if(genres[i].equals(entry.getKey()))
                    temp.add(new Pair(i, plays[i]));
            }
            Collections.sort(temp); // 뽑아낸 곡들을 1) 재생 횟수가 높은 순, 같을 경우 2) 고유 번호가 낮은 순으로 정렬
            answer.add(temp.get(0).num); 앨범에는 장르별 두 곡 씩을어가므로 앞에 2개를 넣어준다.
            if(temp.size() != 1) answer.add(temp.get(1).num); // 주의!! 이때 장르에 곡이 하나만 있는 경우가 있으므로 반드시 예외처리를 해줘야 한다!
        }
        
        int[] ans = new int[answer.size()];
        for(int i=0; i < answer.size(); i++)
            ans[i] = answer.get(i);
        return ans;
    }
}
```
