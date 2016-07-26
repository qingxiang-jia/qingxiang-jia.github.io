---
layout: post
title: Boolean Parenthesization
tags:
- Algorithm
- Dynamic Programming

---
Given a boolean expression (operator: AND, OR, XOR; operand: true, false), compute how many ways to place parentheses so that the result is evaluated to true.

The first moment I encountered this question, I thought the problem is not clearly stated. It didn't say how to place the parentheses. For example, would you consider "(true)" and "((((true))))" to be equal? How about "true OR (false)" and "(true) OR (false)"? My experience is that when it doesn't say anything about it, it means the normal way, that is, yes, both cases are considered equal.

The next thing that I thought unclear is how to represent the data. Would you put them into a string so I have "true AND false", or would you put them in an array so I have ["true", "AND", "false"]? If using array, I probably have to parse it, but would the original array come with pre-exisitng parentheses? My gut told me that I don't need to worry about it, and the given data should be clean.

Also, how to put parenthesis? If you have "true false", should you append a "(" to the beginning, and insert a ")" between "true" and "false"? Again, I know it should be irrelevant. Most likely the way to represent parenthesis may even be implicit.

To make sure my worries are irrelevant, I went to Geeks for Geeks and realized the data are given in two arrays. You have an array of operands (true, false) and one with operators (`'&'` -> AND, `'|'` -> OR, `'^'` -> XOR). I was trying to figure out it myself but I accidentally took a glimpse of the transition function and I immediately gave up.

The first thing to realize is this question is not about putting parenthesis at all. We use a 2D array `T` to record the number of ways to put the parenthesis for all subexpressions that lead to true, which also includes the full expression. We also use a 2D array `F` to record the number of the parenthesis for all subexpressions that lead to false. The subproblem is the number of ways to put parenthesis such that it evaluates to true/false. How to represent a subexpression? Using the beginning index and ending index of the operator array (inclusive). For example, given "true false true false", `T[1][3]` represent the number of ways to put parenthesis that leads to true for the last three operators. `T[0][3]` is the solution to the full expression. I think this is the most difficult part in this question. When you realize it's not about putting parenthesis, you are half way done. Note when I say subexpression, I really mean operands, not the operators.

Suppose you are looking at a subexpression operand[i..j] with corresponding operator[i..j-1], and we have i..k..j (k=i..j-1). You should loop through all possible k, and accumulate the number of ways to place parenthesis that lead to true/false. Specifically,

  For simplicity, let `total_ik` = `T[i][k]+F[i][k]`; let `total_kj` = `T[k+1][j]`+`F[k+1][j]`.
  `total_ik` denotes the total number of ways of placing parenthesis in operand[i..k].
  `total_kj` denotes the total number of ways of placing parenthesis in operand[k+1..j].
  Note that `total_kj` doesn't imply operand[k..j]. Instead, it denotes `k+1`. Unfortunately I can't put + in variable name in Java.

  If the kth operator is `'&'`, then 
  
  `T[i][j]` += `T[i][k]` * `T[k+1][j]`
  
  `F[i][j]` += `total_ik` * `total_kj` - `T[i][k]` * `T[k+1][j]`
  
  Explanation: for `T[i][j]`, for this k, it is simply the number of ways that lead to true in operand[i..k] times the number of ways that lead to true in operand[k+1..j]. For `F[i][j]`, for this k, it is the total number of ways between operand[i..k] and operand[k+1..j] minus the ways that lead to true.

  If the kth operator is `'|'`, then 
  
  `T[i][j]` += `total_ik` * `total_kj` + `F[i][k]` * `T[k+1][j]`
                                   
  `F[i][j]` += `F[i][k]` * `F[k+1][j]`
                                   
  Explanation: similar to the `'&'` case, just consider how `'|'` works.

  If the kth operator is `'^'`, then 
  
  `T[i][j]` += `T[i][k]` * `F[k+1][j]` + `F[i][k]` * `T[k+1][j]`
                                   
  `F[i][j]` += `T[i][k]` * `T[k+1][j]` + `F[i][k]`*`F[k+1][j]`
                                   
  Explanation: similar to the `'|'` case, just consider how `'^'` works.

Finally, `T[0][n-1]` contains the solution for the entire expression (where `n` is the total number of operands). In case you wonder why not `T[0][n]`, we have stated that the indices are inclusive.

The above transition function applies when you look at a subexpression[i..j]. But how to pick such one. You gradually increase the length of the subexpression. For example, you start with operand[0..1], and then [1..2], [2..3]; [0..2], [1..3]; [0..3].

