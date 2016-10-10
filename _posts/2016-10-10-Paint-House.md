---
layout: post
title: Paint House
tags:
- Dynamic Programming

---

This is a LeetCode [question](https://leetcode.com/problems/paint-house/) but since it's paid and you might not have access to it, I will just restate the problem here.

You have an array of n houses, the value of the array represent the house ID. You are given a 2D array whose first entry is the house ID, the second entry is color ID. You want to paint all n houses, but for each house, the cost for different color is different (i.e., the same color for different house may have different cost). Also, two adjacent houses should have different color. Compute the minimum cost.

I literally looked at the question and spent less than one minute to solve it because the question is rather simple. Here is how I thought. First, this is an optimization problem, so naturally, DP may be able to help. Second, since this problem only requires us to look one step backward (adjacent color can't be the same), so, it only involves the relationship between what's already been computed, the previous, and the current. The only tricky thing is, since the color cannot be the same for adjacent houses, we have to find a way to know what's the color of the previous house. Since we don't know in advance what will be the best color for the final solution, for each step, we keep all possible colors. Having thought about the above, we reach the transition function:

**optimal[house][color_x] = costs[house][color_x] + min(optimal[house - 1][color_a], optimal[house - 1][color_b])**

where color\_a and color\_b is the non-conflicting colors for color\_x. Similarly we need to compute the other two possibilities. In the end, we just return whatever the minimal value is among all possible colors.

The following is my Java solution:

```
public int minCost(int[][] costs) {
    if (costs == null || costs.length == 0) {
      return 0;
    }
    int[][] optimal = new int[costs.length][costs[0].length];
    optimal[0][0] = costs[0][0];
    optimal[0][1] = costs[0][1];
    optimal[0][2] = costs[0][2];
    for (int house = 1; house < optimal.length; house++) {
      optimal[house][0] = costs[house][0] + min(optimal[house - 1][1], optimal[house - 1][2]);
      optimal[house][1] = costs[house][1] + min(optimal[house - 1][0], optimal[house - 1][2]);
      optimal[house][2] = costs[house][2] + min(optimal[house - 1][0], optimal[house - 1][1]);
    }
    return min(optimal[optimal.length - 1][0], min(optimal[optimal.length - 1][1], optimal[optimal.length - 1][2]));
}

private int min(int a, int b) {
    if (a > b) {
      return b;
    } else {
      return a;
    }
}
```

A possible optimization is that since we only care about the immediate previous results, we don't really need an array to store all intermediate values (unless you want to reconstruct the solution). So, instead of using an array, we can just use variables to store the previous values.

The following is my less memory intensive version (no use of arrays).

```
public class MyOldSolution {
  public int minCost(int[][] costs) {
    if (costs == null || costs.length == 0) {
      return 0;
    }
    int r = 0, b = 0, g = 0, n = costs.length;
    for (int i = 0; i < n; i++) {
      int _r = r, _b = b, _g = g;
      r = Math.min(_b, _g) + costs[i][0];
      b = Math.min(_r, _g) + costs[i][1];
      g = Math.min(_r, _b) + costs[i][2];
    }
    return Math.min(r, Math.min(b, g));
  }
}
```