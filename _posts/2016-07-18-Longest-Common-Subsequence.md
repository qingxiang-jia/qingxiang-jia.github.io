---
layout: post
title: Longest Common Subsequence
tags:
- Algorithm
- Dynamic Programming

---
There are two strings A and B, and we want to compute the longest common subsequence (L.C.S., for convenience, I call it LCS). The definition of common subsequence is a string that is contained in both A and B, but they don't have to be contiguous. For example, the LCS of "KPLU" and "POOL" is "PL". In "POOL", "P" and "L" is not contiguous, also it's not required for them to be adjacent in "KPLU" either.

Here is the thought process of using dynamic programming to solve this problem. We have a table to store solutions of subproblems. What is the subproblem? Suppose we have A of length `m`, and B of length `n`. The sub-solution is the length of the LCS of substrings of A and B. Like all other dp questions, instead of computing the LCS string itself, we compute the length of it (This post doesn't include the computation of the LCS string, it only contains the computation of legnth. I will add the string part later).

The transition function is:

`M[i][j]` = `M[i-1][j-1]` + 1 if `A[i]` == `B[j]`

`M[i][j]` = max(`M[i][j-1]`, `M[i-1][j]`) if `A[i]` != `B[j]`

First, let's talk about the meaning of `M[i][j]`: the length of LCS between `A[1..i]` and `B[1..j]`. So, how to interpret the transition function. For the first part, it is relatively easy. It says if `A[i]` is the same as `B[j]`, then all we need to do is take the solution of `A[1..i-1]` and `B[1..j-1]` and plus one. Why? We can see `A[1..i]` as `A[1..i-1]` concatenated with `A[i]`. The same goes for B. Since `A[i]` equals `B[i]`, the solution between `A[1..i]` and `B[1..j]` is just the solution between `A[1..i-1]` and `B[1..j-1]` plus one.

For the second part, it's a bit tricky. If `A[i]` doesn't equal to `B[j]`, then we need to find the maximum between `M[i][j-1]` and `M[i-1][j]`. When I first see this, I asked myself, why not `i-2`, `i-3`, `j-2`, `j-3` and so on? Because `M[i][j-1]` is the best we can get at this point. You can certainly take `M[i][j-2]` or `M[i][j-3]`, and it may even be equal to `M[i][j-1]`, but in the worst case, `M[i][j-1]` is as good as `M[i][j-2]` and `M[i][j-3]`. In other cases, `M[i][j-1]` is better than `M[i][j-2]` and `M[i][j-3]`, and that's why you can't just take `M[i][j-2]` and `M[i][j-3]` or other arbitrary previous cells. Remember `M` stores the solution of substrings of A and B. Yes, in some case, a shorter substring of A or B may yield the same solution as the longer substrings, a longer substring always get potentially better solution. Why it that? Because longer substring gives more chance for longer LCS. It doesn't require you to take all characters of the substrings, it but gives potential to do so.

OK, now, go back to the second part of the transition function. If `A[i]` != `B[j]`, that means either we compare `A[1..i-1]` with `B[1..j]` or we compare `A[1..i]` and `B[1..j-1]`. We don't do `A[1..i-1]` with `B[1..j-1]` because potentially comparing `A[1..i-1]` with `B[1..j]` is better than `A[i..i-1]` with `B[1..j-1]`. Similarly, comparing `A[1..i]` with `B[1..j-1]` is better than `A[1..i-1]` with `B[1..j-1]`.

The following is my Java solution. Notice that M is dimension `[A.length() + 1][B.length() + 1]`. I guess you can have it with dimension `[A.length()][B.length()]`, but it may lead to extra code. In my code, `M[i][0]` or `M[j][0]` means the solution of comparing an empty string with A or B respectively, and they should be 0, but since Java initialize arrays with 0, I don't need to fill them myself, and so I have "`if (i != 0 && j != 0)`".

```
public int LCS(String A, String B) {
    int[][] M = new int[A.length() + 1][B.length() + 1];
    for (int i = 0; i < M.length; i++) {
      for (int j = 0; j < M[0].length; j++) {
        if (i != 0 && j != 0) {
          if (A.charAt(i-1) == B.charAt(j-1)) {
            M[i][j] = M[i-1][j-1] + 1;
          } else {
            M[i][j] = max(M[i-1][j], M[i][j-1]);
          }
        }
      }
    }
    return M[A.length()][B.length()];
}
```

The code is straightforward, but notice I have "`if (A.charAt(i-1) == B.charAt(j-1))`". That's because `M[i][j]` actually corresponds to `A[i-1]` and `B[j-1]`. We have `M[0][0]` corresponds to the empty string.

Let's run it manually with a simple sample case, A="ATC" and B="AC".

```
   Ø  A  C
  +--+--+--+
Ø |  |  |  |
  +--+--+--+
A |  |  |  |
  +--+--+--+
T |  |  |  |
  +--+--+--+
C |  |  |  |
  +--+--+--+
```

M is represented in the above diagram. Initially, all cells are filled with zeros, and I use blank for it. The LCS of empty string is still empty string, so the lengh is 0. Similarly, the entire first row is filled with 0.

```
   Ø  A  C
  +--+--+--+
Ø |0 |0 |0 |
  +--+--+--+
A |  |  |  |
  +--+--+--+
T |  |  |  |
  +--+--+--+
C |  |  |  |
  +--+--+--+
```

Next, i=1, j=0, "A" compares with "", we get "" and its length is 0.

```
   Ø  A  C
  +--+--+--+
Ø |0 |0 |0 |
  +--+--+--+
A |0 |  |  |
  +--+--+--+
T |  |  |  |
  +--+--+--+
C |  |  |  |
  +--+--+--+
```

i=1, j=1, "A" compares with "A", since A[0] == B[0], we have `M[1][1]` = `M[0][0]` + 1 == 1.

```
   Ø  A  C
  +--+--+--+
Ø |0 |0 |0 |
  +--+--+--+
A |0 |1 |  |
  +--+--+--+
T |  |  |  |
  +--+--+--+
C |  |  |  |
  +--+--+--+
```

i=1, j=2, "A" compares with "AC", since `A[0]` != `B[1]`, we have `M[1][2]` = max(`M[0][2]`, `M[1][1]`), so we fill it with 1.

```
   Ø  A  C
  +--+--+--+
Ø |0 |0 |0 |
  +--+--+--+
A |0 |1 |1 |
  +--+--+--+
T |  |  |  |
  +--+--+--+
C |  |  |  |
  +--+--+--+
```

i=2, j=0, as discussed before, we get 0.

```
   Ø  A  C
  +--+--+--+
Ø |0 |0 |0 |
  +--+--+--+
A |0 |1 |1 |
  +--+--+--+
T |0 |  |  |
  +--+--+--+
C |  |  |  |
  +--+--+--+
```

i=2, j=1, comparing "AT" with "A", since `A[1]` != `B[0]`, we have `M[2][1]` = max(`M[1][1]`, `M[2][0]`), which results in 1.

```
   Ø  A  C
  +--+--+--+
Ø |0 |0 |0 |
  +--+--+--+
A |0 |1 |1 |
  +--+--+--+
T |0 |1 |  |
  +--+--+--+
C |  |  |  |
  +--+--+--+
```

i=2, j=2, comparing "AT" with "AC", since `A[1]` != `B[1]`, we have `M[2][2]` = max(`M[1][2]`, `M[2][1]`), which results in 1.

```
   Ø  A  C
  +--+--+--+
Ø |0 |0 |0 |
  +--+--+--+
A |0 |1 |1 |
  +--+--+--+
T |0 |1 |1 |
  +--+--+--+
C |  |  |  |
  +--+--+--+
```

i=3, j=0, as discussed before, we get 0.

```
   Ø  A  C
  +--+--+--+
Ø |0 |0 |0 |
  +--+--+--+
A |0 |1 |1 |
  +--+--+--+
T |0 |1 |1 |
  +--+--+--+
C |0 |  |  |
  +--+--+--+
```

i=3, j=1, comparing "ATC" with "A", since A[2] != B[0], we have `M[3][1]` = max(`M[2][1]`, `M[3][0]`), which results in 1.

```
   Ø  A  C
  +--+--+--+
Ø |0 |0 |0 |
  +--+--+--+
A |0 |1 |1 |
  +--+--+--+
T |0 |1 |1 |
  +--+--+--+
C |0 |1 |  |
  +--+--+--+
```

i=3, j=2, comparing "ATC" with "AC", since `A[2]` == `B[1]`, we have `M[3][2]` = `M[2][1]` + 1, which is 2.

```
   Ø  A  C
  +--+--+--+
Ø |0 |0 |0 |
  +--+--+--+
A |0 |1 |1 |
  +--+--+--+
T |0 |1 |1 |
  +--+--+--+
C |0 |1 |2 |
  +--+--+--+
```