---
layout: post
title: Longest Increasing Subsequence
tags:
- Algorithm
- Dynamic Programming

---
Given a sequence of n real numbers A(1) ... A(n), determine a subsequence (not necessarily contiguous) of maximum length in which the values in the subsequence form a strictly increasing sequence. The phrasing of this question comes from [bcdean](https://people.cs.clemson.edu/~bcdean/dp_practice/).

When I first see this question, I didn't see the transition function because this question is so easy that you don't even need an explicit one to come up with the solution.

Here is my thought process. We need some kind of stucture to capture what we already know, and then we need some mechanism to "grow" this structure, so that we eventually find the optimal solution. Since we want the maximum length, following the DP thinking fashion, it is natural to use an array to record the maximum length up to the current element. So, the main loop goes from 0 to n (inclusive), computing the maximum length at each cell. The inner loop, can be computed by considering all previous choices. We check two things. First, whether the previous cell's value is less than the current one (since we want strictly increasing sequence); second, we want to check if our current length is larger than the previous length plus one. If so, yes, we update the current length; else, we ignore this one. The following is my Java solution.

```
public int lis(int[] seq) {
    int[] M = new int[seq.length];
    Arrays.fill(M, 1);
    for (int i = 0; i < seq.length; i++) {
      for (int j = 0; j < i; j++) {
        if (seq[j] < seq[i] && M[j] + 1 > M[i]) {
          M[i] = M[j] + 1;
        }
      }
    }
    return M[M.length - 1];
 }
```

Here is two quick tests.

```
public static void main(String...args) {
    Solution s = new Solution();
    System.out.println(s.lis(new int[] {2, 5, 3}));
    System.out.println(s.lis(new int[] {4, 1, 0, 2, 5, 3}));
}
```