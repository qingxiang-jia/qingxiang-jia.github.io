---
layout: post
title: Minimum Cost to Destination
tags:
- Algorithm
- Dynamic Programming

---
There is a railway starting from station #0 to station #n-1 (for convenience, call it station(n-1)). Given the cost between station i to j where j > i (i.e., going from j to i is impossible), compute the minimum cost traveling from station(0) to station(n-1).

Here is my thought process. Initially, I didn't have a clue, so I decided to write down what I need to compute for each subproblem. To make it short, I used 4 stations. How would you compute the minimum cost from station(0) to station(3)? (minCost(i): minimum cost from station(0) to station(i))

```
minCost(0): 0.
minCost(1): cost(0, 1)
minCost(2): cost(0, 1) + cost(1, 2) <=> minCost(1) + cost(1, 2)
            cost(0, 2)
            then take the minimum
minCost(3): cost(0, 1) + cost(1, 2) + cost(2, 3)
            cost(0, 2) + cost(2, 3)
            cost(0, 1) + cost(1, 3)
            cost(0, 3)
            then take the minimum
```

Now, observe what I have computed so many times. For minCost(2), as I pointed out, we are comparing minCost(1) + cost(1, 2) and cost(0, 2). This may lead you to write down the following transition function: minCost(i) = minCost(i-1) + cost(i-1, i). However, it's **not** correct. You can verify this using the following example (taken from Geeks for Geeks) (i->j <=> row->col):

```
+---+---+---+---+
|0  |15 |80 |90 |
+---+---+---+---+
|INF|0  |40 |50 |
+---+---+---+---+
|INF|INF|0  |70 |
+---+---+---+---+
|INF|INF|INF|0  |
+---+---+---+---+
```

To get the correct transition function, let's observe minCost(3). The first two lines, if we ignore cost(2,3), they are just the problems we computed in minCost(2). Since we will eventually pick the minimum from them, why don't we just use the minimum picked in minCost(2) already? Because for the first two lines, they both have cost(2, 3), so what determines whichever is smaller is the rest of elements -- and that has been determined in minCost(2). I don't know which one, but minCost(2) has picked the one. So we can use one single line to replace the two: minCost(2) + cost(2, 3). Now, how about the third line? Well, that we haven't computed it, but we can convert it to minCost(1) + cost(2, 3) like we did to the first line of minCost(2). Now, how about cost(0, 3)? Hmm, we haven't computed it, we need it. So, at this point, minCost(3) can be rewritten as the following:

```
minCost(3): minCost(2) + cost(2, 3)
            minCost(1) + cost(1, 3)
            cost(0, 3)
            then take the minimum
```

From that, we can derive our transition function: **minCost(i) = min(minCost(j) + cost(j, i) for j=0..i-1, cost(0, i))**. Let's try to understand it from a different perspective. We want minCost(i), our candidates are: the one ticket solution: cost(0, i), and the multi-ticket solution minCost(some_stop) + cost(some_stop, i). Since we don't know which stop will give the best multi-ticket solution, we try all available. Since we don't know if the one-ticket solution is better, or the multi-ticket solution is better, we take the min between them.

As usual, below is my Java solution and I will perform a dry run on the sample data. BTW, I encountered the sample and question from Geeks for Geeks, but my solution is done by myself and is different (I think it's better :) than the Geeks for Geeks solution.

```
public int minCostToDest(int[][] cost) {
    int[] minCost = new int[cost.length];
    minCost[0] = 0; // you can skip it since Java does it automatically
    for (int i = 1; i < cost.length; i++) {
      int candidate = Integer.MAX_VALUE;
      for (int j = 0; j <= i-1; j++) {
        if (candidate > minCost[j] + cost[j][i]) {
          candidate = minCost[j] + cost[j][i];
        }
      }
      minCost[i] = candidate;
    }
    return minCost[cost.length - 1];
}
```

```
         +--+--+--+--+
minCost  |0 |  |  |  |
         +--+--+--+--+
```

First, minCost(0) is initialized to 0 because from station(0) to station(0), the optimal solution doesn't a ticket. Then, we try to compute minCost(1). The only option we have is: `minCost[0]` + `cost[0][1]` and it's evaluated to 15.

```
+--+--+--+--+
|0 |15|  |  |
+--+--+--+--+
```

Next, we try to compute minCost(2). We compute min(`minCost[0]` + `cost[0][2]`, `minCost[1]` + `cost[1][2]`), and we get 55.

```
+--+--+--+--+
|0 |15|55|  |
+--+--+--+--+
```

Finally, we compute minCost(3). We compute min(`minCost[0]` + `cost[0][3]`, `minCost[1]` + `cost[1][3]`, `minCost[2]` + `cost[2][3]`), and we get 65.