# [programmers] 비밀지도

```java
import java.util.*;
class Solution {
    public String[] solution(int n, int[] arr1, int[] arr2) {
        int[][] map1 = new int[n][n];
        int[][] map2 = new int[n][n];
        String[][] post_answer = new String[n][n];
        String[] answer = new String[n];
        for(int i = 0; i < n; i++){
            answer[i] = "";
        }

        for(int i = 0; i < n; i++){
            String binary1 = Integer.toBinaryString(arr1[i]);
            String binary2 = Integer.toBinaryString(arr2[i]);
            int l1 = binary1.length();
            int l2 = binary2.length();
            ArrayList<String> temp1 = new ArrayList<>();
            ArrayList<String> temp2 = new ArrayList<>();
            for(int k = 0; k < n - l1; k++){
                temp1.add("0");
            }
            for(int k = 0; k < l1; k++){
                temp1.add(Character.toString(binary1.charAt(k)));
            }
            for(int k = 0; k < n - l2; k++){
                temp2.add("0");
            }
            for(int k = 0; k < l2; k++){
                temp2.add(Character.toString(binary2.charAt(k)));
            }
            String[] a = temp1.toArray(new String[0]);
            String[] b = temp2.toArray(new String[0]);
            for(int j = 0; j < n; j++){
                map1[i][j] = Integer.parseInt(a[j]);
                map2[i][j] = Integer.parseInt(b[j]);
            }
        }

        for(int i = 0; i < n; i++){
            for(int j = 0; j < n; j++){
                if(map1[i][j] == 1 || map2[i][j] == 1){
                    answer[i] += "#";
                }
                else{
                    answer[i] += " ";
                }
            }
        }
        return answer;
    }
}
```

String은 +로 덧붙일 수 있다!

풀 때 막히더라도 조금만 침착하자.