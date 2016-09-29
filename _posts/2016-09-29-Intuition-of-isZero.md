---
layout: post
title: Intuition of isZero
tags:
- Lambda Calculus

---

*Before reading, make sure you understand how positive integers are represented in lambda calculus.*

We want `isZero` to return true for zero (`λ f x. x`) and false for all other numbers.

```
isZero = λ n. n (λ z. false) true
```

Alternatively, you can write is as:

```
isZero n = n (λ z. false) true
```

So what is zero? Zero is `λ f x. x`, a function that takes two parameters `f` and `x`, and return `x`. What is one `λ f x. f x`? A function that takes `f` and `x`, and return `f x`. `f x` is just f (x). So the intuition for designing isZero is that we want any function application, i.e., f (x) to return false, and none function application to return true.

When isZero is applied to zero, let's see:

```
(λ n. n (λ z. false) true) (λ f x. x)
```

replace n with `(λ f x. x)` we get:

```
(λ f x. x) (λ z. false) true
```

`(λ f x. x)` takes `(λ z. false)` and `true` but immediately it discards `(λ z. false)`, and return `x`, which is true here. If we take anything that is non-zero, say one, we will get false. Here is how.

```
one = λ f x. f x
```

isZero one is just:

```
(λ n. n (λ z. false) true) (λ f x. f x)
```

substitute `(λ f x. f x)` into `isZero`, we get:

```
(λ f x. f x) (λ z. false) true
```

Now, `(λ f x. f x)` is a function that takes two parameters `f` and `x` and return `f x` (or equivalently, it returns x applied to f). So, after reduction, we get:

```
(λ z. false) true
```

where `(λ z. false)` is a function that takes one parameter `z`, and no matter what that `z` is, it simply returns `false`. Therefore we get false.