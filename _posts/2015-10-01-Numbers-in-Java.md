---
layout: post
title: Numbers in Java
tags:
- Java

---
I encountered a problem where I need to put numbers into a set, and later check whether a number is contained in the set. But since we are using `Set<Long>`, an idea crossed my mind: will 1 equal to 1? -- If I create two Long object holding the same value, are they consider equal by `Set`?

Yes. Because the `hashcode` method is implemeted as [follows](http://grepcode.com/file/repository.grepcode.com/java/root/jdk/openjdk/8u40-b25/java/lang/Long.java#Long.hashCode%28%29):

```
return (int)(value ^ (value >>> 32));
```
So only the value of that Number object matters, as opposed to the ["regular" implementation](http://grepcode.com/file/repository.grepcode.com/java/root/jdk/openjdk/8u40-b25/java/lang/Object.java#Object.hashCode%28%29): 
> This is typically implemented by converting the internal address of the object into an integer...