---
layout: post
title: Maximum Independent Set
tags:
- Algorithm
- Dynamic Programming
- Binary Tree

---
In a binary tree, using dp to compute the size of the [maximum independent set (MIS)](https://en.wikipedia.org/wiki/Independent_set_(graph_theory)). In short, if the nodes form an independent set, then, every node in the set is not directly connected to each other.

For example, if we have the binary tree,

```
       __10__
    _20_     30_
  40    50      60
      70  80
```

the MIS should be 5, and they are: 10, 40, 70, 80, 60. Suppose we are looking at a subtree, if its root is selected to be added into the set, it's children can't be added as each node cannot be connected directly. Likewise, if its children is added, the root itself can't be added. So, naturally, we need to make a decision for each subtree: whether or not to include the root. We don't know which decision is better, so we compute both and take the better one.

Here I cite Peter de Rivaz's [explanation](http://stackoverflow.com/questions/13544240/algorithm-to-find-max-independent-set-in-a-tree) for the transition function because it's so concise and clear.

For each subtree, we have two case:

  Case 1:
  
  The root of the subtree is not included
    **B(i) = sum(max(A(j), B(j)) for j children(i))**
  
  Case 2: 
  
  The root of the subtree is included
    **A(i) = 1 + sum(B(j) for j in children(i))**

B(i) denotes the MIS for the subtree rooted at i, if we don't include the root;
A(i) denotes the MIS for the subtree rooted at i, if we include the root.

For case 1, for each child, we take the max between A(j) and B(j). Why? Because since we don't take the root, it doesn't matter whether we take A(j) or B(j), we just take whichever is larger. For case 2, it matters, as we have to be sure that the child's root is not taken, so we can only take values from B(j).

Since we need to work with A(j) and B(j) when we deal with the root, I chose to implement it using post-order traversal. Below is my Java solution.

```
public int MIS(Node root) {
    if (root.left == null && root.right == null) { // leaf
      root.A = 1;
      root.B = 0;
    } else if (root.left != null && root.right != null) { // post-order traversal
      MIS(root.left);
      MIS(root.right);
      root.B = max(root.left.A, root.left.B) + max(root.right.A, root.right.B);
      root.A = 1 + root.left.B + root.right.B;
    } else if (root.left == null && root.right != null) {
      MIS(root.right);
      root.B = max(root.right.A, root.right.B);
      root.A = 1 + root.right.B;
    } else { // root.left != null && root.right == null
      MIS(root.left);
      root.B = max(root.left.A, root.left.B);
      root.A = 1 + root.left.B;
    }
    return max(root.A, root.B);
 }
```

As usual, to get familiar with the algorithm, I will provide a dry run.

```
               (  10  )
          ____ A:0  B:0 ____
         /                  \
     (  20  )            (  30  )
     A:0  B:0            A:0  B:0
    /        \                   \
(  40  )  (  50  )            (  60  )
A:0  B:0  A:0  B:0            A:0  B:0
         /        \ 
     (  70  )   (  80  )
     A:0  B:0   A:0  B:0
```

I will use the value as ID for each node as in our example, they are unique. Initially, we are at the root, we want to compute the MIS for each subtree (rooted at 20 and 30), so we call MIS recursively at 20 and 30. For 20, we recursively call MIS at 40 and 50. For 40, it doesn't have any children, so, A is 1 and b is 0, and we have the following diagram to represent the state for the dry run.

```
               (  10  )
          ____ A:0  B:0 ____
         /                  \
     (  20  )            (  30  )
     A:0  B:0            A:0  B:0
    /        \                   \
(  40  )  (  50  )            (  60  )
A:1  B:0  A:0  B:0            A:0  B:0
         /        \ 
     (  70  )   (  80  )
     A:0  B:0   A:0  B:0
```

For the subtree rooted at 50 (for convenience, I will call it subtree(50)), we recursively call MIS at 70 and 80. For subtree(70), similar to subtree(40), we have A=1 and b=0. The same goes for subtree(80).

```
               (  10  )
          ____ A:0  B:0 ____
         /                  \
     (  20  )            (  30  )
     A:0  B:0            A:0  B:0
    /        \                   \
(  40  )  (  50  )            (  60  )
A:1  B:0  A:0  B:0            A:0  B:0
         /        \ 
     (  70  )   (  80  )
     A:1  B:0   A:1  B:0
```

Now, after evaluating subtree(70) and subtree(80), we can finally process subtree(50). For A, we have 1 since both subtree(70).B and subtree(80).B are 0; for B, we have 2 since both subtree(70).A and subtree(80).A are 1.

```
               (  10  )
          ____ A:0  B:0 ____
         /                  \
     (  20  )            (  30  )
     A:0  B:0            A:0  B:0
    /        \                   \
(  40  )  (  50  )            (  60  )
A:1  B:0  A:1  B:2            A:0  B:0
         /        \ 
     (  70  )   (  80  )
     A:1  B:0   A:1  B:0
```

For subtree(20), we have A=3 and B=3, the reasoning is similar to the last step.

```
               (  10  )
          ____ A:0  B:0 ____
         /                  \
     (  20  )            (  30  )
     A:3  B:3            A:0  B:0
    /        \                   \
(  40  )  (  50  )            (  60  )
A:1  B:0  A:1  B:2            A:0  B:0
         /        \ 
     (  70  )   (  80  )
     A:1  B:0   A:1  B:0
```

For subtree(60), we have A=1, B=0;

```
               (  10  )
          ____ A:0  B:0 ____
         /                  \
     (  20  )            (  30  )
     A:3  B:3            A:0  B:0
    /        \                   \
(  40  )  (  50  )            (  60  )
A:1  B:0  A:1  B:2            A:1  B:0
         /        \ 
     (  70  )   (  80  )
     A:1  B:0   A:1  B:0
```

For subtree(30), we have A=1, B=1.

```
               (  10  )
          ____ A:0  B:0 ____
         /                  \
     (  20  )            (  30  )
     A:3  B:3            A:1  B:1
    /        \                   \
(  40  )  (  50  )            (  60  )
A:1  B:0  A:1  B:2            A:1  B:0
         /        \ 
     (  70  )   (  80  )
     A:1  B:0   A:1  B:0
```

Finally, for subtree(10), A = 3 + 1 + 1, B = 3 + 1, so the solution to the entire tree is 5.

```
               (  10  )
          ____ A:5  B:4 ____
         /                  \
     (  20  )            (  30  )
     A:3  B:3            A:1  B:1
    /        \                   \
(  40  )  (  50  )            (  60  )
A:1  B:0  A:1  B:2            A:1  B:0
         /        \ 
     (  70  )   (  80  )
     A:1  B:0   A:1  B:0
```