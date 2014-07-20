---
layout: post
title: Deploy LaTeX Support with Jekyll
categories:
- Tech
tags:
- LaTeX

---
Although I usually don't have many formula to write, but there comes time where you desprately need formula display. I like the formulas on Math Exchange. Here is how to do it with Jekyll: 

->Step 1. Include the CDN link of the ```.js``` file.<-

That's it. Yes, only one step. [Link to include](http://docs.mathjax.org/en/latest/start.html#mathjax-cdn)

As long as the ```.js``` is included, you can use MathJax. I put it in ```\_layouts\default.html```.

\begin{equation}
E = mc^2
\end{equation}



