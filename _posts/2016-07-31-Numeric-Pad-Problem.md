---
layout: post
title: Numeric Pad Problem
tags:
- Algorithm
- Dynamic Programming

---
You have a phone keypad like the one below, by only clicking the button itself and the neighbor (left, up, right, down), you will be able to produce a set of numbers with certain length (e.g. with length being 2, you can produce numbers like 00, 08...). Compute the amount of numbers with length L produced using this method.

```
+--+--+--+
|1 |2 |3 |
+--+--+--+
|4 |5 |6 |
+--+--+--+
|7 |8 |9 |
+--+--+--+
   |0 |
   +--+
```

If we have L=4, and we are looking at key with 7 on it (abbreviated as key(7)), there are many paths to reach it. For example, we can have 6->9->8->7, 4->5->8->7, 7->7->7->7, and so on. But the paths are built on each other. For example, take 6->9->8->7, if we just consider L=1, 8->7 is a valid path. If we consider L=3, then 9->8->7 is a valid path. So we now know the relationship between each subproblem: the subproblem for L=i is built on the subproblems for L=i-1. Like many other dp problem, we can use a table to store the sub-solutions. 

Define table `count[num][len]` to represent the amount of numbers whose last digit is num (num=0..9, inclusive), with length len (len=0..L).

`count[num][len]` = sum(`count[i][len-1]` for i in neighbor(num)) + `count[num][len-1]`

Interpretation is the following. For each num at len, the solution is the sum of all its neighbor's solution at len-1 (since one more step we are at num, with length being len-1+1 = len) combined with it's solution at len-1 (since we allow clicking the same keypad).

The base case is simple. For `count[i][0]` (i in 0..9), it's just 0 as if we allow zero number of digits, no clicking at all. For `count[i][1]`, it's 1 since we can only click once. The following is my Java solution.

Note that in the code, I made a static 2D array to store an adjacency list so that I can quickly loop through all neighbors of a given key.

```
private static final int[][] NEIGHBOR = new int[][] {
      {8}, // 0's valid neighbor
      {2, 4}, // 1's valid neighbor
      {1, 3, 5}, // 2
      {2, 6}, // 3
      {1, 5, 7}, // 4
      {2, 4, 6, 8}, // 5
      {3, 5, 9}, // 6
      {4, 8}, // 7
      {5, 7, 9, 0}, // 8
      {6, 8} // 9
};

  public int countOfNum(int L) {
    int[][] count = new int[10][L+1];
    for (int num = 0; num < count.length; num++) {
      count[num][1] = 1;
    }
    for (int len = 2; len <= L; len++) {
      for (int num = 0; num < 10; num++) {
        for (int neighborIndex = 0; neighborIndex < NEIGHBOR[num].length; neighborIndex++) {
          count[num][len] += count[NEIGHBOR[num][neighborIndex]][len-1];
        }
        count[num][len] += count[num][len-1];
      }
    }
    int result = 0;
    for (int num = 0; num < 10; num++) {
      result += count[num][L];
    }
    return result;
}
```

As usual, let's have a dry run to get familiar with the algorithm.

As discussed previously, we initialize the first column of count to be 0, the second column to be 1.

```
   0  1  2
  +--+--+--+
0 |0 |1 |  |
  +--+--+--+
1 |0 |1 |  |
  +--+--+--+
2 |0 |1 |  |
  +--+--+--+
3 |0 |1 |  |
  +--+--+--+
4 |0 |1 |  |
  +--+--+--+
5 |0 |1 |  |
  +--+--+--+
6 |0 |1 |  |
  +--+--+--+
7 |0 |1 |  |
  +--+--+--+
8 |0 |1 |  |
  +--+--+--+
9 |0 |1 |  |
  +--+--+--+
```

First, we know the neighbor of key(0), it's just key(8). We sum over all its neighbors' solutions at len=2-1, and combined with it's own solution at len=2-1, we get 2.

```
   0  1  2
  +--+--+--+
0 |0 |1 |2 |
  +--+--+--+
1 |0 |1 |  |
  +--+--+--+
2 |0 |1 |  |
  +--+--+--+
3 |0 |1 |  |
  +--+--+--+
4 |0 |1 |  |
  +--+--+--+
5 |0 |1 |  |
  +--+--+--+
6 |0 |1 |  |
  +--+--+--+
7 |0 |1 |  |
  +--+--+--+
8 |0 |1 |  |
  +--+--+--+
9 |0 |1 |  |
  +--+--+--+
```

Next, for key(1), we have its neighbors being key(2) and key(4). We sum over it's neighbors' solutions at len=1, combined with it's own solution at len=1, we get 3.

```
   0  1  2
  +--+--+--+
0 |0 |1 |2 |
  +--+--+--+
1 |0 |1 |3 |
  +--+--+--+
2 |0 |1 |  |
  +--+--+--+
3 |0 |1 |  |
  +--+--+--+
4 |0 |1 |  |
  +--+--+--+
5 |0 |1 |  |
  +--+--+--+
6 |0 |1 |  |
  +--+--+--+
7 |0 |1 |  |
  +--+--+--+
8 |0 |1 |  |
  +--+--+--+
9 |0 |1 |  |
  +--+--+--+
```

Similarly, we compute the rest of cells, and we get: 

```
   0  1  2
  +--+--+--+
0 |0 |1 |2 |
  +--+--+--+
1 |0 |1 |3 |
  +--+--+--+
2 |0 |1 |4 |
  +--+--+--+
3 |0 |1 |3 |
  +--+--+--+
4 |0 |1 |4 |
  +--+--+--+
5 |0 |1 |5 |
  +--+--+--+
6 |0 |1 |4 |
  +--+--+--+
7 |0 |1 |3 |
  +--+--+--+
8 |0 |1 |5 |
  +--+--+--+
9 |0 |1 |3 |
  +--+--+--+
```

Finally, we sum all `count[2][i]` (i=0..9) and we get 36.