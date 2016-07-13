---
layout: post
title: Building Bridges
tags:
- Algorithm
- Dynamic Programming

---
The problem is that you have two rows of cities (2n in total), for convenience, we call them north row and south row. For each row, the cities are named by a unique number (1...n). For example, if we have 6 cities in total, we have 3 in the north row, and 3 in the south row. We want to build bridges to connect cities with the same name. Notice that cities in each row are not necessarily in any order (i.e., the order is random). Compute the maximum number of bridges we can build without crossing any bridges.

OK, so, I wrote the solution myself for this one, but when I check my version with the existing one, the result is troubling. What you can find online is to first form pairs between cities, and then sort the pair by the south city number, and then use the longest increasing sequence (LIS) approach to compute the maximum number bridges possible. Well, this is simply wrong. 

Here is why.

For example, let's say we have the following situation:

```
2 4 5 1 3
=========
2 5 1 3 4
```

By just looking at the diagram, we know that we can form the following bridges:

`(2, 2)`, `(5, 5)`, `(1, 1)`, `(3, 3)`

We don't build `(4, 4)` because it would cross three bridges. This is simply and easy. Let's see what result you will get if you use the aforementioned wrong algorithm.

First, we form number pairs, to distinguish it between the bridge, I will use `[` and `]`.

`[2, 2]`, `[4, 5]`, `[5, 1]`, `[1, 3]`, `[3, 4]`

Now, we sort it by cities in the south row (You can do north as well).

`[5, 1]`, `[2, 2]`, `[1, 3]`, `[3, 4]`, `[4, 5]`

Now, we have an array `{5, 2, 1, 3, 4}`. The LIS of it is 1, 3, 4, and therefore according to this algorithm the maximum number of bridges possible is 3. But we know it should be 4. In case you want to test the wrong implementation yourself, [here](http://stackoverflow.com/a/20805839/1509779) is it.

I don't know why on the internet this wrong solution is everywhere. Probably because the [bcdean](https://people.cs.clemson.edu/~bcdean/dp_practice/) published this problem first and somehow his video solution got this wrong. Maybe everyone else then took solution from him (by the way, he said the complexity was `O(nlog(n))`, that's because LIS can be solved WITHOUT dp in `O(nlog(n))`, if you want to solve it using dp, the complexity is inevitably `O(n^2))`. This is sad because no one stands out and point out the incorrectness. OK, enough complaints, now let's go to my solution.

Just like LIS, we have an array that stores how many cities we can build including this city being connected without crossing any existing bridges. We compute this from the leftmost city to the rightmost, keeping the maximum number and then return it. For each city, we scan all previous (its left) cities and see whether building bridge for current city will cross the previous bridges.

Let's use the above example.

```
2 4 5 1 3
=========
2 5 1 3 4
```

Initially, the array is `[1, 1, 1, 1, 1]`. It's one because if we don't connect any previous cities, we can at least connect the current one. The following will be south row based, so when I say city i, I am referring to the one in the south row.

`2` can connect to `2`, so the array is `[1, 1, 1, 1, 1]`.

`5` can connect to `5` without crossing `(2, 2)`, so the array is `[1, 2, 1, 1, 1]`.

`1` can connect to `1` without crossing `(2, 2)` or `(5, 5)`, so the array is `[1, 2, 3, 1, 1]`.

`3` can connect to `3` without crossing `(2, 2)` or `(5, 5)`, or `(1, 1)`, so the array is `[1, 2, 3, 4, 1]`.

`4` can connect to `4`, but it will cross `(5, 5)` and `(1, 1)`, so the array is `[1, 2, 3, 4, 2]`.

So we return 4.

The following is my Java solution.

```
public int maxBridges(int[][] ns) { // assert n.len == s.len
    int[] n = ns[0];
    int[] s = ns[1];
    int[] northPosition = new int[n.length + 1]; // key: city name, val: index
    int[] southPosition = new int[n.length + 1]; // key: city name, val: index
    for (int i = 0; i < n.length; i++) {
      northPosition[n[i]] = i;
      southPosition[s[i]] = i;
    }
    int[] M = new int[n.length];
    Arrays.fill(M, 1);
    int max = Integer.MIN_VALUE;
    for (int i = 0; i < M.length; i++) {
      for (int j = 0; j < i; j++) { // south based
        int b1N = northPosition[s[i]];
        int b1S = southPosition[s[i]];
        int b2N = northPosition[s[j]];
        int b2S = southPosition[s[j]];
        if (!(b1N < b2N && b1S > b2S /* b1 b2 not crossed */) && M[j] + 1 > M[i]) {
          M[i] = M[j] + 1;
        }
        if (max < M[i]) {
          max = M[i];
        }
      }
    }
    return max;
}
```
The parameter ns is a 2D array that tells you how the cities are located. Notice the first city is named 1, not 0. northPosition is a map of city name (key) and its position in north row (1 based). The same goes for southPosition. We then populate the location of each city. I did this so that we can later quickly get the location information (to compute whether the bridge will cross).

M is the array that stores how many cities can we connect without crossing at this current city if we also have the current city connected.

b1N is the position of the current bridge's **n**orth pier.

b1S is the position of the current bridge's **s**outh pier.

b2N is the position of a previous bridge's **n**orth pier.

b2S is the position of a previous bridge's **s**outh pier.

`b1N < b2N && b1S > b2S` is to see if two bridges cross.