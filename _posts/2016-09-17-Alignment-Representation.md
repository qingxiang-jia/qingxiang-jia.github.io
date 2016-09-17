---
layout: post
title: Alignment Representation
tags:
- Algorithm
- Kleinberg & Tardos

---
In the book Algorithm Design by Jon Kleinberg and Eva Targos, page 280, it explains the representation of alignment (a special case of matching). The language for how it is represented is rather ambiguous, and therefore I think an example works better than definition.

Say we have a alignment:

```
stop-
-tops
```
The book then continues and saying we have: {(2, 1), (3, 2), (4, 3)}.

What it really means is:

```
1234
stop-
-tops
 1234
```
Since we align this way, 1 maps to nothing, 2 maps to 1; 3 maps to 2; 4 maps to 3. The 4 in the lower word maps to nothing, like 1 in the upper word, it's therefore not shown. So we have (2, 1), (3, 2), (4, 3).