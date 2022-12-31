---
layout: default
title: Expectation and Integration
parent: Probability Theory
grand_parent: All Things Statistics
nav_order: 3
has_toc: false
has_children: true
usemathjax: true
---

# Probability as a Measure
{: .no_toc }

## Table of contents
{: .no_toc .text-delta }

1. TOC
{:toc}

---

$\newcommand{\reals}{\mathbb{R}}$ $\newcommand{\nats}{\mathbb{N}}$ $\newcommand{\ind}{\mathbb{1}}$  $\newcommand{\pr}{\mathbb{P}}$ $\newcommand{\cv}[1]{\mathcal{#1}}$ $\newcommand{\nul}{\varnothing}$ $\newcommand{\eps}{\varepsilon}$ $\newcommand{\E}{\mathbb{E}}$ 

# Integration

Thus far, we have defined a random variable as a function. We have also developed a mechanism to help understand how to evaluate probability measures of limiting events and its relationship to continuity. Another important property of a random variable is its expectation or moment, and we can examine higher order moments for random variables which will provide more information about the behavior of the random variable. Moments also help us control certain aspects of the random variable, which allows us to make generalizations of sequences of random variables ad infinitum. Expectation is expressed as an integration. For random variable $X$, we define the expectation as

$$\E(X) = \int_\Omega X(\omega) d\pr = \int_\Omega X(\omega) \pr(d\omega)$$

Recall the discussion on induced measures from the measure theory and $\sigma$-algebra discussion. We can rewrite the integral by changing the variable of integration justified through induced measures by the random variable. $X : (\Omega, \cv{F}, \pr) \to (\reals, \cv{B})$ where $\lambda$ is the induced measure on $(\reals, \cv{B})$:

$$\E(X) = \int_\Omega X(\omega) \pr(d\omega) = \int_\reals x \lambda(dx)$$

## Riemann-Darboux Function Approximation is not Sufficient, a Proposed Solution

At this point, integration ought to be defined. In the Riemann sense, integration is not entirely well defined as we see pitfalls when Riemann integrating some pathological functions. This is particularly troublesome because it means Riemann integration is not a general enough technique. For example, let $f(\omega) = \ind_{\omega \in \mathbb{Q}}$. where $\omega \in (0,1)$. It is easy to show the lower and upper Riemann sums do not agree, thus the Riemann integral is not defined. 

**Exercise**: Show that the function above is not Riemann integrable. (Hint: Riemann integration requires the lower and upper sum to agree in the limit in order to be integrable, in the Riemann sense.)

The integral of the non-Riemann integrable function given above is one formulation of asking the question "what is the probability of picking a rational number from all real numbers in the interval [0,1]?" Since the rational numbers are countable, the probability should be 0. Yet, breaking a function up into interval partitions and observing how its upper and lower sum converges in the Riemann sense will not provide an adequate answer (the function is not Riemann integrable). So the Riemann integral is sufficient for a subset of "nice" functions, but there are functions in which the Riemann integral is not adequate. Thus we need another approach to integration - one even more general to handle more than just the "nice" functions. As Riemann integration relied on forming peicewise functions that approximate the original function from above and below based on interval partions, we would need to estiblish another paradigm of approximating a function. Hopefully this new paradigm will help form a more general definition of an integral.

### Simple non-Negative Functions

We introduce the idea of a simple function in hopes of approximating general function. A **simple function** is a non-negative measurable function that can be expressed as a finite linear combination of indicator functions on disjoint sets. That is for simple $f: (\Omega, \cv{F}) \to ([0,\infty], \cv{B}([0,\infty]))$:

$$f(\omega) := \sum_{i=1}^N a_{i} \ind_{A_{i}}(\omega)$$

where $a\_i \geq 0$ is a sequence of constants and $A\_i$ is a sequence of disjoint sets indexed by $i$. While this may look like we are approximating the function in a Riemann sense where we take $\inf f(x) \Delta x$ or $\sup f(x) \Delta x$, however the difference is that $A\_i$ does not need to be an interval; it could be a union of seperate disjoint intervals. It could even be a single point. The sole requirement is that $A\_i$ must be $\cv{F}$-measurable.  

### General non-Negative Functions

The simple function is peicewise by definition. However it can be used to approximate more general non-negative measurable functions. Specifically, for non-negative general function $f$, it can be approximated from below by a sequence of simple functions $f\_n$ with arbitrary precision. This is called the **simple function approximation theorem**.

_Proof_ : Given a function $f$, we form a simple function $f\_n$ by dividing is co-domain into $2^n +1$ intervals of equal length, so that each interval is of length $1/2^n$. Define the interval $I\_{n,k} = [\frac{k-1}{2^n}, \frac{k}{2^n})$ for $k=1,...,2^{2^n}$. For $k=2^{2^n}+1$ let the interval $I_{n,k} = [2^n, \infty)$. Now define $A_{n,k} = f^{-1}(I_{n,k})$ - the preimage of $f$ on these intervals. Each $A_{n,k}$ is measurable for each $k$ for any $n$ since $f$ is measurable. 

Now we define $f\_n$ as:

$$f_n(\omega) = \sum_{i=1}^{2^{2^n}+1} \frac{i-1}{2^n} \ind_{A_{n,i}})(\omega)$$

For any $\omega$, $f(\omega) - f\_n(\omega) < 1/2^n$ by construction of $f\_n$. So when $n$ is large enough, $f\_n \to f$ pointwise with arbitrary precision. If $f$ is bounded, this convergence is uniform almost everywhere since after a large enough $n$, $f^{-1}(I_{n,2^{2^n+1}}) = \nul$ which has measure 0.  $\tag*{∎}$ 

We did not need to divide this using powers of 2. We could have divided into powers of 100 and the idea of the proof would remain the same. A picture of a function $f$ overlayed with a simple function will better help understand this concept.

![Simple Function](simpleapprox.svg)

We can represent this simple function as

$$f_n(\omega) = a_1\ind_{A_1} + a_2\ind_{A_2} + a_3\ind_{A_3}$$

Here, we divided the the co-domain at values $a\_1$ to $a\_4$ and the regions in red in the domain is the measurable set $A\_1$, regions in blue is the measurable set $A\_2$ and the regions in green is the measurable set $A\_3$. $f\_{n+1}$ is formed by further subdividing these regions in the codomain to smaller regions, and the number of regions increases, which in turn produces better approximations of $f$. We can see general non-negative functions as completions of simple functions.

### General Functions

So far we have been dealing with non-negative functions. Now, we can consider functions that may also be negative. A function $f$ may have portions of its codomain where it is negative and portions where it is positive. If we define $f^+$ and $f^-$ as the following:

$$f^+(\omega) = \max(f(\omega), 0)\;\qquad \; f^-(\omega) = -\min(f(\omega), 0)$$

then $f^+$ corresponds to $f$ where $f$ is positive or zero, and $f^-$ corresponds to $f$ where $f$ is negative or zero. Furthermore,

$$f = f^+-f^-\; \qquad \; |f| = f^+ + f^-$$

$f^+$ and $f^-$ are both non-negative functions, and thus both can be represented as the limits of sequences of simple functions $\geq 0$.

With measurable functions now defined as a completion of non-negative simple functions and differences thereof, we are now ready to define the Lebesgue integral.

## Lebesgue Integral

The Riemann integral attempts to partition the region of integration into infinitessimal intervals.

![The Integral](lebesgue-integral.svg)

The above image is the case when $n=3$, where we divide the codomain of the function $f$ into 3 equally spaced intervals $f = a\_1$, $f=a\_2$, and $f=a\_3$. Then we examine the measure of $\\{\omega : f(\omega) = a\_1 \\}$ and multiply it by $a\_1$ and we do the same for $a\_2$ and $a\_3$. Essentially, we are representing the function as a sequence of stepwise functions.



