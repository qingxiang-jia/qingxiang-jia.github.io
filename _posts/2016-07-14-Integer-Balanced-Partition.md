---
layout: post
title: Balanced Partition
tags:
- Algorithm
- Dynamic Programming

---
There is an array of `N` integers. The problem is to classify the integers into two sets such that the difference of the sum of all integers in each set is the minimal.

The solution is kind of surprising. The idea is that I can ask the question differently. If the difference is 0, then the sum of each of the sets are equal. Instead of going about the difference, we focus on whether the integers can be divided into two sets where each of them have the same sum. Say the sum of `N` integers is `K`, we want to know, if it's possible to have two sets each has sum `⌊K/2⌋`. This hint directs us into a table that stores information about whether equal sum partition is possible.

Suppose we have a boolean table `P`, it's dimension is `[⌊K/2⌋][N]`. The following transition function operates on the table. `P[i][j] = true` iff `P[i][j-1]` or `P[i-S[j]][j-1]`, any other case, it should be false. The first part says that if without considering the current candidate `S[j]` (i.e. `P[i][j-1]==true`), then `P[i][j]` must also be true because I can just not to pick the jth candidate. The second part is a bit more involved. It says if I just consider the `1..j-1` candidate, I can sum to `i-S[j]`, then since our current candidate is `S[j]`, I can also reach sum `i` when I consider the jth candidate. Now I want to point out, if you search this algorithm, the pseudo code on the Wikipedia page is incorrect as it uses `S[j-1]`, which doesn't make any sense (verified by coding). I tried to correct it, but I got error when saving the result.

Below is my Java solution. I will briefly go through the code as it's quite self-explanatory.

```
public boolean isBalanced(int[] paraS) {
    int[] S = new int[paraS.length + 1]; // S is 1 based
    make1Based(paraS, S);
    int K = sum(S);
    boolean[][] P = new boolean[K/2+1][S.length];
    // sum to zero can be reached by not taking anything, so P(0, any) should be true
    for (int col = 0; col < P[0].length; col++) {
      P[0][col] = true;
    }
    // no number taken makes any sum impossible, so P(any_except0, 0) should be false
    for (int row = 1; row < P.length; row++) {
      P[row][0] = false;
    }
    for (int i = 1; i < P.length; i++) {
      for (int j = 1; j < P[0].length; j++) {
        if (P[i][j-1]) {
          P[i][j] = true;
        } else if (i-S[j] >= 0 && P[i-S[j]][j-1]) {
          P[i][j] = true;
        } else {
          P[i][j] = false;
        }
      }
    }
    return P[P.length-1][P[0].length-1];
}
```

The `paraS` is the array of `N` integers, but like all arrays, it's 0-based. For convenience, I then convert it into 1-based.

Then I initialize `P` to have dimension `[K/2+1][S.length]`. Notice that I am still taking floor of `K/2` as required by the algorithm. The `+1` is due to the 1-based array.

The first for loop initialize `P[0][any]` to true because if we want to sum to 0, we can always do so by not picking any number. The second for loop I initialize all `P[any_except0][0]` to false because if we don't consider any candidate number, we can't sum to any number except 0.

For the nested loop, it's just the representation of the transition function. Note that when we consider `P[i-S[j]][j-1]`, we need to make sure `i-S[j]` is a valid array index.

Let's run through a sample input. Say we have S={3, 1, 2}, we want to know if the integers can be divided into two sets with equal sum. Here, `K` is 6, and `K/2+1` is 4, so we have 4 rows. We make `S` 1-based so index 1 corresponds to the first element 3. We then initialize the first row to true as 0 can be reached by not picking any candidates. Next, we initialize the first column to false (except col=0) as without picking any candidates, nothing but 0 can be reached.

```
   0  3  1  2
  +--+--+--+--+
0 |T |T |T |T |
  +--+--+--+--+
1 |F |  |  |  |
  +--+--+--+--+
2 |F |  |  |  |
  +--+--+--+--+
3 |F |  |  |  |
  +--+--+--+--+
```

