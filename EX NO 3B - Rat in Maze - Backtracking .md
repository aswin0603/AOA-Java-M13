
# EX 3B Rat in Maze- Backtracking 
## DATE: 27-09-2025
## AIM:
To write a Java program to for given constraints.
here is a ball in a maze with empty spaces (represented as 0) and walls (represented as 1). The ball can go through the empty spaces by rolling up, down, left or right, but it won't stop rolling until hitting a wall. When the ball stops, it could choose the next direction.

Given the m x n maze, the ball's start position and the destination, where start = [startrow, startcol] and destination = [destinationrow, destinationcol], return true if the ball can stop at the destination, otherwise return false.

You may assume that the borders of the maze are all walls (see examples).
<img width="573" height="573" alt="image" src="https://github.com/user-attachments/assets/d6f1c054-cdc2-4bb3-9c55-512fb2cf0fb7" />
Input: maze = [[0,0,1,0,0],[0,0,0,0,0],[0,0,0,1,0],[1,1,0,1,1],[0,0,0,0,0]], start = [0,4], destination = [4,4]
Output: true
Explanation: One possible way is : left -> down -> left -> down -> right -> down -> right.


## Algorithm
1. The current position is marked as visited to prevent cycles; if it was already visited, return false. If the current position is the destination, return true.
2. Iterate through all four cardinal directions (up, down, left, right) from the current position.
3. In each direction, roll the ball (update the coordinates r and c) until it hits a wall (maze[r][c] == 1) or goes out of bounds.
4. Backtrack one step to find the ball's final resting position before the wall/boundary, as this is the next valid spot.
5. Recursively call dfs from this new stop position; if the recursive call finds the path, return true; otherwise, continue the loop or return false after all directions are checked.

## Program:
```java
import java.util.*;

public class Main {

    public static void main(String[] args) {
        Scanner sc = new Scanner(System.in);

        int m = sc.nextInt();
        int n = sc.nextInt();

        int[][] maze = new int[m][n];
        for (int i = 0; i < m; i++) {
            for (int j = 0; j < n; j++) {
                maze[i][j] = sc.nextInt();
            }
        }

        int[] start = new int[]{sc.nextInt(), sc.nextInt()};

        int[] destination = new int[]{sc.nextInt(), sc.nextInt()};

        Solution sol = new Solution();
        boolean result = sol.hasPath(maze, start, destination);

        System.out.println(result);
    }
}

class Solution {
    public boolean hasPath(int[][] maze, int[] start, int[] destination) {
        int m = maze.length;
        int n = maze[0].length;
        boolean[][] visit = new boolean[m][n];
        return dfs(m, n, maze, start, destination, visit);
    }

    public boolean dfs(int m, int n, int[][] maze, int[] curr, int[] destination, boolean[][] visit) {
        if (visit[curr[0]][curr[1]]) return false;
        if (curr[0] == destination[0] && curr[1] == destination[1]) return true;
        visit[curr[0]][curr[1]] = true;

        int []dirX = {0, 1, 0, -1};
        int []dirY = {-1,0,1,0};
        for(int i=0; i<4; i++){
            int r = curr[0], c=curr[1];
            while(r>=0&&r<n&&c>=0&&c<n&&maze[r][c]==0){
                r+=dirX[i];
                c+=dirY[i];
            }
            r-=dirX[i];
            c-=dirY[i];
        if(dfs(m,n,maze, new int[] {r,c}, destination,visit)){
            return true;
        }
        }
        return false;
    }
}
```

## Output:
<img width="344" height="464" alt="image" src="https://github.com/user-attachments/assets/d3fc7dbb-df57-4cd8-8e0e-5763837d3e18" />



## Result:
The program successfully implemented and the expected output is verified.

```
Developed by: ASWIN B
Register Number:  212224110007
```
