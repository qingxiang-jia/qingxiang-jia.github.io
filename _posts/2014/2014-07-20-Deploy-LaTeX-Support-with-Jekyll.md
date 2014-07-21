---
layout: post
title: Deploy LaTeX Support with Jekyll
categories:
- Tech
tags:
- LaTeX

---
Although I usually don't have many formula to write, but there comes time where you desprately need formula display. I like the formulas on Math Exchange. Here is how to do it with Jekyll: 

<p style='text-align: center;'>Step 1. Include the CDN link of the <code>.js</code> file.</p>

That's it. Yes, only one step. [Link to include](http://docs.mathjax.org/en/latest/start.html#mathjax-cdn) However, there is one caveat; if you are using `rdiscount`, switch it to `kramdown` (in `_config.yml` file). Initially I didn't realize the difference, until I found `$$\LaTeX$$` will be displayed correctly but not `$$a^2 + b^2 = c^2$$`.

As long as the `.js` is included, you can use MathJax. I put it in `\_layouts\default.html`.

```\\[\LaTeX\\]``` will take an entire line, like this
\\[\LaTeX\\]

and ```$$\LaTeX$$``` will be inline, like this $\LaTeX$.

Here are some more complicated formula brought from [Tex Samples](http://www.mathjax.org/demos/tex-samples/).
\\[P(E) = {n \choose k} p^k (1-p)^{ n-k} \\]
\\[ \frac{1}{\Bigl(\sqrt{\phi \sqrt{5}}-\phi\Bigr) e^{\frac25 \pi}} = 1+\frac{e^{-2\pi}} {1+\frac{e^{-4\pi}} {1+\frac{e^{-6\pi}} {1+\frac{e^{-8\pi}} {1+\ldots} } } } \\]
\\[ \begin{aligned} \nabla \times \vec{\mathbf{B}} -\, \frac1c\, \frac{\partial\vec{\mathbf{E}}}{\partial t} & = \frac{4\pi}{c}\vec{\mathbf{j}}\end{aligned} \\]