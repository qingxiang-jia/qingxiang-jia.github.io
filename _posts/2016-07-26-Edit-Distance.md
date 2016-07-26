---
layout: post
title: Edit Distance
tags:
- Algorithm
- Dynamic Programming

---
Given two strings A and B, compute the minimum cost to covert A to B. The allowed modifications are: deleting, inserting, and replacing, one character at a time, at any position.

I didn't figure out this problem myself so instead of providing my thought process, I will present the algorithm as clearly as I can.

First, all dp has subproblems and to solve the original problem we "grow" the subproblem step by step and reach the original problem eventually. The subproblem is the minimum edit distance between two substrings A[1..i] and B[1..j]. The solution to each subproblem is then stored in `D[i][j]`. The transition function grows the subproblem and eventually we get the solution of the original problem.

First, let's talk about the trivial case, where one of the string is empty. Say, we have the first substring being empty, `D[i][j]` is just `D[0][j]` and we know the solution is j. Why? Because the only way to convert an empty substring to B[1..j] is to insert j characters into A (Yes, I use "the first string" and A interchangeably, and the same goes for B). Similarly, when B is empty, `D[i][j]` is just `D[i][0]` and the solution to the subproblem is i.

Now, let's talk about the non-trivial case, where neither of A nor B are empty. We have three ways of modifying the first string A, so the transition function has four corresponding cases (including one where we don't do anything).

Case 1, we accomplish the conversion from A[1..i] to B[1..j] by deleting the ith character of A[1..i] and that costs 1; we then add the minimal cost (minimal edit distance) of converting A[1..i-1] to B[1..j]. So, we have `D[i][j]` = 1 + `D[i-1][j]`. Or, you can also view this using graph. `D[i-1][i]` + 1 reaches `D[i][j]`: if we already know `D[i-1][i]`, i.e., the minimum cost of converting A[1..i-1] to B[1..j], then the cost of converting A[1..i] to B[1..j] is just 1 more, which comes from removing A[i] from A[1..i] so that we form A[1..i-1].

