# [programmers]종이접기

```java
import java.util.*;
class Solution {
    public int[] solution(int n) {
       int[] answer;
        ArrayList<Integer> arr = new ArrayList<>();
        arr.add(0);
        if(n == 1){

        }
        else{
            for(int i = 1; i < n; i++){
                int zem = 0;
                for(int j = 0; j <= arr.size(); j=j+2){
                    if(zem == 0 ){
                        arr.add(j,0);
                        zem = 1;
                    }
                    else{
                        arr.add(j,1);
                        zem = 0;
                    }
                }
            }
        }
        answer = new int[arr.size()];
        for(int i = 0; i < arr.size(); i++){
            answer[i] = arr.get(i);
        }
        return answer;
    }
}
```