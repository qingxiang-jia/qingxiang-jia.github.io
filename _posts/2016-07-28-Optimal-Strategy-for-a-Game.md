---
layout: post
title: Optimal Strategy for a Game
tags:
- Algorithm
- Dynamic Programming

---
There is a row of numbers, and two players A and B. When it's player A's turn, he picks either the left or right end of the row, and the value is then added to his score. The next time will be player B's turn, and she can do the same. Two players keep playing this until there is nothing left (to be fair, the row has even number of elements). If we move first (we are A), compute the maximum score we can definitely get regardless the other player's move.

Well, the first time I saw this question I thought this is so easy, we can just simulate the process of two players playing this game, and each time, they choose whatever is best for them, and it will be an O(n) process. However, I realized this was wrong because of a counter example: [3, 17, 2, 1].

```
A: 3
B: 17
A: 2
B: 1
```

But A can be smarter, and he will get 17 regardless B's move.

```
A: 1
B: 3
A: 17
B: 2
```

Even though B takes 2 in her second move, A gets to take 17 in the next move. So, the greedy approach doesn't work here.

We want to get the best result regardless B's move, that is the same to say we want to get the best result for A even if at each move, B chooses the move such that A's gain is minimized. So, we want to build some formula where we maximize whatever that will be minimized by B in the next turn. Notice here, the difference between greedy and dp is that for greedy, B should minimize whatever A's gain is at this step; but for dp, B considers the whole picture. This will be obvious when we discuss the transition function.

The entire problem is the maximum value A definitely gains regardless B's move for the entire row. So the subproblem is naturally the maximum value A definitely gains regardless B's move for the subrow. To represent the subrow, we use two indices, signaling the beginning and ending of the subrow (inclusive). So, `v[i][j]` will be the maximum value A can definitely get regardless B's move. By the way, why we need two indices? Remember for some question, like the edit distance, we only use the ending index to represent the substring. Here, we need two indices because the players picks the value from either ends. Both situation is possible, so to accommodate that, two indices are necessary.

As we discussed previously, we want to maximize whatever the value that will later be minimized by B. In a word, B chooses whatever is bad for us OVERALL, we accept it and try to find the best solution then.

Imagine that we are at a subrow row[i..j] and it's our turn. We have two choices, either to pick the ith value, or the jth. If we take `row[i]`, B can then take either `row[i+1]` or `row[j]`; if we take `row[j]`, B can then take `row[i]` or `row[j-1]`. That's all possible situation for a turn. So we have:

`v[i][j]` = max(min(`v[i+1][j-1]`, `v[i+2][j]`) + `row[i]`, min(`v[i][j-2]`, `v[i+1][j-1]`) + `row[j]`)

What does this mean? First, let's focus on the case where we pick the ith. As discussed, B can either take `row[i+1]` or `row[j]`. If B takes `row[i+1]`, this leaves us with row[i+2..j]. If B takes `row[j]`, this leaves us row[i+1..j-1]. Similarly, if we take the jth, B can either take `row[i]`, which leaves us row[i+1..j-1]; or if B takes `row[j-1]`, which then leaves us row[i..j-2]. For either case, we add the value of that element we just took. The inner `min()` represent B's decision. B takes whatever is bad for us overall. The outer `max()` represent our decision: we pick whatever is good for us based on what B will take that is bad for us.

Now, we have the transition function, but in what order should we evaluate the subproblems?

We can figure it out by a simple example. Say we are at a subrow (row[2..5]), the number is the index of each element.

```
+--+--+--+--+
|2 |3 |4 |5 |
+--+--+--+--+
```

According to the transition function, we need to calculate the following:

```
+--+--+
|2 |3 |
+--+--+

      +--+--+
      |4 |5 |
      +--+--+

  +--+--+
  |3 |4 |
  +--+--+
```

What does this diagram tell us? It shows that we need to compute the subproblems between i..j if we want the solution `v[i][j]`, and of course the subproblems between i..j will need more smaller subproblems. So we should compute the subproblem starting from the smallest range, and gradually increase it as a large range subproblem requires solutions to all smaller range subproblem. More specifically, we can compute the subproblem `v[i][i]` first for all valid i; and then `v[i][i+1]` for all valid i and so on. 

However, there are some corner cases. When the range only includes 1 element (the `v[i][i]` case), it represents the last pick, and it's our turn, so we just pick `row[i]`. The other corner case is when the range only includes two elements, i.e., the `v[i][j]` case where j-i==1. It means there are only two elements left, and we get to pick either (and of course B can only take what's left by us). In this case, the inner min is gone as B has no choice, we can just pick whichever is larger.

The following is my Java solution. It should be straightforward after you see the transition function and evaluating order.

```
public int maxGuaranteed(int[] row) {
    int[][] v = new int[row.length][row.length];
    for (int initJ = 0; initJ < v.length; initJ++) {
      for (int i = 0, j = initJ; j < v[0].length; i++, j++) {
        if (i == j) {
          v[i][j] = row[i];
        } else if (j - i == 1) {
          v[i][j] = max(row[i], row[j]);
        } else {
          v[i][j] = max(min(v[i+1][j-1], v[i+2][j]) + row[i], min(v[i][j-2], v[i+1][j-1]) + row[j]);
        }
      }
    }
    return v[0][v.length-1];
 }
```