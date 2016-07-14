---
layout: post
title: Integer Knapsack Problem
tags:
- Algorithm
- Dynamic Programming

---
This is the classical 0-1 knapsack problem. You have an array of items, each of them has a value. You have a bag, with certain weight limit. You want to maximize the value while making sure the total weight is under (or equal) the limit. Compute the maximum value.

The key is to realize this transition function: `M[i][w] = max(M[i-1][w], value[i] + M[i-1][w-weight[i]])`. 

`value[i]` represents the value of the ith item. `weight[i]` represents the weight of the ith value. `M[i][j]` represents the maximized value given the range of items you can choose from `(0..i)`, and the weight limit `j`. Here, several explanations online didn't get the meaning of `i` correctly. `i` just gives you the range to choose the items, you don't have to take every item in that range. For `j`, it's just a limit, your algorithm doesn't have to meet the limit exactly. The transition function means that for each range `0..i`, and each weight limit `w`, you have two choices, either take the ith item or not. If you don't take the ith item, `M[i][w] = M[i-1][w]`. This says that if you don't take it, the maximized value is the same as the value with the same weight limit but without ith item. Notice that even for `M[i-1][w]`, the value doesn't necessarily includes `value[i-1]`. If you take the ith item, there is `M[i][w] = value[i] + M[i-1][w-weight[i]]`. For `value[i]`, of course, you took the ith item, you must have `value[i]` included. `M[i-1][w-weight[i]]` says that if we take the ith item, the maximized value includes not only the `value[i]`, but also the maximized value with range `0..i-1`, and weight limit `w-weight[i]`. The range part is easy but why we choose the previous state with weight limit = `w-weight[i]`? Because you have decided to stuff in the ith item, so the maximum weight limit for the previous state is `w-weight[i]`. When I did the problem, I was confused at this part. Since every weight limit that is less than `w-weight[i]` should be okay. Yes, they are okay, but they are not optimal. As you can certainly choose the previous state with much less weight limit, but that means you have missed many possible items that could have been stuffed in the bag. You can also think the other way: the higher the limit, potentially there are more items can be stuffed in. The higher limit doesn't guarantee a higher total value, but it is at least as good as the states with lower limit.

Below is my Java solution, it's not the shortest one, but it is better for seeing the thought process than the shortest solution.

```
public int knapsack(int[] weight, int[] value, int maxWeight) {
    int items = weight.length;
    int[][] M = new int[items][maxWeight+1];
    /* M[i][w] represents maximum value that can be attained if the maximum weight is w and items are chosen from 0...i */
    for (int i = 0; i < items; i++) {
      for (int w = 0; w <= maxWeight; w++) {
        if (w - weight[i] >= 0) { // if at limit w, I can take ith item
          if (i == 0) { // if i == 0, i-1 will be -1, so, the only thing it can do is to match the weight limit against i(0)'s weight
            M[i][w] = value[i]; // (if j == 0, it's just 0 since only zero weight is allowed)
          } else {
            M[i][w] = max(M[i-1][w], value[i] + M[i-1][w-weight[i]]);
          }
        } else { // at limit w, I can't take ith item
          if (i > 0) { // if i == 0, meaning that I can only take the 0th item, I will just get zero since weight[0] is too large.
            M[i][w] = M[i-1][w];
          }
        }
      }
    }
    return M[items-1][maxWeight];
}

```

In my code, I made everything explicit. For `M`, it's dimension is `[items][maxWeight+1]`. This is where my solution differs most from the shorter solution. For me, since the items are given in an array, the first item will be the 0th. Some solution starts at 1, that means you need to offset this in your transition function which makes it less obvious. So, the first dimension for `M` is items. For the second part of the dimension, I chose to use `maxWeight+1` as it makes more sense for me to allow the bag to reach exactly that limit (instead of one less).

Now, many popular solutions initialize `M` before the nested loop. That's fine, it makes the loop nicer but I prefer to do everything in the loop as I want to inclose all the core algorithm together. When traversing `M`, each time, there are several decisions to make.

