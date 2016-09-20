---
layout: post
title: Sequence Alignment
tags:
- Algorithm
- Kleinberg & Tardos

---

The problem is on p.281 of Algorithm Design by Kleinberg & Tardos. If you don't have a book, here is the problem description.

We are given two strings, and we want to find the minimum cost to align them together. For example, say we have "stop" and "tops" and we can align them like this:

```
stop-
-tops
```

where "top" is the aligned part, and we have two gaps in total ("-" represents a gap).

We can also align the words like this:

```
stop
tops
```

But doing so we have four mismatches, and we aligned nothing.

Define the cost of a mismatch to be 1, and the cost of a gap to be 1 as well. In the first example (indeed, it is the minimum cost), the cost is 2. In the second one, the cost is 4 (nothing aligned).

We can solve this problem using dynamic programming. In fact, the code for this is identical to the dynamic programming solution for edit distance. Well, "sequence alignment" is a synonym of "edit distance". So what's the point of repeating? The point is, to think this problem differently. Recall in edit distance, we think about adding a character, removing a character, and replacing a character so one string can be eventually converted to another one. But here, thinking it as alignment is equivalent, and I personally feels it more intuitive.

So, when aligning two words, if we go character by character, you have three cases. Case 1, the characters match. Whatever the minimum cost so far remains the same. Case 2, the characters don't match and you choose to put a gap there, this will increase the minimum cost so far by 1 (or whatever cost you set). Case 3, the characters don't match and you choose to live with it -- counting it as a mismatch and go on. The minimum cost so far equals whatever the smallest at this point, leading us to the following transition function:


**optimal[i][j] = min((if x[i]=y[j] then 0 else 1) + optimal[i-1][j-1], 1 + optimal[i-1][j], 1 + optimal[i][j-1])**

Notice that these three parameters (of function `min`) are actually not case 1 through 3. The first expression includes both case 1 and 3. The second and third expression correspond to case 2. This is because when you choose to put a gap, you in fact have two choices. You can either put a gap in string x, or do so in string y. But we don't know which choice leads to a better solution so we try both and take the minimum.

The following is my Java solution. Since we ran a dry run when dealing with edit distance, I will skip it here.

```
public int minCost(String x, String y) {
    int[][] optimal = new int[x.length() + 1][y.length() + 1];
    for (int i = 0; i < x.length() + 1; i++) {
      optimal[i][0] = i;
    }
    for (int j = 0; j < y.length() + 1; j++) {
      optimal[0][j] = j;
    }

    for (int i = 1; i < x.length() + 1; i++) {
      for (int j = 1; j < y.length() + 1; j++) {
        optimal[i][j] = min((x.charAt(i-1) == y.charAt(j-1) ? 0 : 1) + optimal[i-1][j-1], 1 + optimal[i-1][j], 1 + optimal[i][j-1]);
      }
    }
    printTable(optimal);
    return optimal[x.length()][y.length()];
}

public static int min(int...args) {
    int min = Integer.MAX_VALUE;
    for (int k : args) {
      if (k < min) {
        min = k;
      }
    }
    return min;
}
```