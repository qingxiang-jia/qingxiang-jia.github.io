---
layout: post
title: Longest Consecutive Path
tags:
- Algorithm
- Dynamic Programming

---
You are given a table of letters (repetition allowed). Compute the length of longest consecutive (alphabetic order) path (8 directions allowed: upper, upper left, upper right, left, right, lower, lower left, lower right).

For example (problem and example taken from Geeks for Geeks, but I solved the problem independently), if you have the following table:

```
+--+--+--+
|a |c |d |
+--+--+--+
|h |b |e |
+--+--+--+
|i |g |f |
+--+--+--+
```

The solution for 'i' should be 1, as the path only includes the letter itself.
The solution for 'h' should be 2, as the path is h->i.

I didn't have a clue the first time I saw this problem. I tried to find the solution by hand for each cell.

```
a: a->b->c->d->e->f->g->h->i 9
b:    b->c->d->e->f->g->h->i 8
c:       c->d->e->f->g->h->i 7
d:          d->e->f->g->h->i 6
e:             e->f->g->h->i 5
f:                f->g->h->i 4
g:                   g->h->i 3
h:                      h->i 2
i:                         i 1
```

This example is kind of extreme in the sense that each cell has a solution that is a sub-solution of the other cell. It clearly shows the subproblem and the relationship between them. What this tells me is that possibly, each cell contains a subproblem, we can solve it one by one. So I have the following transition function:

len(i, j) = max{len(row, col) where row and col represents the valid surrounding of cell(i, j), and table(row, col) is to the left (nothing in between) of table(i, j) in alphabetical order} + 1.
(Table len stores the length of the path ending at the cell.)

But, in what order? Well, recall that the path, however long it might be, sis always in alphabetical order. If we start computing the last one, say, 'z', it won't have any dependency. Then, we can try to find 'y', the only dependency of 'y' is 'z', and by the time we compute 'y', we have already computed 'z'. 

1) Initialize every cell of the len table to 1 as if there is no other cell around, that's the length of the path.

2) For letters, pick them one by one in reversed alphabetical order. For each of them, check its surrounding (up to 8 neighbors), and see if the neighbor is one left to the current one. If so and if the value of the neighbor is less than one plus the current letter's value, then we update the neighbor's value (we do this because there may be a shorter path, and we only want the longest).

3) Since we want the longest path for a given character, we search through the table, and pick the highest value associated with that character, and return it.

The following is my Java solution. The data structure is not that beautiful so let me explain it. posMap is a List<List<int[]>>. Letter a's position(s) is stored in the 0th cell in the list. Letter z's position is stored in the 25th cell in the list. We use ArrayList so random access is possible with cost O(1). Since 'a' is just integer 97, we have mapping from char to int, and int to char. We use this mapping along with random access provided by ArrayList to quickly retrieve the positions of a given letter. The positions are stored in List<int[]>, the int[] is an integer pair, where the first element represents row, the second represents column.

```
  static final int[] ROW_DIRECTION = new int[]{-1, -1, 0, 1, 1, 1, 0, -1};
  static final int[] COL_DIRECTION = new int[]{0, 1, 1, 1, 0, -1, -1, -1};

  public int maxConsecutiveLen(char[][] table, char c) {
    List<List<int[]>> posMap = new ArrayList<>();
    for (int alphabet = 0; alphabet < 26; alphabet++) {
      posMap.add(new ArrayList<>());
    }

    for (int row = 0; row < table.length; row++) {
      for (int col = 0; col < table[0].length; col++) {
        posMap.get(index(table[row][col])).add(new int[] {row, col});
      }
    }

    int[][] len = new int[table.length][table[0].length];
    for (int row = 0; row < len.length; row++) { // init each cell to 1
      for (int col = 0; col < len[0].length; col++) {
        len[row][col] = 1;
      }
    }

    for (int i = posMap.size() - 1; i >= 0; i--) {
      for (int[] pos : posMap.get(i)) { // for each position of this character
        for (int directionIndex = 0; directionIndex < ROW_DIRECTION.length; directionIndex++) { // check surrounding
          int row = pos[0];
          int col = pos[1];
          row = row + ROW_DIRECTION[directionIndex];
          col = col + COL_DIRECTION[directionIndex];
          if (row < len.length && row >= 0 && col < len[0].length && col >= 0) {
            if (index(table[row][col]) + 1 == i) { // if table[row][col] is one left to i
              if (len[row][col] < 1 + len[pos[0]][pos[1]]) {
                len[row][col] = 1 + len[pos[0]][pos[1]];
              }
            }
          }
        }
      }
    }

    int maxLen = 0;
    for (int row = 0; row < len.length; row++) {
      for (int col = 0; col < len[0].length; col++) {
        if (table[row][col] == c) {
          if (maxLen < len[row][col]) {
            maxLen = len[row][col];
          }
        }
      }
    }
    printTable(len);
    return maxLen;
  }
```

We then initialize posMap. After that, we initialize len table (which has been discussed). We then run the algorithm. Lastly, we construct the solution using len table.

To get familiar with the algorithm, let's have a dry run with the following sample data.

```
+--+--+--+
|b |e |f |
+--+--+--+
|h |d |a |
+--+--+--+
|i |c |a |
+--+--+--+
```

Initially, the len table looks like the one below.

```
+--+--+--+
|1 |1 |1 |
+--+--+--+
|1 |1 |1 |
+--+--+--+
|1 |1 |1 |
+--+--+--+
```

We then pick letter 'z', which doesn't exist. We skip until we hit 'i'. We look around, 'h' is a valid neighbor and 2 > 1, so we update the value of 'h' to 2.

```
+--+--+--+
|1 |1 |1 |
+--+--+--+
|2 |1 |1 |
+--+--+--+
|1 |1 |1 |
+--+--+--+
```

We pick 'h'. No letter around it is one left to it, in fact, we don't have 'g' in the table, so nothing happens.

We pick 'f', 'e' is a valid neighbor of it and it one left to it, and 2 > 1, so we update the value of 'e' to 2.

```
+--+--+--+
|1 |2 |1 |
+--+--+--+
|2 |1 |1 |
+--+--+--+
|1 |1 |1 |
+--+--+--+
```

We pick 'e'. 'd' is a valid neighbor and is one left to it, and 3 > 1, so we update the value of 'd' to 3.

```
+--+--+--+
|1 |2 |1 |
+--+--+--+
|2 |3 |1 |
+--+--+--+
|1 |1 |1 |
+--+--+--+
```

We pick 'd'. 'c' is a valid neighbor and is one left to it, and 4 > 1, so we update the value of 'c' to 4.

```
+--+--+--+
|1 |2 |1 |
+--+--+--+
|2 |3 |1 |
+--+--+--+
|1 |4 |1 |
+--+--+--+
```

We pick 'c'. No neighbor around it is one left to it, i.e., 'b'. So nothing happens.

We pick 'b'. No neighbor around it is one left to it, i.e., 'a'. So nothing happens.

We pick 'a'. There are two occurrences of it, but there is nothing to the left of 'a'. So nothing happens.