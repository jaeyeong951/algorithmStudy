# 하노이탑

간단한 재귀 알고리즘을 활용하는 문제입니다.

```java
import java.io.*;

public class Main {
    static StringBuilder sb = new StringBuilder();
    static int input;
    static int count;

    public static void main(String[] args) throws IOException {
        BufferedReader br = new BufferedReader(new InputStreamReader(System.in));
        BufferedWriter bw = new BufferedWriter(new OutputStreamWriter(System.out));

        input = Integer.parseInt(br.readLine());
        count = 0;

        hanoi(input, 1, 3);
        sb.insert(0,"\n");
        sb.insert(0,count);

        bw.write(sb.toString());
        bw.flush();
        bw.close();
    }

    static void hanoi(int num, int from, int to){
        if(num == 1){
            count++;
            sb.append(from);
            sb.append(" ");
            sb.append(to);
            sb.append("\n");
        }
        else{
            if(from+to == 3){
                hanoi(num-1, from, 3);
                hanoi(1, from, to);
                hanoi(num-1, 3, to);
            }
            else if(from+to == 4){
                hanoi(num-1, from, 2);
                hanoi(1, from, to);
                hanoi(num-1, 2, to);
            }
            else if(from+to == 5){
                hanoi(num-1, from, 1);
                hanoi(1, from, to);
                hanoi(num-1, 1, to);
            }
        }
    }
}
```