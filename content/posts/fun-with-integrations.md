---
title: "Fun with integrations"
date: 2021-06-12T09:47:54+02:00
draft: false
toc: false
images:
math: true
tags:
  - Analyis I
---
In the first post of this series centered around my university degree I will be talking about integration. Now this topic wasn't mentioned in our script but I rather stumbled upon it on youtube.

The premise is the following:

We assume that we have a function f(x) which we can integrate over the interval a to b. 

Calculate the following integral:
$$\int_{2}^{4}\frac{\sqrt{x}}{\sqrt{6-x} + \sqrt{x}} dx$$
Doesn't look trivial now, does it?
But miraculously, it is! This whole integral equates to: 
$$\frac{b-a}{2} = 1$$.

Let's take a look at another integral for fun.
$$\int_{0}^{\frac{\pi}{2}}\frac{\sqrt{sin x}}{\sqrt{sin x} + \sqrt{cos x}}dx$$

Can you see an emerging pattern? This is yet again equal to:
$$\frac{b-a}{2} = \frac{\frac{\pi}{2}}{2} = \frac{\pi}{4}$$.

We can observe that for any integral of the form
$$\int_{a}^{b}\frac{f(x)}{f(a+b-x) + f(x)}dx$$
the following holds:
$$\int_{a}^{b}\frac{f(x)}{f(a+b-x) + f(x)}dx = \frac{b-a}{2}$$.

Now if I were to just throw this out there I would probably get lynched by Ueli Maurer himself. Thus the proof goes as following:
We know that:
$$\int_{a}^{b}\frac{f(x)}{f(a+b-x) + f(x)}dx = I$$
This will be our first equation.
Now we set \\(u = a + b - x\\) and \\(\frac{du}{dx} = - 1 \implies du = -dx\\) by putting that into our integral we receive:
$$\int_{b}^{a}\frac{f(a+b-u)}{f(u) + f(a+b-u)} (-du) = I\newline
 \implies \int_{a}^{b}\frac{f(a+b-u)}{f(u) + f(a+b-u)} du = I \newline
 \implies \int_{a}^{b}\frac{f(a+b-x)}{f(x) + f(a+b-x)} dx = I
$$ 
Since u is only used as a placeholder variable we may rename it as x.
By adding these two integrals (which both equal I) together, we are left with:
$$
\int_{a}^{b}\frac{f(a+b-x) + f(x)}{f(x) + f(a+b-x)} dx = 2I\newline
\implies \int_{a}^{b} dx = 2I \newline
\implies b-a = 2I \newline
\implies I = \frac{b-a}{2} \square $$

Now you can solve some integrals very quickly and without the need of much calculation!

This post was largely inspired and based on this ["MindYourDecisions"](https://www.youtube.com/watch?v=BfZObnTIsYk) video. Check it out for another example for an integral which you can solve with this method.