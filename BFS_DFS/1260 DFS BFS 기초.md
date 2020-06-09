# 1260번 DFS, BFS 기초

```java
import java.util.*;

public class Main {
    static boolean[] visited;
    static int vertex;
    static int edge;
    static boolean[][] arr;
    static Queue<Integer> q = new LinkedList<>();

    public static void main(String[] args) {
        Scanner sc = new Scanner(System.in);
        vertex = sc.nextInt();
        edge = sc.nextInt();
        int startVertex = sc.nextInt();
        q.add(startVertex);
        visited = new boolean[vertex+1];
        arr = new boolean[vertex+1][vertex+1];
        for(int i = 1; i < vertex+1; i++){
            arr[i][i] = true;
        }
        for(int i = 0; i < edge; i++){
            int start = sc.nextInt();
            int end = sc.nextInt();
            arr[start][end] = true;
            arr[end][start] = true;
        }
        dfs(startVertex);
        while(!q.isEmpty()){
            System.out.print(q.poll());
            System.out.print(" ");
        }
        Arrays.fill(visited, false);
        bfs(startVertex);
        sc.close();
    }

    public static void dfs(int i){
        visited[i] = true;
        for(int j = 1; j < vertex+1; j++){
            if(arr[i][j] && !visited[j]){
                q.add(j);
                dfs(j);
            }
        }
    }

    public static void bfs(int i){
        visited[i] = true;
        q.offer(i);
        System.out.println();
        System.out.print(i);
        System.out.print(" ");
        while(!q.isEmpty()){
            int temp = q.poll();
            for(int j = 1; j < vertex + 1; j++){
                if(arr[temp][j] && !visited[j]){
                    System.out.print(j);
                    System.out.print(" ");
                    q.offer(j);
                    visited[j] = true;
                }
            }
        }
    }
}
```