---
layout: post
title: Making Change
tags:
- Algorithm
- Dynamic Programming

---
A country has denominations: `d1, d2, d3, ..., dk` (in unit, say, dollar). You are asked to make change for n dollars. You want to make as few banknotes as possible. Design an algorithm to do it.

`C[p] = 1 + C[p-x]`

Initially I thought we can use greedy algorithm to do it. We try the largest denomination that is less than or equal to `n` repeatedly, and subtract that amount from `n`; eventually `n` will be 0 and we are done. This is simple and intuitive. However, this does not work every time. For example, say, I have the following denominations: `[1, 5, 10, 20, 25]`. Given 40, the greedy algorithm will return `[25, 10, 5]`. This is not optimal since we can just do `[20, 20]`. Then I found Dr. Cliff Stein's [slides](www.columbia.edu/~cs2035/courses/csor4231.F07/dynamic.pdf) which gave the above transition function.

Instead of considering what are the banknotes that will be returned, we take one step back, thinking what's the minimum number of banknotes needed. In the above equation, `C[p]` represents the minimum banknotes needed for `p` dollars. So, `C[0]` is 0 as if there is no money, there is no change needed. `C[p]` is just `C[p-x]` plus `1`. The equation says: the minimum number of banknotes needed for `p` dollars, can be constructed from `C[p-x]` if we know what `x` is. `x` is one of the denominations. Since we don't know which one is appropriate here, we try all of them. This is the inner loop. For `n` from `1` to `n`, we run the inner loop, and when it goes to `n`, we have our solution.

```
public void change(int n, int[] d) {
    int[] C = new int[n + 1];
    int[] S = new int[n + 1];
    for (int p = 1; p <= n; p++) {
      int min = Integer.MAX_VALUE;
      int coin = 0;
      for (int i = 0; i < d.length; i++) {
        if (p >= d[i] && C[p - d[i]] + 1 < min) {
          min = C[p - d[i]] + 1;
          coin = i;
        }
      }
      C[p] = min;
      S[p] = coin;
    }
    // reconstruct solution
    int remain = n;
    List<Integer> soln = new ArrayList<Integer>();
    while (remain > 0) {
      soln.add(d[S[remain]]);
      remain -= d[S[remain]];
    }
    System.out.println(soln.toString());
  }
```

Above is my Java solution to this question. `C`, short for Change, stores the minimum number of banknotes needed for the cell number of dollars. `S`, short for Solution, it records which denomination we should use for the cell number of dollars. To make sense of the above code, let's go through an example.

Say I have the following denomination (denoted by variable `d`): `[1, 5, 10, 20, 25]`, and I am given 6 dollars. First, for `p=1`, in the inner loop, the only choice is to take $1, so we have `C[1]=1`, `S[1]=0` ($1 corresponds to cell number 0). This means, if we were to make change for 1 dollar, we only need one banknote whose value is one dollar. Next, for `p=2`, again, we don't have many choices as all denominations except $1 is larger than 2. In this case, `min = C[2 - d[0]] + 1` which is 2. `S[2] = 2`. Next, for `p=3`, similarly, we don't have many choice, but to choose denomination $1 and build on the previous solution `C[2]`. Consequently we get `C[3]=3` and `S[3]=0`. For `p=4`, again, we have only one denomination possible: $1, and we end up getting `C[4]=4`, `S[4]=0`. For `p=5`, this time, in the inner loop, we have two choices. We first encounter our old choice $1, and we take it, we have `min = C[5 - d[0]] + 1`, which is 5. But in the next iteration, we encounter the new choice, $5, and we have `min = C[5 - d[1]] + 1`, which is 1, and is better than our current `min`, so we record this new min and its corresponding banknote. So, in the end, we have `C[5]=1` and `S[5]=1`. Next, for `p=6`, again, in the inner loop, we have two choices: $1 and $5. We first encounter $1, and we have `min = C[6 - d[0]] + 1`. Since `d[0]` is 1, `min = C[5] + 1`. This gives `min=2`. In the next iteration, we encounter `d[1]` which is $5. `min = C[6 - 5] + 1`, resulting in 2, this is equally good as what we got from the previous iteration. They are actually identical. What we get from the first iteration says `[5, 1]` and this one says `[1, 5]`.We are not done yet. We now have the minimum number of banknotes needed for 6 dollars. But we don't have [1, 5] yet. To construct the solution, we use variable C, S, and d. Recall that C records the minimum number of banknotes needed for cell number of dollars; S records what banknote will be used for cell number of dollars; d is the denomination. So, to reconstruct the solution, we use S to locate the cell number of the banknote will be used (given the money remained); then use d to get the actually banknote value. Subtract that amount from the remaining money and repeat until we exhaust the money.