Why couldn't I compute it in a different order? Say, [0..1], [0..2], [0..3]; [1..2], [1..3]. Because the correct order ensures that when you compute a larger solution, all its needed subproblem has been solved already. Let's look at an example where you have 4 operands.

```
+----+----+----+----+
|0   |1   |2   |3   |
+----+----+----+----+
 <--> <--> <--> <-->  initialization loop: you compute each operand separately.
 <------->
      <------->
           <------->  first loop: each computation requires previous sub-solutions (the ones the double arrow spans).
 <------------>
      <------------>  second loop: used results from both the initialization loop and the first loop.
 <----------------->  third loop: used results from all previous loops.
```

 If the above diagram isn't clear enough, let's talk about it elaborately. For the initialization loop, what we did really is to fill the diagonal of `T` and `F`. Why? Because it denotes every individual operand, the indices are `T[i][i]` and `F[i][i]`. If we have operand[i] to be `'T'`, then `T[i][i]` should be 1 as there is only one way to place the parentheses and it always evaluates to true. Similarly, `F[i][i]` should be 0. Conversely, if operand[i] is `'F'`, `T[i][i]` should be 0 and `F[i][i]` should be 1.

 For the first loop, we first consider the case where i=0, j=1. In this case, we only have one place for k, index 0, that is, the place between operand #0 and #1. Well if you don't see that k should be in the middle of operand #0 and #1, let's read the diagram below.

```
                +---+---+---+---+
 operand array  |0  |1  |2  |3  |
                +---+---+---+---+
                  +---+---+---+
  operator array  |0  |1  |2  |
                  +---+---+---+
```

From the diagram, it is clear that operator #0 is in between of operand #0 and #1, likewise for the rest of operators.

Since k is in between operator #0 and #1, it divides the subexpression [0..1] into [0..0] and [1..1] and requires information from `T/F[0][0]` and `T/F[1][1]`. The next case, where we consider subexpression [1..2], k divides it into [1..1] and [2..2] and thus needing sub-solution `T/F[1][1]` and `T/F[2][2]`. Next, k divides [2..3] and we need sub-solution for [2..2] and [3..3] thus `T/F[2][2]` and `T/F[3][3]`.

In the second loop, it first considers [0..2] and thus giving two places for k: 0, 1. For k at 0, it divides [0..2] into [0..0] and [1..2] and thus we need sub-solution `T/F[0][0]` and `T/F[1][2]`. Then, k moves to 1, dividing [0..2] into [0..1] and [2..2], thus we need sub-solution `T/F[0][1]` and `T/F[2][2]`. Then, it looks at [1..3], and the analysis is very similar and thus I skip this part.

In the third loop, the only subexpression it considers is the entire expression [0..3] which gives three spots for k: 0, 1, 2. For each spot of k, it needs sub-solution from the previous subproblems. The analysis is again very similar and therefore I skip it.

This is a very classical example of dynamic programming, although it is relatively complicated.

The following is my Java solution. Usually I will do a dry run to just illustrate the algorithm, but this time I think the above analysis does the same thing.

```
public int countParenthesization(char operand[], char operator[]) {
    int n = operand.length;
    int T[][] = new int[n][n];
    int F[][] = new int[n][n];

    for (int i = 0; i < n; i++) {
      if (operand[i] == 'T') {
        T[i][i] = 1;
      } else {
        F[i][i] = 1;
      }
    }

    for (int initJ = 1; initJ < n; initJ++) {
      for (int i = 0, j = initJ; j < n; i++, j++) {
        for (int k = i; k < j; k++) {
          int total_ik = T[i][k] + F[i][k];
          int total_kj = T[k+1][j] + F[k+1][j];
          if (operator[k] == '&') {
            T[i][j] += T[i][k] * T[k+1][j];
            F[i][j] += total_ik * total_kj - T[i][k] * T[k+1][j];
          } else if (operator[k] == '|') {
            T[i][j] += total_ik * total_kj - F[i][k] * F[k+1][j];
            F[i][j] += F[i][k] * F[k+1][j];
          } else if (operator[k] == '^') {
            T[i][j] += F[i][k] * T[k+1][j] + T[i][k] * F[k+1][j];
            F[i][j] += T[i][k] * T[k+1][j] + F[i][k] * F[k+1][j];
          }
        }
      }
    }
    return T[0][n-1];
 }
```