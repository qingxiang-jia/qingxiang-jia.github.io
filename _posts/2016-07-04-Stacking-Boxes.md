---
layout: post
title: Stacking Boxes
tags:
- Algorithm
- Dynamic Programming

---
You are given an array of boxes. Each box has three dimensions: height, width, depth `(h, w, d)`. The constraint is that a box can only be placed on another if its `w`, and `d` are strictly less than the other. You can reuse each type of box. You can also rotate a box. Compute the maximum height possible.

When I first see this problem, I was confused as it says "each box can be reused." Does that mean I can just stack on type of box forever and get infinity as the maximum? No, in case you have the same doubt as I did, notice the constraint "strictly less than," that means you can't just keep reusing one type of box without rotation.

I didn't come up with the solution myself, but this would be my thought process if I ever encounter this problem again. First, for each type of boxes, you can only reuse it at most two times as each box has only three dimensions and with the constraint, if you reuse it the third time, you will violate the constraint on dimensions.

If you don't believe this, consider a box with dimension `x`, `y`, `z`. where `x != y`, `y != z`, `x != z`. Now, the decision tree is like this:

**Legend: `(x, y)` => picking `x` and `y` as the base dimension.**

`(x, y)` -> `(y, z)` -> `(x, z)`

`(x, y)` -> `(x, z)` -> `(y, z)`

`(x, z)` -> `(x, y)` -> `(y, z)`

`(x, z)` -> `(y, z)` -> `(x, y)`

`(y, z)` -> `(y, z)` -> `(x, z)`

`(y, z)` -> `(x, z)` -> `(x, y)`

Let's pick the first branch (any one will work). So, on the first level, we have `x` and `y` as the base dimension. According to the constraint, the following holds: `x > y` and `y > z`. Then, between the second and the third level, with the constraint, we should have `y > x` and `z > z`. We have two contradictions: `z > z` is a contradiction; `x > y` and `y > x` is another contradiction.

Going back to the problem, although we can at most use the same type of boxes twice, but this only holds if you only have one type. It means if we have more types with various dimensions, we actually might be able to use all three types because they don't have to be used next to each other.

Having said that, given an array of boxes, we can generate all possible rotations. Next, we sort all those boxes by base area (increasing order in my case, either way works). Why would we do this? I searched for correctness of this approach, but found nothing. I will show my intuition later. We then use the approach used in "[longest increasing subsequence (L.I.S.)]({% post_url 2016-06-29-Longest-Increasing-Subsequence %})" to pick correct rotations.

Now, let's talk about the intuition. Because of the constraint, if we ever have a solution, it must be a sequence of rotations with increasing base area (or decreasing order, I will stop mention this from now on). If we don't have a correctly sorted sequence, we will never end up with an optimal solution. Put it another way, sorting doesn't give you the solution, but it gives you a set where the solution lies in. If you don't sort the rotations, you won't be able to have this set where one of its element is the solution.

Now I want to mention the transition function, which is:

(`M[i]` represents the maximum height of the stack ending at the ith rotation.
`h[i]` represents the height of the ith rotation.)

**`M[i]` = max{`M[j]` + `h[i]`} where `j` < `i`, `w[j]` < `w[i]` and `d[j]` < `d[i]`** 

(we initialize each cell in M with the height of the box/rotation because if we stack from this cell, the height is the height of this box). **Meaning of this function**: the maximum height of the stacking ending at the ith rotation is the sum of the previous stack height plus this rotation for all previous `0..j` rotations.

The following is my Java solution. Here, I used a three-element array to represent a box/rotation `(h, w, d)`, and the base area is defined as the product of `w` and `d`. The comment should be self-explanatory.

```
public long maxHeight(int[][] paraBoxes) {
    // add all possibilities
    List<Integer[]> boxes = new ArrayList<Integer[]>(3 * paraBoxes.length);
    for (int[] box : paraBoxes) {
      boxes.add(new Integer[] {box[0], box[1], box[2]});
      boxes.add(new Integer[] {box[1], box[0], box[2]});
      boxes.add(new Integer[] {box[2], box[0], box[1]});
    }
    // sort the boxes by base area (define base area = w * d)
    Collections.sort(boxes, new BoxComparator());
    // L.I.S.
    long[] M = new long[boxes.size()]; // stores max height ending at each cell (ending cell is at top)
    long max = Long.MIN_VALUE;
    for (int i = 0; i < boxes.size(); i++) {
      M[i] = boxes.get(i)[0];
    }
    for (int i = 0; i < M.length; i++) {
      for (int j = 0; j < i; j++) {
        if (boxes.get(j)[1] < boxes.get(i)[1] &&
            boxes.get(j)[2] < boxes.get(i)[2] &&
            M[j] + boxes.get(i)[0] > M[i]) {
          M[i] = M[j] + boxes.get(i)[0];
        }
      }
      if (max < M[i]) {
        max = M[i];
      }
    }
    return max;
}
```
Here goes the comparator:

```
private class BoxComparator implements Comparator<Integer[]> {
    @Override
    public int compare(Integer[] a, Integer[] b) {
      if (a[1] * a[2] > b[1] * b[2]) {
        return 1; // increasing order
      } else if (a[1] * a[2] < b[1] * b[2]) {
        return -1;
      } else {
        return 0;
      }
    }
}
```
Two quick test cases:

```
public static void main(String...args) {
    Solution s = new Solution();
    System.out.println(s.maxHeight(new int[][] { {16, 20, 30}, {20, 10, 15} }));
    System.out.println(s.maxHeight(new int[][] { {4, 6, 7}, {1, 2, 3}, {4, 5, 6}, {10, 12, 32} }));
}
```