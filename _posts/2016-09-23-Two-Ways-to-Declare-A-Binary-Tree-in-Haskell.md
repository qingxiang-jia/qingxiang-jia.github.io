---
layout: post
title: Two Ways to Declare A Binary Tree in Haskell
tags:
- Haskell

---

I am about to take [Professor Jhala's](https://ranjitjhala.github.io/) [class](http://ucsd-pl.github.io/cse230/) and now I am learning Haskell. One thing I find interesting is how you can define a recursive data structure in two different ways.

**Method 1**

```
data Tree a = Leaf a | Branch (Tree a) (Tree a)
```

**Method 2**

```
data Tree a = EmptyTree | Node a (Tree a) (Tree a)
```

In short, method 2 is just method 1 with the "|" moved one left. 

Long explanation: a here is a type variable. On the left of = is type constructor'; on the right of = is the value constructor. Method 1 says we define type named Tree and BTW we have a value a to store; the Tree type can either be a Leaf, where it just has the value a, or it can be a Branch, where it has two Trees each will store a value a. Method 2 says, we define a Tree and BTW we have a value a to store. The Tree will either be an EmptyTree that stores nothing, or it can be a Node that stores a value a and has two Trees  each stores a value a.