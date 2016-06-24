---
layout: post
title: Maximum Value Contiguous Subsequence
tags:
- Algorithm
- Dynamic Programming

---
Given a sequence of n real numbers A(1) ... A(n), determine a contiguous subsequence A(i) ... A(j) for which the sum of elements in the subsequence is maximized.

```
         +           +
+--+--+--+--+--+--+--+--+
|  |  |  |  |  |  |  |  |
+--+--+--+--+--+--+--+--+
         +           +
           i        j
```

`M[j] = max sum over all window ending at j`

`M[j] = max { M[j-1] + A[j], A[j] }`

Thought process:
The naive solution runs in O(n^2) because we need to try all possible combinations of i and j. The dp version runs in O(n). i and j cannot be changing in the same time as in that case the subproblem is hard to define. So, what's the subproblem? The subproblem can be defined as the optimal solution at j. When j is 0, there is no choice but to pick whatever the first element is in A. Here is an example:

```
+--+--+--+--+
|-1| 3|-2| 5|
+--+--+--+--+
```

When `j=0`, meaning the optimal solution ending at j (max sum over all windows ending at j), there is no choice but to take -1. (OK, here is an issue with definition. By the question, it implies that we must have at least a sequence, that is, we cannot make no choice. So, in case of `[-1, -1, -1]`, the solution should be -1, instead of 0 (making to choice at all).) When `j=1`, we have two choices, take only `A[1]`, or, take the previous optimal and `A[1]`. Clearly, in this case, it is better to take just `A[1]`, so here, we have `M[1]=3`. When `j=2`, we have two choices again: taking the sum of the previous optimal or just taking the current one. So `M[2]=1` here. If you ever have a thought of keep 3 in `M[2]`, you should notice that we actually don't have this option. Either we do `M[i-1] + A[i]`, or `A[i]`. In fact, we can't make no choice as that will form uncontigous sequence. When `j=3`, we have two options again, and clearly, the better one is to sum up the previous optimal solution with the current value, that is `1+5=6`.

I saw the problem from [Brian Dean](https://people.cs.clemson.edu/~bcdean/dp_practice/), he has all credits for this solution, I just added my interpretations.