Case 2, we accomplish the conversion from A[1..i] to B[1..j] by inserting B[j] to the end of A[1..i], and that costs 1, we then add the minimal cost of converting A[1..i] to B[1..j-1]. So, we have `D[i][j]` = 1 + `D[i][j-1]`. Or, you can also view this using graph. `D[i][j-1]` + 1 reaches `D[i][j]`: if we already know `D[i][j-1]`, i.e., the minimum cost of converting A[1..i] to B[1..j-1], then the cost of converting A[1..i] to B[1..j] is just 1 more, which comes from adding B[j] to the end of A[1..i], so A[i+1] == B[j]. This in fact is tricky and I think this is why some people said on Geeks for Geeks that the insert and delete are flipped. This misunderstanding is so common that a [CS professor](http://jeffe.cs.illinois.edu/teaching/algorithms/notes/05-dynprog.pdf) also thought them flipped. No, they are NOT. Please see the diagram below if you think they are flipped.

For case 2, we already know `D[i][j-1]`, the minimum cost to convert A[1..i] to B[1..j-1]. We correspond `A[i+1]` (`A[i+1] == B[j]`) to `B[j]`.

```
  +---+---+---+---+---+---+---+---+ +---+
A |1  |...|...|...|...|...|...|i  | |i+1|
  +---+---+---+---+---+---+---+---+ +---+
  +---+---+---+---+---+---+---+---+ +---+
B |1  |...|...|...|...|...|...|j-1| |j  |
  +---+---+---+---+---+---+---+---+ +---+
```

Case 3, we accomplish the conversion from A[1..i] to B[1..j] by replacing the ith character of A[1..i] with the jth character of B[1..j], the replacing costs 1, but for the total cost, we need also add in the minimum cost of converting A[1..i-1] to B[1..j-1]. To view it in terms of graph, `D[i-1][j-1]` + 1 reaches `D[i][j]`: if we already know the minimum cost to convert A[1..i-1] to B[1..j-1], the cost of converting A[1..i] to B[1..j] is just 1 plus that. Why? Because we just replace whatever `A[i]` is with `B[j]`.

Case 4, the same as case 3 except that `A[i] == B[j]` so no replacing needed.

Now, we don't know which case will yield the minimal cost, so we take the minimum of the three. All three is a solution but only one of them is the best.

Below is my Java solution, with the comments, it should be self-explanatory. Let's have a dry run just to get familiar with the algorithm.

```
private static final int REPLACE = 1, INSERT = 1, DELETE = 1;

  public int editDistance(String A, String B) {
    int[][] D = new int[A.length() + 1][B.length() + 1];
    for (int i = 0; i < D.length; i++) {
      for (int j = 0; j < D[0].length; j++) {
        if (i == 0) {
          D[i][j] = j;
        } else if (j == 0) {
          D[i][j] = i;
        } else {
          int byInserting = D[i-1][j] + DELETE;
          int byDeleting = D[i][j-1] + INSERT;
          int byReplacing;
          if (A.charAt(i-1) == B.charAt(j-1)) { // for A, B, things start at 0, so i-1/j-1 for A/B is i/j for D
            byReplacing = D[i-1][j-1]; // since A[i-1] == B[j-1], we don't need any of the three operations,
            // notice this i-1/j-1 for A/B doesn't correspond to D[i-1][j-1], this looks very confusing.
          } else {
            byReplacing = D[i-1][j-1] + REPLACE; // replace A[i-1] with B[j-1], and take the previous optimal solution D[i-1][j-1]
          }
          D[i][j] = min(byDeleting, byInserting, byReplacing); // D[i][j] corresponds to A[i-1] and B[j-1]
        }
      }
    }
    return D[A.length()][B.length()];
 }
```

Suppose we have input "ssd" and "sdsd". Initially, the table looks like the following:

```
   Ø  s  d  s  d
  +--+--+--+--+--+
Ø |  |  |  |  |  |
  +--+--+--+--+--+
s |  |  |  |  |  |
  +--+--+--+--+--+
s |  |  |  |  |  |
  +--+--+--+--+--+
d |  |  |  |  |  |
  +--+--+--+--+--+
```

First, both of them are empty strings, and we have 0.

```
   Ø  s  d  s  d
  +--+--+--+--+--+
Ø |0 |  |  |  |  |
  +--+--+--+--+--+
s |  |  |  |  |  |
  +--+--+--+--+--+
s |  |  |  |  |  |
  +--+--+--+--+--+
d |  |  |  |  |  |
  +--+--+--+--+--+
```

Next, we are converting empty string with non-empty one. As discussed, this is one of the base case, and the same goes for the rest of this row.

```
   Ø  s  d  s  d
  +--+--+--+--+--+
Ø |0 |1 |2 |3 |4 |
  +--+--+--+--+--+
s |  |  |  |  |  |
  +--+--+--+--+--+
s |  |  |  |  |  |
  +--+--+--+--+--+
d |  |  |  |  |  |
  +--+--+--+--+--+
```

Now we are converting "s" to "", another base case, so 1.

```
   Ø  s  d  s  d
  +--+--+--+--+--+
Ø |0 |1 |2 |3 |4 |
  +--+--+--+--+--+
s |1 |  |  |  |  |
  +--+--+--+--+--+
s |  |  |  |  |  |
  +--+--+--+--+--+
d |  |  |  |  |  |
  +--+--+--+--+--+
```

Then we are converting "s" to "s". We have four cases. First, it sounds stupid but we can try to convert "s" to "s" by deleting our only character 's' AT THIS STEP, which yields 2 (`D[0][1]` + 1). How so? Well, we are at state "s" vs "s", by deleting the only 's', we get "" vs "s" and `D[0][1]` says we can get "s" vs "s" from "" vs "s" by adding one. So, in short this means we convert "s" to "s" by first remove the first 's' and add it back. As stupid as it is, but this is a valid solution.

We can also convert "s" to "s" by inserting 's' at the end of 's' AT THIS STEP, which yields 2 (`D[1][0]` + 1). We are at state "s" vs "s", by adding 's', we correspond the newly added 's' (`A[i+1]`) with `B[j]` (of course `j==1` and `B[1]=='s'`), and `D[1][0]` says A[1..i] and B[1..i-1] is already computed, is 1. What exactly does `D[1][0]` say: to convert "s" to "", we just remove the 's'. So, in short, this choice adds a new 's' to "s" and remove the first 's' to get "s" vs "s". It's stupid but it is a valid option.

The third option is to check whether `A[i] == B[j]`, and yes, so we skip this option.

Since `A[i] == B[j]`, we are at the fourth option, which is do nothing. So we have `D[1][1]` to be 0.

Usually I will run it to the end, but this time I want to stop. Not that I am getting lazy but this problem is harder than it looks. So it's better to focus on the important part than a dry run. Why so? Just look at *Geeks for Geeks* and see that the analysis and code doesn't match. The code got the inserting and deleting right, but the analysis got it flipped. Read all the comments below (click "load more comments"), at least three people suggested the that the code should follow the analysis (which is wrong). Also, take a look at [this](http://jeffe.cs.illinois.edu/teaching/algorithms/notes/05-dynprog.pdf) algorithm class material, the professor also got the inserting and deletion part flipped (chapter 5). Why so many people make this mistake? I don't know. One possible reason is that even if you got it flipped, you will get the correct solution, not just the final solution, but the entire table is correct. So, I guess they are in some sense "equivalent", but our language (or just me) can't make it reasonable. 