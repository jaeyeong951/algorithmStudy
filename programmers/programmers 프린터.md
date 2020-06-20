# [programmers] 프린터

```java
import java.util.*;
class Solution {
    public int solution(int[] priorities, int location) {
        int answer = 0;
        int tl = location;
        LinkedList<Integer> l = new LinkedList<>();
        for(int i = 0; i < priorities.length; i++){
            l.add(priorities[i]);
        }
        while(true){
            int isBiggerExist = 0;
            int temp = l.peekFirst();
            for(int i = 1; i < l.size(); i++){
                if(l.get(i) > temp){
                    if(tl == 0) tl = l.size()-1;
                    else tl--;
                    int pf = l.pollFirst();
                    l.add(pf);
                    isBiggerExist = 1;
                    break;
                }
            }
            if(isBiggerExist == 0){
                if(tl == 0){
                    break;
                }
                tl--;
                answer++;
                l.pollFirst();
            }
        }
        answer++;

        return answer;
    }
}
```

원래 큐로 푸는 문제이다.

알고리즘 자체는 큐와 동일하나 처음에 큐로는 접근할 방법이 생각이 안나서 링크드 리스트로 풀었다.

큐로 풀면

```java
import java.util.*;

class Solution {
    public int solution(int[] priorities, int location) {
        int answer = 0;
        int l = location;

        Queue<Integer> que = new LinkedList<Integer>();
        for(int i : priorities){
            que.add(i);
        }

        Arrays.sort(priorities);
        int size = priorities.length-1;

        while(!que.isEmpty()){
            Integer i = que.poll();
            if(i == priorities[size - answer]){
                answer++;
                l--;
                if(l <0)
                    break;
            }else{
                que.add(i);
                l--;
                if(l<0)
                    l=que.size()-1;
            }
        }

        return answer;
    }
}
```