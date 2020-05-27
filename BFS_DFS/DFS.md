# DFS

제일 하단 node까지 방문하고 다시 부모 노드로 돌아도는 완전 탐색 방법인 DFS

인접 행렬, 인접 리스트, 스택 등으로 구현할 수 있으나 인접 리스트가 코드가 깔끔해서 인접 리스트로 구현하였다.

현재 노드의 인접리스트를 탐색하고 탐색 결과 노드의 방문 배열값이 false이면 해당 노드로 dfs를 수행한다. 

백준의 2606번 바이러스 문제가 dfs를 간단하게 공부해볼 수 있을것 같다.

```java
import java.io.*;
import java.util.*;

public class Main {
    static StringBuilder sb = new StringBuilder();
    static int computerNumber;
    static int coupled;
    static ArrayList<Integer>[] adjacentList;
    static Boolean[] visited;
    static int answer = 0;

    public static void main(String[] args) throws IOException {
        BufferedReader br = new BufferedReader(new InputStreamReader(System.in));
        BufferedWriter bw = new BufferedWriter(new OutputStreamWriter(System.out));

        computerNumber = Integer.parseInt(br.readLine());
        coupled = Integer.parseInt(br.readLine());
        visited = new Boolean[computerNumber+1];
        adjacentList = new ArrayList[computerNumber+1];

	//인접 리스트와 방문 배열 초기화!! -> 잊지말것
        for(int  i = 0; i < computerNumber+1; i++){
            adjacentList[i] = new ArrayList<>();
            visited[i] = false;
        }

        for(int i = 0; i < coupled; i++){
            StringTokenizer st = new StringTokenizer(br.readLine());
            int first = Integer.parseInt(st.nextToken());
            int second = Integer.parseInt(st.nextToken());
	    //인접리스트는 양방향으로 추가해줬다.
            adjacentList[first].add(second);
            adjacentList[second].add(first);
        }

        dfs(1);
        sb.append(answer-1);

        bw.write(sb.toString());
        bw.flush();
        bw.close();
    }

    static void dfs(int x){
        visited[x] = true;
        answer++;

        for(int i : adjacentList[x]){
            if(!visited[i]){
                dfs(i);
            }
        }
    }
}
```