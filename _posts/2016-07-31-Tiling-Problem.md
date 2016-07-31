---
layout: post
title: Tiling Problem
tags:
- Algorithm
- Dynamic Programming

---
Given a 2 by n floor, tile it using 2 by 1 tile. Compute the number of ways to tile the floor. What's important and is implicit (I truly hope every problem describes itself as explicitly as possible, even though it may look verbose) is that you have to cover the floor completely and exactly. That means that you cannot leave any part of the floor uncovered, also, you cannot cover any part that is not the floor.

Below is a diagram for the floor.

```
+--+--+--+--+  +--+
|  |  |  |  |..|  |
+--+--+--+--+  +--+
|  |  |  |  |..|  |
+--+--+--+--+  +--+
```

Below is a diagram for the tile.

```
+--+
|  |
+--+
|  |
+--+
```

You can place the tile either vertically, or horizontally. So there's only two ways we can place the tile: if you place it vertically, it takes a 2 by 1 portion of the floor; if you place it horizontally, you have to place another one below or above the original tile horizontally.

The only difficulty in this problem is that you need to think reversely. Let's see if we have the last portion of the tile covered (the nth), how many ways to tile the floor ending at the nth portion really only depends on two things: the n-1 th, and n-2 th. Why? Because when you place the tile, you have two choices, you either do it vertically, or horizontally. If you do it vertically, it's easy as it only takes the current portion. But if you do it horizontally, it covers the current portion and the next portion. So when thinking reversely, the total number of ways for the floor ending the nth portion is the sum of the number of the ways ending at the n-1 th portion (the n-1 th portion was tiled vertically so the n-1 th portion is the neighbor of the nth portion) and the n-2 th portion (the n-2 th portion was tiled horizontally so the n-2 portion is the neighbor of the nth portion).

If we store the number of ways of tiling the floor ending (inclusive) at the ith portion in an array cell T[i], then we have the following transition function:

T[i] = T[i-1] + T[i-2]

Yes, this is the same as the fibonacci sequence formula.

Below is my Java solution. Usually I would do a dry run but as this question is easy, I will skip it.

```
public int tiling(int n) {
    if (n == 0) {
      return 0;
    } else if (n == 1) {
      return 1;
    } else if (n == 2) {
      return 2;
    } else {
      int[] T = new int[n+1];
      T[1] = 1;
      T[2] = 2;
      for (int i = 3; i <= n; i++) {
        T[i] = T[i-1] + T[i-2];
      }
      return T[n];
    }
}
```