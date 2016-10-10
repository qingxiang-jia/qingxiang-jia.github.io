---
layout: post
title: Climbing Stairs
tags:
- Dynamic Programming

---

There are n stairs. You are climbing the stairs, each time, you can either climb it by going up one step or two steps. Compute the number of distinct ways of climbing the n stairs.

Instead of thinking about the entire problem, let's just think about an intermediate scenario of the problem. Say, you are at stair `i`, and you already know how at each previous stair, how many distinct ways there are to get that stair. To compute the distinct ways of getting stair `i`, there are only two cases. Since we can only go up by one step or two, you can get to stair `i` either from stair `i-1` (taking one step) or from stair `i-2` (taking two steps). So, we reach a transition function:

**ways[i] = ways[i-1] + ways[i-2]**

Now, the problem is, how to deal with the initial case. So, if we have only one stair, to reach it, there is only one way. Therefore, the first element of ways should be 1. Now, if we have two stairs, to get to stair #2, we have two ways. Either from stair `1` by going up one step, or from nowhere, going up two steps. So the second element of ways should be two. Now we have solve both the initial case and intermediate case, we can keep computing the results using the transition function, and finally reach the full solution `ways[n-1]`.

The following is my Java solution.

```
public int climbStairs(int n) {
  if (n <= 1) {
    return n;
  }
  int[] ways = new int[n];
  ways[0] = 1;
  ways[1] = 2;
  for (int i = 2; i < n; i++) {
    ways[i] = ways[i-2] + ways[i-1];
  }
  return ways[n-1];
}
```

This is just another case (see previous post) where you only care about the previous results, so to conserve memory, we can use several more variables instead of arrays. The following is my memory-conserving version of the solution.

```
public int climbStairsLowMem(int n) {
  if (n <= 1) {
    return n;
  }
  int prevPrev = 1;
  int prev = 2;
  int curr = 2;
  for (int i = 2; i < n; i++) {
    curr = prevPrev + prev;
    prevPrev = prev;
    prev = curr;
  }
  return curr;
}
```