`i=1`, `j=1`, we are trying to reach 1, with candidate `S[1]`. By just `P[1][0]`, we can't do it, and `1-S[1]==-2` so we can't sum to 1 by just 3. Therefore it should be false.

```
   0  3  1  2
  +--+--+--+--+
0 |T |T |T |T |
  +--+--+--+--+
1 |F |F |  |  |
  +--+--+--+--+
2 |F |  |  |  |
  +--+--+--+--+
3 |F |  |  |  |
  +--+--+--+--+
```

`i=2`, `j=1`, similarly, `P[2][0]==false`, and `2-S[1]==-1`, so false.

```
   0  3  1  2
  +--+--+--+--+
0 |T |T |T |T |
  +--+--+--+--+
1 |F |F |  |  |
  +--+--+--+--+
2 |F |F |  |  |
  +--+--+--+--+
3 |F |  |  |  |
  +--+--+--+--+
```

`i=3`, `j=1`, `P[3][0]==true`, so we can sum to 3.

```
   0  3  1  2
  +--+--+--+--+
0 |T |T |T |T |
  +--+--+--+--+
1 |F |F |  |  |
  +--+--+--+--+
2 |F |F |  |  |
  +--+--+--+--+
3 |F |T |  |  |
  +--+--+--+--+
```

`i=1`, `j=2`, `P[1][1]==false`. `1-S[2]==0`, `P[0][1]==true`, so we can sum to 1 when we have candidates 3, 1 (picking 1).

```
   0  3  1  2
  +--+--+--+--+
0 |T |T |T |T |
  +--+--+--+--+
1 |F |F |T |  |
  +--+--+--+--+
2 |F |F |  |  |
  +--+--+--+--+
3 |F |T |  |  |
  +--+--+--+--+
```

`i=2`, `j=2`, `P[2][1]==false`. `2-S[2]==1`, `P[2][1]==false`, so we can't sum to 2 with just 3, 1.

```
   0  3  1  2
  +--+--+--+--+
0 |T |T |T |T |
  +--+--+--+--+
1 |F |F |T |  |
  +--+--+--+--+
2 |F |F |F |  |
  +--+--+--+--+
3 |F |T |  |  |
  +--+--+--+--+
```

`i=3`, `j=2`, `P[3][1]==true`, so we can sum to 3 by just picking 3.

```
   0  3  1  2
  +--+--+--+--+
0 |T |T |T |T |
  +--+--+--+--+
1 |F |F |T |  |
  +--+--+--+--+
2 |F |F |F |  |
  +--+--+--+--+
3 |F |T |T |  |
  +--+--+--+--+
```

`i=1`, `j=3`, `P[1][2]==true`, so we can just pick 1 to reach 1.

```
   0  3  1  2
  +--+--+--+--+
0 |T |T |T |T |
  +--+--+--+--+
1 |F |F |T |T |
  +--+--+--+--+
2 |F |F |F |  |
  +--+--+--+--+
3 |F |T |T |  |
  +--+--+--+--+
```

`i=2`, `j=3`, `P[2][2]==false`, but `2-S[2]==0`, and `P[0][3]==true`, so we can reach 2 using 2.

```
   0  3  1  2
  +--+--+--+--+
0 |T |T |T |T |
  +--+--+--+--+
1 |F |F |T |T |
  +--+--+--+--+
2 |F |F |F |T |
  +--+--+--+--+
3 |F |T |T |  |
  +--+--+--+--+
```

`i=3`, `j=3`, `P[3][2]==true`, so we can reach 3 without even considering candidate 2.

```
   0  3  1  2
  +--+--+--+--+
0 |T |T |T |T |
  +--+--+--+--+
1 |F |F |T |T |
  +--+--+--+--+
2 |F |F |F |T |
  +--+--+--+--+
3 |F |T |T |T |
  +--+--+--+--+
```