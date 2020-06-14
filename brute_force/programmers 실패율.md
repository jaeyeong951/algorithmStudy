# [programmers]실패율 문제

```java
import java.util.*;
class Solution {
    public int[] solution(int N, int[] stages) {
        //dodal, not dodal모두 0은 신경 안씀
        int[] dodal = new int[N+2];
        int[] dodalbutnotclear = new int[N+2];
        float[] arr = new float[N+2]; //실패율을 담은 배열
        int[] answer = new int[N];

        for(int i = 0; i < stages.length; i++){
            for(int j = 1; j <= stages[i]; j++){
                dodal[j] = dodal[j] + 1;
            }
        }

        for(int i = 0; i < stages.length; i++){
            dodalbutnotclear[stages[i]] = dodalbutnotclear[stages[i]] + 1;
        }

        for(int i = 1; i < arr.length; i++){
            if(dodal[i] == 0){
                arr[i] = 0;
            }
            else{
                arr[i] = (float)dodalbutnotclear[i] / (float)dodal[i];
            }
        }

        Map<Integer,Float> map = new HashMap<>();
        for(int i = 1; i < arr.length; i++){
            map.put(i,arr[i]);
        }

        List<Integer> keySetList = new ArrayList<>(map.keySet());
        keySetList.sort((o1, o2) -> (map.get(o2).compareTo(map.get(o1))));
        int size = 0;
        for(Integer key : keySetList){
            if(key == N+1) {
                //Do Nothing
            }
            else{
                answer[size] = key;
                size++;
            }
        }
        return answer;
    }
}
```

마지막 HashMap 정렬하는 부분 다시 볼 것

`keySetList.sort((o1, o2) -> (map.get(o2).compareTo(map.get(o1))));`

o1과 o2를 비교하는 comparator를 람다 형식으로 쓴 것

compareTo는 클 경우 1 작을 경우 -1 같으면 0을 반환