First, we want to know whether the ith item can be stuffed in. This is done by "`if (w - weight[i] >= 0)`". Initially, I felt this very unintuitive. Why so? Because for each state, when we consider whether an item can be stuffed in, we also need to consider what has been filled, just comparing the total weight for this state with `weight[i]` seems to be wrong. This is actually fine. Because we know that as long as `w` is greater than `weight[i]`, we have the opportunity to stuff it in. Because later, in the transition function, `M[i-1][w-weight[i]]` picks whatever previous state that fits the "hole" created by `w - weight[i]`.

Now, if we can stuff the ith item in, we still have some corner cases to cover. Notice in the transition function, there is `i-1`. What if `i==0`? So this one has to be considered separately. `i==0` means that we can only pick the first item. So, we can just let `M[i][w] = value[i]`. When `i > 0`, we come to the case where the transition function applies. I will skip since we already discussed the meaning of it.

So, what if `j==0`? That means the weight limit is 0, meaning that we didn't even bring the bag. So, the result will simply be 0. Because Java fills the array with 0, we don't need to do any thing here (you may have to manually fill it if it's some other language).

The other case is that when `w - weight[i] < 0`. That means that we can't fill in the nth item. That's simple, because it will just be equal to `M[i-1][w]`, but note that we must make sure `i >= 1`. So what if `i==0`? In that case, it means we can't pick the 0th item because we are under the premise that `w - weight[i] < 0`, so zero.

In the end, we return `M[items-1][maxWeight]` because it is the solution when we have items items, given limit `maxWeight`.

It makes more sense if we have an example. For convenience, I use the following case:
weight = {1, 1, 1, 1}
value = {10, 20, 15, 5}
maxWeight = 5

```
   0  1  2  3
  +--+--+--+--+
0 |  |  |  |  |
  +--+--+--+--+
1 |  |  |  |  |
  +--+--+--+--+
2 |  |  |  |  |
  +--+--+--+--+
3 |  |  |  |  |
  +--+--+--+--+
4 |  |  |  |  |
  +--+--+--+--+
5 |  |  |  |  |
  +--+--+--+--+
```

The table represents `M`, where the columns represent item 0 to 3, and the rows represent different weight limits. Initially, every cell is filled with 0 and here I use blank to represent it.

First, `i=0`, we are looking at the situation where the only choice we have is item 0, and the limit is 0, so, nothing we can do.

```
   0  1  2  3
  +--+--+--+--+
0 |0 |  |  |  |
  +--+--+--+--+
1 |  |  |  |  |
  +--+--+--+--+
2 |  |  |  |  |
  +--+--+--+--+
3 |  |  |  |  |
  +--+--+--+--+
4 |  |  |  |  |
  +--+--+--+--+
5 |  |  |  |  |
  +--+--+--+--+
```

Next, `w` increases to 1, and we now can stuff in item 0, so we have:

```
   0  1  2  3
  +--+--+--+--+
0 |0 |  |  |  |
  +--+--+--+--+
1 |10|  |  |  |
  +--+--+--+--+
2 |  |  |  |  |
  +--+--+--+--+
3 |  |  |  |  |
  +--+--+--+--+
4 |  |  |  |  |
  +--+--+--+--+
5 |  |  |  |  |
  +--+--+--+--+
```

`w` increases to 2, but we don't have any choice but to pick item 0. So is the next three steps, which I will skip for this reason.

```
   0  1  2  3
  +--+--+--+--+
0 |0 |  |  |  |
  +--+--+--+--+
1 |10|  |  |  |
  +--+--+--+--+
2 |10|  |  |  |
  +--+--+--+--+
3 |10|  |  |  |
  +--+--+--+--+
4 |10|  |  |  |
  +--+--+--+--+
5 |10|  |  |  |
  +--+--+--+--+
```

Now `w` returns to 0, and i increases to 1, we now have item `0..1` in hand. But since w is 0, nothing can be done. We have:

```
   0  1  2  3
  +--+--+--+--+
0 |0 |0 |  |  |
  +--+--+--+--+
1 |10|  |  |  |
  +--+--+--+--+
2 |10|  |  |  |
  +--+--+--+--+
3 |10|  |  |  |
  +--+--+--+--+
4 |10|  |  |  |
  +--+--+--+--+
5 |10|  |  |  |
  +--+--+--+--+
```

The weight limit `w` increases to 1 and meanwhile we have two choices, item 0 and 1. Since `w=1`, we can take item 1, so we are at the transition function, comparing whether the previous solution (`M[i-1][w]`, i.e. not taking item 1) or current solution (`value[i] + M[i-1][w-weight[i]]`, i.e., take item 1) is larger. In this case, the previous solution is `M[0][1]`, 10 and the current solution is `value[1] + M[0][0]`, so current solution (20) is better than the previous solution (10). The table becomes the following:

```
   0  1  2  3
  +--+--+--+--+
0 |0 |0 |  |  |
  +--+--+--+--+
1 |10|20|  |  |
  +--+--+--+--+
2 |10|  |  |  |
  +--+--+--+--+
3 |10|  |  |  |
  +--+--+--+--+
4 |10|  |  |  |
  +--+--+--+--+
5 |10|  |  |  |
  +--+--+--+--+
```

`w` increases to 2, we still have item 0 and 1. Again, because `1 > weight[1]`, we are at the transition function and considering whether the previous solution (10) or current solution (`value[1] + M[0][1] = 20`) is better.

```
   0  1  2  3
  +--+--+--+--+
0 |0 |0 |  |  |
  +--+--+--+--+
1 |10|20|  |  |
  +--+--+--+--+
2 |10|  |  |  |
  +--+--+--+--+
3 |10|  |  |  |
  +--+--+--+--+
4 |10|  |  |  |
  +--+--+--+--+
5 |10|  |  |  |
  +--+--+--+--+
```

Now, nothing has changed except that `w` has increased to 2. Because `2-weight[1] >= 0`, we are again at the transition function. Now, the previous solution is `M[0][2]`, which is 10. The current solution is `value[1] + M[0][1]`, which is 30, so we take 30. This will be true for the next 3 steps as well because we only have item 0 and 1 at hand, the sum of the value of them is 30. For this reason, we will skip the next 4 steps.

```
   0  1  2  3
  +--+--+--+--+
0 |0 |0 |  |  |
  +--+--+--+--+
1 |10|20|  |  |
  +--+--+--+--+
2 |10|30|  |  |
  +--+--+--+--+
3 |10|30|  |  |
  +--+--+--+--+
4 |10|30|  |  |
  +--+--+--+--+
5 |10|30|  |  |
  +--+--+--+--+
```

`i=2`, `w=0`, since `w=0`, although additionally we now have item 2, we can do nothing but fill in 0.

```
   0  1  2  3
  +--+--+--+--+
0 |0 |0 |0 |  |
  +--+--+--+--+
1 |10|20|  |  |
  +--+--+--+--+
2 |10|30|  |  |
  +--+--+--+--+
3 |10|30|  |  |
  +--+--+--+--+
4 |10|30|  |  |
  +--+--+--+--+
5 |10|30|  |  |
  +--+--+--+--+
```

`w` increases to 1, since `1-weight[2] >= 0`, i.e., we can take item 2, we are at the transition function. The previous solution is `M[1][1]`, which is 20. The current solution is `value[2] + M[1][0]`, which is 15, so we keep our old solution.

```
   0  1  2  3
  +--+--+--+--+
0 |0 |0 |0 |  |
  +--+--+--+--+
1 |10|20|20|  |
  +--+--+--+--+
2 |10|30|  |  |
  +--+--+--+--+
3 |10|30|  |  |
  +--+--+--+--+
4 |10|30|  |  |
  +--+--+--+--+
5 |10|30|  |  |
  +--+--+--+--+
```

Next, `w` has increased to 2, again because we can take item 2, we are at the transition function and comparing the previous solution (`M[1][2]=30`) and current one (`value[2] + M[1][1] = 35`). So we take 35.

```
   0  1  2  3
  +--+--+--+--+
0 |0 |0 |0 |  |
  +--+--+--+--+
1 |10|20|20|  |
  +--+--+--+--+
2 |10|30|35|  |
  +--+--+--+--+
3 |10|30|  |  |
  +--+--+--+--+
4 |10|30|  |  |
  +--+--+--+--+
5 |10|30|  |  |
  +--+--+--+--+
```

`w` increases to 3. Since we can take item 2, we are at the transition function, comparing the previous solution (`M[1][3]`, 30) and current solution (`value[2] + M[1][2]`, 45). So we take 45. It goes identically for the next two steps.

```
   0  1  2  3
  +--+--+--+--+
0 |0 |0 |0 |  |
  +--+--+--+--+
1 |10|20|20|  |
  +--+--+--+--+
2 |10|30|35|  |
  +--+--+--+--+
3 |10|30|45|  |
  +--+--+--+--+
4 |10|30|45|  |
  +--+--+--+--+
5 |10|30|45|  |
  +--+--+--+--+
```

Now `i` increases to 3 and `w` returns to 0. Since `w=0`, we fill 0 in.

```
   0  1  2  3
  +--+--+--+--+
0 |0 |0 |0 |0 |
  +--+--+--+--+
1 |10|20|20|  |
  +--+--+--+--+
2 |10|30|35|  |
  +--+--+--+--+
3 |10|30|45|  |
  +--+--+--+--+
4 |10|30|45|  |
  +--+--+--+--+
5 |10|30|45|  |
  +--+--+--+--+
```

`w` increases to 1 (`w-weight[3] >= 0`), we can choose either item 3 with an appropriate previous solution (`value[3] + M[2][0] = 5`), or the previous solution, 20. Obviously, we should take 20. 

```
   0  1  2  3
  +--+--+--+--+
0 |0 |0 |0 |0 |
  +--+--+--+--+
1 |10|20|20|20|
  +--+--+--+--+
2 |10|30|35|  |
  +--+--+--+--+
3 |10|30|45|  |
  +--+--+--+--+
4 |10|30|45|  |
  +--+--+--+--+
5 |10|30|45|  |
  +--+--+--+--+
```

`w` increases to 2, since `w=2`, we can take item 3. If we don't take item 3, we have the previous solution `M[2][2]=35`. If we take item 3 with an appropriate previous solution: `value[3] + M[2][1]`, 35, we will end up with 35 as well. So, 35.

```
   0  1  2  3
  +--+--+--+--+
0 |0 |0 |0 |0 |
  +--+--+--+--+
1 |10|20|20|20|
  +--+--+--+--+
2 |10|30|35|35|
  +--+--+--+--+
3 |10|30|45|  |
  +--+--+--+--+
4 |10|30|45|  |
  +--+--+--+--+
5 |10|30|45|  |
  +--+--+--+--+
```

`w` increases to 3, since `w=3`, we can take item 3. If we don't take item 3, we have the previous solution `M[2][3]=45`. If we do take item 3 with an appropriate previous solution: `value[3] + M[2][2] = 40`, we would get less. So, take 45.

```
   0  1  2  3
  +--+--+--+--+
0 |0 |0 |0 |0 |
  +--+--+--+--+
1 |10|20|20|20|
  +--+--+--+--+
2 |10|30|35|35|
  +--+--+--+--+
3 |10|30|45|45|
  +--+--+--+--+
4 |10|30|45|  |
  +--+--+--+--+
5 |10|30|45|  |
  +--+--+--+--+
```

`w` increases to 4, which means we can take item 3. If we don't take item 3, we have the previous solution `M[2][4]=45`. If we do take item 3 with an appropriate previous solution, we have: `value[3] + M[2][3] = 50`. So, take 50. Similarly, the last cell is 50 too.

```
   0  1  2  3
  +--+--+--+--+
0 |0 |0 |0 |0 |
  +--+--+--+--+
1 |10|20|20|20|
  +--+--+--+--+
2 |10|30|35|35|
  +--+--+--+--+
3 |10|30|45|45|
  +--+--+--+--+
4 |10|30|45|50|
  +--+--+--+--+
5 |10|30|45|50|
  +--+--+--+--+
```