---
layout: post
title: Pacific Atlantic Water Flow
tags:
- Algorithm
- DFS
- BFS
- Graph

---

Here is a sample input (taken from LeetCode):
 
```
  where ~   -> Pacific ocean
        *   -> Atlantic ocean
        (a) -> coordinate satisfying in solution set
        -- yes, the notation is a bit haskelly 

  Pacific ~   ~   ~   ~   ~ 
       ~  1   2   2   3  (5) *
       ~  3   2   3  (4) (4) *
       ~  2   4  (5)  3   1  *
       ~ (6) (7)  1   4   5  *
       ~ (5)  1   1   2   4  *
          *   *   *   *   * Atlantic
```

Immediately I thought we could do either DFS or BFS from each sides (Pacific sides and Atlantic sides), and compute the intersection. But then I thought we might be able to something a bit faster. What I thought was connected component. We can start from nodes that are both connected to Pacific and Atlantic, namely, the lower left and the upper right. However, I saw "(5)" in the middle of the matrix, and I knew the connected component strategy didn't work. "(5)" is not connected to neither of them, but itself is "flowable" to both oceans.

So, back to the previous solution, which is traversing the graph (matrix (2D array)) from Pacific sides and Atlantic sides via either BFS or DFS and take the intersection. I ended up using BFS, but DFS works equally.

The following is my Java solution.

```
public List<int[]> pacificAtlantic(int[][] mat) {
    if (mat == null || mat.length == 0 || mat[0].length == 0) {
      return new LinkedList<>();
    }
    int maxRow = mat.length, maxCol = mat[0].length;
    LinkedList<int[]> results = new LinkedList<>();
    boolean[][] vP = new boolean[maxRow][maxCol];
    boolean[][] vA = new boolean[maxRow][maxCol];
    Queue<int[]> qP = new LinkedList<>();
    Queue<int[]> qA = new LinkedList<>();
    // add columns
    for (int row = 0; row < maxRow; row++) {
      qP.offer(new int[]{row, 0});
      vP[row][0] = true;
      qA.offer(new int[]{row, maxCol - 1});
      vA[row][maxCol - 1] = true;
    }
    // add rows
    for (int col = 0; col < maxCol; col++) {
      qP.offer(new int[]{0, col});
      vP[0][col] = true;
      qA.offer(new int[]{maxRow - 1, col});
      vA[maxRow - 1][col] = true;
    }
    BFS(mat, qP, vP);
    BFS(mat, qA, vA);
    for (int row = 0; row < maxRow; row++) {
      for (int col = 0; col < maxCol; col++) {
        if (vP[row][col] && vA[row][col]) {
          results.add(new int[]{row, col});
        }
      }
    }
    return results;
}

private void BFS(int[][] mat, Queue<int[]> q, boolean[][] visited) {
    int maxRow = mat.length, maxCol = mat[0].length;
    while (!q.isEmpty()) {
      int[] curr = q.poll();
      int r = curr[0], c = curr[1];
      // for all its neighbors
      if (r - 1 >= 0 && mat[r - 1][c] >= mat[r][c] && !visited[r - 1][c]) { // up
        visited[r - 1][c] = true;
        q.offer(new int[]{r - 1, c});
      }
      if (r + 1 < maxRow && mat[r + 1][c] >= mat[r][c] && !visited[r + 1][c]) { // down
        visited[r + 1][c] = true;
        q.offer(new int[]{r + 1, c});
      }
      if (c - 1 >= 0 && mat[r][c - 1] >= mat[r][c] && !visited[r][c - 1]) { // left
        visited[r][c - 1] = true;
        q.offer(new int[]{r, c - 1});
      }
      if (c + 1 < maxCol && mat[r][c + 1] >= mat[r][c] && !visited[r][c + 1]) { // right
        visited[r][c + 1] = true;
        q.offer(new int[]{r, c + 1});
      }
    }
}
```